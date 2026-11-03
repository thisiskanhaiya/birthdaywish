<script setup>
import { computed, onBeforeUnmount, onMounted, ref } from 'vue'

const galaxyMode = ref(false)
const attempts = ref(0)
const wishCaught = ref(false)
const deliveryReady = ref(false)
const soundOn = ref(false)
const pointerPosition = ref({ x: 0, y: 0 })
const candlesLit = ref(true)
const stickerCanvas = ref(null)
let renderer
let resizeObserver
let animationFrame
let starMeshes = []
let audioContext
let ambientGain
let tuneGain
let ambientOscillators = []
let fluteTimer
let deliveryTimer

const skyStars = Array.from({ length: 72 }, (_, index) => ({
  id: index,
  x: (index * 47 + 13) % 100,
  y: (index * 67 + 19) % 100,
  size: index % 9 === 0 ? 3 : index % 3 === 0 ? 2 : 1,
  delay: `${(index % 13) * -0.37}s`,
  duration: `${2.5 + (index % 8) * 0.45}s`
}))

const targetPositions = [
  { x: 70, y: 30 },
  { x: 25, y: 68 },
  { x: 61, y: 48 }
]

const targetStyle = computed(() => ({
  left: `${targetPositions[Math.min(attempts.value, 2)].x}%`,
  top: `${targetPositions[Math.min(attempts.value, 2)].y}%`
}))

const skyStyle = computed(() => ({
  '--near-x': `${pointerPosition.value.x}px`,
  '--near-y': `${pointerPosition.value.y}px`,
  '--far-x': `${pointerPosition.value.x * -0.35}px`,
  '--far-y': `${pointerPosition.value.y * -0.35}px`
}))

const startWishJourney = () => {
  galaxyMode.value = true
  attempts.value = 0
  wishCaught.value = false
  deliveryReady.value = false
  soundOn.value = true
  startAmbientSound()
  playChime([523, 784])
}

const moveSky = (event) => {
  const bounds = event.currentTarget.getBoundingClientRect()
  pointerPosition.value = {
    x: ((event.clientX - bounds.left) / bounds.width - 0.5) * 26,
    y: ((event.clientY - bounds.top) / bounds.height - 0.5) * 20
  }
}

const attemptToCatchWish = () => {
  if (wishCaught.value) return

  attempts.value += 1
  if (attempts.value < 3) {
    playChime(attempts.value === 1 ? [392] : [349, 440])
    return
  }

  wishCaught.value = true
  playChime([523, 659, 784, 1047])
  deliveryTimer = window.setTimeout(() => {
    deliveryReady.value = true
  }, 750)
}

const toggleSound = () => {
  soundOn.value = !soundOn.value
  if (soundOn.value) startAmbientSound()
  else stopAmbientSound()
}

const closeGalaxy = () => {
  galaxyMode.value = false
  stopAmbientSound()
}

function getAudioContext() {
  if (!audioContext) {
    const AudioContextConstructor = window.AudioContext || window.webkitAudioContext
    if (AudioContextConstructor) audioContext = new AudioContextConstructor()
  }
  if (audioContext?.state === 'suspended') void audioContext.resume()
  return audioContext
}

function startAmbientSound() {
  const context = getAudioContext()
  if (!context || ambientOscillators.length) return

  ambientGain = context.createGain()
  ambientGain.gain.setValueAtTime(0.0001, context.currentTime)
  ambientGain.gain.exponentialRampToValueAtTime(0.012, context.currentTime + 1.4)
  ambientGain.connect(context.destination)
  tuneGain = context.createGain()
  tuneGain.gain.value = 0.8
  tuneGain.connect(context.destination)

  for (const [frequency, type] of [[110, 'sine'], [164.81, 'triangle']]) {
    const oscillator = context.createOscillator()
    oscillator.type = type
    oscillator.frequency.value = frequency
    oscillator.connect(ambientGain)
    oscillator.start()
    ambientOscillators.push(oscillator)
  }
  playFlutePhrase()
}

function stopAmbientSound() {
  window.clearTimeout(fluteTimer)
  if (ambientGain && audioContext) {
    ambientGain.gain.setTargetAtTime(0.0001, audioContext.currentTime, 0.15)
  }
  if (tuneGain && audioContext) {
    tuneGain.gain.setTargetAtTime(0.0001, audioContext.currentTime, 0.08)
  }
  ambientOscillators.forEach((oscillator) => oscillator.stop())
  ambientOscillators = []
  ambientGain = null
  tuneGain = null
}

function playFlutePhrase() {
  const context = audioContext
  if (!soundOn.value || !context || !tuneGain) return

  const notes = [523.25, 587.33, 659.25, 783.99, 659.25, 587.33, 523.25, 392, 523.25, 587.33, 659.25, 587.33, 523.25]
  const beat = 0.34

  notes.forEach((frequency, index) => {
    const startAt = context.currentTime + 0.08 + index * beat
    const oscillator = context.createOscillator()
    const vibrato = context.createOscillator()
    const vibratoDepth = context.createGain()
    const filter = context.createBiquadFilter()
    const volume = context.createGain()

    oscillator.type = 'sine'
    oscillator.frequency.setValueAtTime(frequency, startAt)
    vibrato.frequency.value = 5.2
    vibratoDepth.gain.value = 4
    vibrato.connect(vibratoDepth)
    vibratoDepth.connect(oscillator.detune)
    filter.type = 'lowpass'
    filter.frequency.value = 2200
    volume.gain.setValueAtTime(0.0001, startAt)
    volume.gain.exponentialRampToValueAtTime(0.075, startAt + 0.055)
    volume.gain.exponentialRampToValueAtTime(0.0001, startAt + 0.31)
    oscillator.connect(filter)
    filter.connect(volume)
    volume.connect(tuneGain)
    oscillator.start(startAt)
    vibrato.start(startAt)
    oscillator.stop(startAt + 0.33)
    vibrato.stop(startAt + 0.34)
  })

  fluteTimer = window.setTimeout(playFlutePhrase, notes.length * beat * 1000 + 500)
}

function playChime(notes) {
  if (!soundOn.value) return
  const context = getAudioContext()
  if (!context) return

  notes.forEach((frequency, index) => {
    const startAt = context.currentTime + index * 0.11
    const oscillator = context.createOscillator()
    const volume = context.createGain()
    oscillator.type = 'sine'
    oscillator.frequency.setValueAtTime(frequency, startAt)
    volume.gain.setValueAtTime(0.0001, startAt)
    volume.gain.exponentialRampToValueAtTime(0.075, startAt + 0.025)
    volume.gain.exponentialRampToValueAtTime(0.0001, startAt + 0.42)
    oscillator.connect(volume)
    volume.connect(context.destination)
    oscillator.start(startAt)
    oscillator.stop(startAt + 0.44)
  })
}

onMounted(async () => {
  const THREE = await import('three')
  const canvas = stickerCanvas.value
  const scene = new THREE.Scene()
  const camera = new THREE.PerspectiveCamera(38, 1, 0.1, 40)
  camera.position.set(0, 0, 8)

  renderer = new THREE.WebGLRenderer({ canvas, alpha: true, antialias: true })
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2))
  renderer.outputColorSpace = THREE.SRGBColorSpace
  renderer.toneMapping = THREE.ACESFilmicToneMapping
  renderer.setClearColor(0x000000, 0)

  scene.add(new THREE.AmbientLight(0xffffff, 2.1))
  const keyLight = new THREE.DirectionalLight(0xfff0df, 3.2)
  keyLight.position.set(-3, 5, 6)
  scene.add(keyLight)

  const starShape = new THREE.Shape()
  for (let point = 0; point < 10; point += 1) {
    const radius = point % 2 === 0 ? 0.48 : 0.22
    const angle = point * Math.PI / 5 - Math.PI / 2
    const x = Math.cos(angle) * radius
    const y = Math.sin(angle) * radius
    if (point === 0) starShape.moveTo(x, y)
    else starShape.lineTo(x, y)
  }
  starShape.closePath()

  const starGeometry = new THREE.ExtrudeGeometry(starShape, {
    depth: 0.14,
    bevelEnabled: true,
    bevelSegments: 3,
    steps: 1,
    bevelSize: 0.045,
    bevelThickness: 0.04
  })
  starGeometry.center()

  const starMaterials = [
    new THREE.MeshStandardMaterial({ color: '#f2a94f', roughness: 0.3, metalness: 0.04 }),
    new THREE.MeshStandardMaterial({ color: '#7eb3a4', roughness: 0.34, metalness: 0.08 }),
    new THREE.MeshStandardMaterial({ color: '#e989a3', roughness: 0.32, metalness: 0.05 })
  ]
  const starPositions = [
    [-2.05, 0.42, 0.12, 0.88],
    [2.12, 0.95, -0.35, 0.7],
    [-2.12, -0.68, -0.4, 0.55],
    [2.15, -0.74, 0.3, 0.48]
  ]

  starMeshes = starPositions.map(([x, y, z, scale], index) => {
    const star = new THREE.Mesh(starGeometry, starMaterials[index % starMaterials.length])
    star.position.set(x, y, z)
    star.scale.setScalar(scale)
    star.userData.phase = index * 1.7
    star.userData.baseY = y
    scene.add(star)
    return star
  })

  const resize = () => {
    const { width, height } = canvas.parentElement.getBoundingClientRect()
    if (!width || !height) return
    renderer.setSize(width, height, false)
    camera.aspect = width / height
    camera.updateProjectionMatrix()
  }
  resizeObserver = new ResizeObserver(resize)
  resizeObserver.observe(canvas.parentElement)
  resize()

  const clock = new THREE.Clock()
  const animate = () => {
    const time = clock.getElapsedTime()
    starMeshes.forEach((star) => {
      star.rotation.y = Math.sin(time * 0.7 + star.userData.phase) * 0.48
      star.rotation.x = Math.cos(time * 0.55 + star.userData.phase) * 0.12
      star.position.y = star.userData.baseY + Math.sin(time + star.userData.phase) * 0.08
    })
    renderer.render(scene, camera)
    animationFrame = requestAnimationFrame(animate)
  }
  animate()
})

onBeforeUnmount(() => {
  cancelAnimationFrame(animationFrame)
  resizeObserver?.disconnect()
  renderer?.dispose()
  window.clearTimeout(deliveryTimer)
  stopAmbientSound()
  void audioContext?.close()
})
</script>

<template>
  <main class="birthday-page" :class="{ 'galaxy-theme': galaxyMode, 'cartoon-theme': wishCaught }">
    <div class="confetti confetti-one" aria-hidden="true">✦</div>
    <div class="confetti confetti-two" aria-hidden="true">✷</div>
    <div class="confetti confetti-three" aria-hidden="true">✧</div>
    <div class="confetti confetti-four" aria-hidden="true">✿</div>

    <header class="topline">
      <span class="tiny-star" aria-hidden="true">✦</span>
      <span>Birthday dispatch for Dhanashri</span>
      <span class="tiny-star" aria-hidden="true">✦</span>
    </header>

    <section class="birthday-card" aria-labelledby="birthday-title">
      <div class="card-copy">
        <p class="eyebrow"><span class="sparkle">✦</span> Today is all about you <span class="sparkle">✦</span></p>
        <h1 id="birthday-title">Happy birthday,<br /><span>Dhanashri!</span></h1>
        <p class="intro">For the girl whose sticker replies deserve their own museum.</p>
      </div>

      <div class="cake-stage" aria-label="A little pink birthday cake with candles">
        <canvas ref="stickerCanvas" class="sticker-canvas" aria-hidden="true"></canvas>
        <div class="floating-sticker sticker-chick" aria-hidden="true"><span>🐥</span><b>tiny boss</b></div>
        <div class="floating-sticker sticker-cat" aria-hidden="true"><span>😎</span><b>cool-ish</b></div>
        <div class="floating-sticker sticker-frog" aria-hidden="true"><span>🐸</span><b>cake patrol</b></div>
        <div class="cake-shadow"></div>
        <div class="cake">
          <div class="cake-topper"><span>D</span><i>✦</i></div>
          <div class="candle-row">
            <button
              v-for="(candle, index) in 3"
              :key="candle"
              class="candle"
              :class="[`candle-${index + 1}`, { 'is-lit': candlesLit }]"
              :aria-label="candlesLit ? 'Blow out the birthday candles' : 'Light the birthday candles again'"
              @click="candlesLit = !candlesLit"
            >
              <span v-if="candlesLit" class="flame" aria-hidden="true"></span>
            </button>
          </div>
          <div class="cake-upper">
            <span class="icing-drip drip-one"></span>
            <span class="icing-drip drip-two"></span>
            <span class="icing-drip drip-three"></span>
            <span class="cake-decoration deco-one">✿</span>
            <span class="cake-decoration deco-two">✦</span>
            <span class="cake-decoration deco-three">✿</span>
          </div>
          <div class="cake-lower">
            <span class="lower-decoration lower-one">✦</span>
            <span class="lower-decoration lower-two">●</span>
            <span class="lower-decoration lower-three">✦</span>
            <span class="lower-decoration lower-four">●</span>
          </div>
          <div class="cake-plate"></div>
        </div>
        <div class="stage-sparkle sparkle-a" aria-hidden="true">✧</div>
        <div class="stage-sparkle sparkle-b" aria-hidden="true">✦</div>
        <div class="stage-sparkle sparkle-c" aria-hidden="true">✧</div>
      </div>

      <div class="wish-area">
        <button class="wish-button" type="button" @click="startWishJourney">
          <span>Chase your birthday wish</span>
          <span class="button-sparkle" aria-hidden="true">✷</span>
        </button>
      </div>
    </section>

    <footer class="footer-note">Cake calories are on vacation today.</footer>

    <Transition name="galaxy">
      <section
        v-if="galaxyMode"
        class="galaxy-overlay"
        :class="{ 'universe-warm': attempts === 1, 'universe-cartoon': attempts >= 2 || wishCaught }"
        :style="skyStyle"
        aria-label="Dhanashri's birthday wish journey"
        @pointermove="moveSky"
      >
        <div class="galaxy-nebula nebula-one" aria-hidden="true"></div>
        <div class="galaxy-nebula nebula-two" aria-hidden="true"></div>
        <div class="starfield" aria-hidden="true">
          <i
            v-for="star in skyStars"
            :key="star.id"
            class="sky-star"
            :style="{
              left: `${star.x}%`,
              top: `${star.y}%`,
              width: `${star.size}px`,
              height: `${star.size}px`,
              animationDelay: star.delay,
              animationDuration: star.duration
            }"
          ></i>
        </div>

        <header class="galaxy-toolbar">
          <button class="sound-toggle" type="button" :aria-pressed="soundOn" @click="toggleSound">
            <span aria-hidden="true">{{ soundOn ? '♫' : '♪' }}</span>
            {{ soundOn ? 'Sound on' : 'Sound off' }}
          </button>
          <button class="galaxy-close" type="button" aria-label="Return to the birthday page" @click="closeGalaxy">×</button>
        </header>

        <div class="galaxy-content">
          <template v-if="!wishCaught">
            <div class="mission-copy" aria-live="polite">
              <p class="galaxy-kicker">A BIRTHDAY WISH IS LOOSE</p>
              <h2>{{ attempts === 0 ? 'There it goes!' : attempts === 1 ? 'Whoosh! It changed lanes.' : 'It did a tiny loop-de-loop!' }}</h2>
              <p>{{ attempts === 0 ? 'A shooting star is carrying something for you.' : attempts === 1 ? 'That wish zipped off with another star. Look, it popped up over there!' : 'It is showing off now. One more try, birthday girl!' }}</p>
            </div>
            <button
              class="wish-star"
              :style="targetStyle"
              type="button"
              aria-label="Catch the shooting star and birthday card"
              @click="attemptToCatchWish"
            >
              <span class="wish-star-tail" aria-hidden="true"></span>
              <span class="wish-star-symbol" aria-hidden="true">✦</span>
              <span class="wish-card-tag" aria-hidden="true">D <i>✦</i></span>
            </button>
            <div class="helper-track" :class="`helper-step-${Math.min(attempts, 3)}`" aria-hidden="true">
              <svg viewBox="0 0 90 112">
                <path d="M22 105h15m23 0h15" stroke="#f5d477" stroke-width="8" stroke-linecap="round" />
                <path d="M31 70q14-12 29 0l6 30H25z" fill="#86c7b1" />
                <path d="M34 96l-3 9m29-9 4 9" stroke="#efc29f" stroke-width="8" stroke-linecap="round" />
                <path d="M31 72 17 81m42-9 12-10" stroke="#efc29f" stroke-width="8" stroke-linecap="round" />
                <circle cx="46" cy="42" r="27" fill="#efc29f" />
                <path d="M19 42q-3-31 25-32 31 2 29 30l-11-8q-17 4-31-7l-9 15z" fill="#624331" />
                <circle cx="37" cy="44" r="2.5" fill="#523c45" />
                <circle cx="55" cy="44" r="2.5" fill="#523c45" />
                <path d="M39 55q7 6 14 0" fill="none" stroke="#a84e69" stroke-width="2.5" stroke-linecap="round" />
              </svg>
              <span>tiny helper</span>
            </div>
            <p class="galaxy-hint">The wish is getting away…</p>
          </template>

          <div v-else-if="!deliveryReady" class="caught-copy" role="status">
            <span class="caught-burst" aria-hidden="true">✦</span>
            <p class="galaxy-kicker">GOTCHA!</p>
            <h2>Your wish has a delivery buddy.</h2>
          </div>

          <div v-else class="delivery-stage">
            <p class="galaxy-kicker">SPECIAL DELIVERY FROM THE STARS</p>
            <h2>Your wish made it, Dhanashri!</h2>
            <p class="delivery-caption">A tiny helper had to take the scenic route.</p>

            <div class="delivery-scene">
              <svg class="delivery-art" viewBox="0 0 520 240" role="img" aria-labelledby="delivery-title delivery-description">
                <title id="delivery-title">A little helper delivers a birthday card to Dhanashri</title>
                <desc id="delivery-description">A smiling child runs in with a tiny birthday card while a cartoon girl waits with open arms.</desc>
                <path d="M38 207 Q260 194 482 207" fill="none" stroke="#7889bc" stroke-width="2" stroke-linecap="round" opacity=".55" />
                <g class="waiting-girl">
                  <path d="M374 155 Q401 134 430 155 L446 203 L358 203Z" fill="#f2a4b7" />
                  <path d="M382 195 L379 218 M422 195 L426 218" stroke="#efc4a4" stroke-width="12" stroke-linecap="round" />
                  <path d="M373 218 L383 218 M421 218 L433 218" stroke="#f8e5ca" stroke-width="8" stroke-linecap="round" />
                  <path d="M374 157 Q348 165 338 150 M437 157 Q455 145 461 132" fill="none" stroke="#efc4a4" stroke-width="11" stroke-linecap="round" />
                  <circle cx="401" cy="112" r="39" fill="#efc29f" />
                  <path d="M363 113 Q355 66 400 66 Q445 68 440 118 L432 103 Q422 92 416 83 Q395 103 368 99Z" fill="#543748" />
                  <path d="M369 82 Q350 92 363 111 M435 82 Q453 94 440 112" fill="none" stroke="#543748" stroke-width="13" stroke-linecap="round" />
                  <circle cx="388" cy="115" r="2.8" fill="#523c45" />
                  <circle cx="414" cy="115" r="2.8" fill="#523c45" />
                  <path d="M391 130 Q401 139 412 129" fill="none" stroke="#a84e69" stroke-width="3" stroke-linecap="round" />
                  <circle cx="379" cy="126" r="6" fill="#e992a6" opacity=".6" />
                  <circle cx="422" cy="126" r="6" fill="#e992a6" opacity=".6" />
                  <path d="M396 69 L403 53 L410 69" fill="#e9b64f" />
                </g>
                <g class="delivery-kid">
                  <path d="M100 149 Q121 133 146 150 L153 194 L94 194Z" fill="#86c7b1" />
                  <path d="M108 188 L104 214 M139 188 L145 214" stroke="#efc29f" stroke-width="10" stroke-linecap="round" />
                  <path d="M99 215 L110 215 M141 215 L153 215" stroke="#f5d477" stroke-width="8" stroke-linecap="round" />
                  <path d="M101 151 Q83 160 72 145 M146 152 Q163 145 176 129" fill="none" stroke="#efc29f" stroke-width="10" stroke-linecap="round" />
                  <circle cx="124" cy="112" r="34" fill="#efc29f" />
                  <path d="M91 111 Q88 73 120 72 Q156 74 157 106 L145 99 Q127 101 110 93 L96 109Z" fill="#624331" />
                  <circle cx="113" cy="114" r="2.6" fill="#523c45" />
                  <circle cx="136" cy="114" r="2.6" fill="#523c45" />
                  <path d="M115 127 Q124 135 134 126" fill="none" stroke="#a84e69" stroke-width="2.7" stroke-linecap="round" />
                  <path d="M169 119 L226 104 L242 137 L184 151Z" fill="#fff2bd" stroke="#d7b76b" stroke-width="2" class="delivered-card" />
                  <path d="M194 124 L205 134 L222 115" fill="none" stroke="#df8c9f" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" class="card-sparkle" />
                </g>
                <path d="M279 87 l5 12 13 1 -10 8 3 12 -11 -7 -11 7 3 -12 -10 -8 13 -1Z" fill="#f2bd58" class="art-star star-a" />
                <path d="M322 155 l3 7 8 1 -6 5 2 8 -7 -4 -7 4 2 -8 -6 -5 8 -1Z" fill="#8ac8b5" class="art-star star-b" />
                <circle cx="258" cy="171" r="4" fill="#f5d386" class="art-dot dot-a" />
                <circle cx="306" cy="73" r="3" fill="#e99aae" class="art-dot dot-b" />
              </svg>
            </div>

            <article class="delivered-wish-card">
              <span class="wish-card-stamp" aria-hidden="true">✦</span>
              <p>YOUR OFFICIAL BIRTHDAY REPORT</p>
              <h3>Unlimited cake. Unlimited stickers.</h3>
              <span>Wisdom level: still loading…</span>
            </article>
            <button class="back-button" type="button" @click="closeGalaxy">Back to the cake</button>
          </div>
        </div>
      </section>
    </Transition>
  </main>
</template>