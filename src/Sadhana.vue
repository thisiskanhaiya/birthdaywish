<script setup>
import { ref } from "vue";

defineEmits(["back"]);

const selected = ref("");
</script>

<template>
  <article class="reader sadhana-reader">

    <!-- NAVIGATION -->
    <header class="reader-nav">
      <button
        type="button"
        aria-label="Back"
        @click="$emit('back')"
      >
        ←
      </button>

      <strong>
        little.log <span>♡</span>
      </strong>

      <button type="button" aria-label="Save">
        ♡
      </button>
    </header>


    <!-- ==================================================
         HERO
    =================================================== -->

    <section class="sadhana-hero">

      <div class="morning-sun"></div>

      <span class="sadhana-spark spark-one">✦</span>
      <span class="sadhana-spark spark-two">♡</span>

      <!-- City side -->
      <div class="city-world">

        <div class="city-building building-one"></div>
        <div class="city-building building-two"></div>
        <div class="city-building building-three"></div>

        <div class="city-phone">
          <span>⚡</span>
          <small>everything<br />now</small>
        </div>

      </div>


      <!-- Path -->
      <div class="village-path"></div>


      <!-- Village side -->
      <div class="village-world">

        <div class="village-house">
          <div class="house-roof"></div>
          <div class="house-body">
            <span></span>
          </div>
        </div>

        <div class="village-tree">
          <span class="tree-top tree-one"></span>
          <span class="tree-top tree-two"></span>
          <span class="tree-trunk"></span>
        </div>

      </div>


      <!-- Question card -->

      <div class="sadhana-question">

        <small>A WEEKEND EXPERIMENT</small>

        <p>
          Could you spend 24 hours somewhere
          without your phone or internet?
        </p>

        <div class="sadhana-options">

          <button
            type="button"
            :class="{ selected: selected === 'yes' }"
            @click="selected = 'yes'"
          >
            I'd try it 🌿
          </button>

          <button
            type="button"
            :class="{ selected: selected === 'hard' }"
            @click="selected = 'hard'"
          >
            Honestly... difficult 😅
          </button>

        </div>


        <div v-if="selected" class="sadhana-response">

          <template v-if="selected === 'yes'">
            Then someone in India really needs to build this.
          </template>

          <template v-else>
            That's exactly why the experiment might be interesting.
          </template>

        </div>

      </div>


      <div class="hero-hand-note">
        less signal.<br />
        more you. ♡
      </div>

    </section>


    <!-- ==================================================
         ARTICLE
    =================================================== -->

    <section class="reader-content">

      <div class="reader-meta">

        <span class="sadhana-tag">
          Life
        </span>

        <small>
          5 min read
        </small>

      </div>


      <h1>
        Someone Should<br />
        Build This<br />
        in India.
      </h1>


      <p class="reader-subtitle">
        We are learning to control almost everything around us.
        Except ourselves.
      </p>


      <div class="author">

        <span class="author-circle sadhana-author">
          l
        </span>

        <div>
          <strong>by little.log</strong>
          <small>Thought #04</small>
        </div>

        <div class="reactions">
          <span>♡ 284</span>
          <span>◯ 31</span>
        </div>

      </div>


      <div class="story">

        <!-- OPENING -->

        <p>
          For the last few weeks, I've been speaking with
          different people working in technology.
        </p>

        <p>
          Different jobs. Different companies. Different cities.
          Different lives.
        </p>

        <p>
          Yet one thing keeps coming up:
        </p>


        <div class="tired-note">

          <span>☾</span>

          <p>
            “I sleep... but somehow I still don't feel
            properly rested.”
          </p>

        </div>


        <p>
          People finish work, but the mind doesn't always
          finish with work.
        </p>

        <p>
          You lie down to sleep and suddenly the brain remembers
          tomorrow's meeting, an unfinished task, a conversation,
          an idea, a reel...
        </p>

        <p>
          And one thought calls another.
        </p>


        <!-- CONTRADICTION -->

        <div class="human-question">

          <small>AND THAT MADE ME THINK...</small>

          <p>
            How did we become so powerful outside ourselves,
            but remain so difficult to control inside?
          </p>

        </div>


        <h2>
          Look at the world we built.
        </h2>


        <div class="instant-grid">

          <div class="instant-item">
            <span>🍲</span>
            <strong>Hungry?</strong>
            <p>Food comes to you.</p>
          </div>

          <div class="instant-item">
            <span>✈</span>
            <strong>Far away?</strong>
            <p>Fly there in hours.</p>
          </div>

          <div class="instant-item">
            <span>⌘</span>
            <strong>Have an idea?</strong>
            <p>Build a prototype tonight.</p>
          </div>

          <div class="instant-item">
            <span>♫</span>
            <strong>Want a song?</strong>
            <p>It starts in seconds.</p>
          </div>

        </div>


        <p>
          Human beings have become incredibly good at telling
          the outside world:
        </p>


        <div class="command-note">
          “Do this for me.”
        </div>


        <p>
          And increasingly, the world responds.
        </p>


        <h2>
          Now try commanding yourself.
        </h2>


        <!-- Fake API -->

        <div class="body-api">

          <header>
            <span></span>
            <span></span>
            <span></span>

            <small>human.js</small>
          </header>

          <code>
            <span>
              <b>sleep</b>(withinFiveMinutes);
            </span>

            <span class="api-error">
              → command unavailable
            </span>

            <span>
              <b>makeMood</b>("happy");
            </span>

            <span class="api-error">
              → cannot guarantee result
            </span>

            <span>
              <b>increaseStrength</b>(40%);
            </span>

            <span class="api-error">
              → training required
            </span>
          </code>

        </div>


        <p>
          You can play a happy song.
        </p>

        <p>
          That doesn't guarantee happiness.
        </p>

        <p>
          You can lie in bed for eight hours.
        </p>

        <p>
          That doesn't guarantee deep rest.
        </p>

        <p>
          Your heart needs training.
          Your muscles need movement.
          Attention needs practice.
        </p>


        <div class="beauty-note">

          <span>♡</span>

          <div>
            <small>AND MAYBE THAT'S BEAUTIFUL.</small>

            <p>
              We can command machines.
              But we still have to train ourselves.
            </p>
          </div>

        </div>


        <!-- IDEA -->

        <h2>
          Which made me think...
        </h2>


        <div class="india-idea">

          <span class="india-tape"></span>

          <small>SOMEONE PLEASE BUILD THIS 🇮🇳</small>

          <p>
            A simple weekend near our cities where
            nothing is instant.
          </p>

          <span class="india-heart">♡</span>

        </div>


        <p>
          Not another luxury wellness resort.
        </p>

        <p>
          Not an expensive “digital detox retreat.”
        </p>

        <p>
          Something much simpler.
        </p>


        <!-- Week simulation -->

        <div class="weekend-card">

          <div class="weekend-heading">
            <span>🌿</span>

            <div>
              <small>IMAGINE SATURDAY</small>
              <strong>90 minutes outside your city.</strong>
            </div>
          </div>


          <div class="weekend-step">

            <span>10:00</span>

            <div>
              <strong>Phone goes away.</strong>
              <p>Family gets an emergency contact number.</p>
            </div>

          </div>


          <div class="weekend-step">

            <span>12:30</span>

            <div>
              <strong>Simple local food.</strong>
              <p>Maybe you even help prepare it.</p>
            </div>

          </div>


          <div class="weekend-step">

            <span>16:00</span>

            <div>
              <strong>Walk. Play. Talk.</strong>
              <p>No notifications deciding what comes next.</p>
            </div>

          </div>


          <div class="weekend-step">

            <span>21:30</span>

            <div>
              <strong>Nothing left to do.</strong>
              <p>And that's the point.</p>
            </div>

          </div>

        </div>


        <p>
          No Netflix.
        </p>

        <p>
          No “one final reel.”
        </p>

        <p>
          No late-night Teams message.
        </p>

        <p>
          No sudden urge to open the laptop because an idea
          entered your head at 12:37 AM.
        </p>

        <p>
          Just a clean place to sleep.
        </p>


        <div class="night-note">

          <span>☾</span>

          <p>
            For one night,
            nothing needs to happen.
          </p>

        </div>


        <!-- VILLAGE ECONOMY -->

        <h2>
          And the village shouldn't just be the location.
        </h2>

        <p>
          This part matters.
        </p>

        <p>
          I don't imagine a company buying land beside a village,
          building a fancy resort and using “village life”
          as marketing.
        </p>

        <p>
          The community should participate in the value.
        </p>


        <div class="community-grid">

          <div>
            <span>🍲</span>
            <strong>Local food</strong>
            <p>Families and local kitchens.</p>
          </div>

          <div>
            <span>🌾</span>
            <strong>Local activities</strong>
            <p>Farms, crafts and walks.</p>
          </div>

          <div>
            <span>🏡</span>
            <strong>Local spaces</strong>
            <p>Simple, clean accommodation.</p>
          </div>

          <div>
            <span>🤝</span>
            <strong>Local income</strong>
            <p>Operations owned with the community.</p>
          </div>

        </div>


        <p>
          Then the exchange becomes interesting.
        </p>

        <p>
          City people get something increasingly rare:
          <strong>space, slowness and disconnection.</strong>
        </p>

        <p>
          Villages gain another source of economic activity
          without needing to become cities.
        </p>


        <!-- POCKET -->

        <h2>
          But here's the experiment I really want.
        </h2>


        <div class="pocket-test">

          <span class="pocket-icon">📱</span>

          <small>PHONE HANDED OVER AT 10:00 AM</small>

          <p>
            When would your hand first reach into your pocket
            automatically?
          </p>


          <div class="time-options">
            <span>10:07?</span>
            <span>10:26?</span>
            <span>11:40?</span>
          </div>


          <strong>
            And when the phone isn't there...
            what appears instead?
          </strong>

        </div>


        <div class="what-appears">

          <span>boredom?</span>
          <span>restlessness?</span>
          <span>ideas?</span>
          <span>sleepiness?</span>
          <span>conversation?</span>
          <span>peace?</span>

        </div>


        <p>
          We talk constantly about screen time.
        </p>

        <p>
          I'm becoming more interested in a different question:
        </p>


        <div class="big-question">

          <small>WHEN THE SCREEN DISAPPEARS...</small>

          <p>
            What appears?
          </p>

        </div>


        <!-- SADHANA -->

        <h2>
          Maybe that's where sadhana comes in.
        </h2>

        <p>
          Not necessarily in a religious sense.
        </p>

        <p>
          I mean the simpler idea behind it:
        </p>


        <div class="sadhana-definition">

          <span>◌</span>

          <p>
            Some things within us are
            <strong>cultivated</strong>,
            not delivered.
          </p>

        </div>


        <p>
          You practise sleeping at better times.
        </p>

        <p>
          You practise moving your body.
        </p>

        <p>
          You practise attention.
        </p>

        <p>
          You practise not reacting immediately.
        </p>

        <p>
          You practise staying with something even when
          there is no instant reward.
        </p>


        <!-- FINAL INTERACTIVE QUESTION -->

        <div class="final-weekend-question">

          <small>SO... WOULD YOU GO?</small>

          <h3>
            One phone-free weekend.
          </h3>


          <div class="weekend-features">

            <span>🌿 village stay</span>
            <span>📵 no phone</span>
            <span>🍲 local food</span>
            <span>🏏 outdoor games</span>
            <span>🌙 quiet night</span>
            <span>🌅 slow morning</span>

          </div>


          <p>
            Not to escape technology.
          </p>

          <p>
            Just to discover whether you can still be
            comfortable when technology temporarily disappears.
          </p>

        </div>


        <div class="story-finish sadhana-finish">

          <span>◌</span>

          <p>
            Maybe progress isn't only controlling more.
          </p>

          <strong>
            Maybe some progress happens when we learn
            to control ourselves. ♡
          </strong>

        </div>

      </div>


      <footer class="reader-footer">

        <button
          type="button"
          @click="$emit('back')"
        >
          ← Back to all thoughts
        </button>

        <span>
          maybe that's<br />
          our sadhana ♡
        </span>

      </footer>

    </section>

  </article>
</template>


<style scoped>

/* ==================================================
   HERO
================================================== */

.sadhana-hero {
  position: relative;

  min-height: 500px;

  overflow: hidden;

  background:
    radial-gradient(
      circle at 80% 15%,
      #ffe59b 0 9%,
      transparent 22%
    ),
    linear-gradient(
      145deg,
      #cfeeff,
      #e3ddff 35%,
      #ffe0e9 67%,
      #ffe8bd
    );
}

.morning-sun {
  position: absolute;

  top: 45px;
  right: 62px;

  width: 90px;
  height: 90px;

  border-radius: 50%;

  background: rgba(255, 222, 116, .68);
}

.sadhana-spark {
  position: absolute;

  z-index: 5;

  color: #806db1;

  font-size: 25px;
}

.spark-one {
  top: 42px;
  left: 44px;
}

.spark-two {
  top: 92px;
  left: 91px;

  color: #e76b99;
}


/* ==================================================
   CITY
================================================== */

.city-world {
  position: absolute;

  right: 65px;
  bottom: 35px;

  width: 240px;
  height: 245px;
}

.city-building {
  position: absolute;

  bottom: 0;

  border: 3px solid #55506b;

  background: #aaa3db;
}

.building-one {
  left: 0;

  width: 65px;
  height: 155px;
}

.building-two {
  left: 72px;

  width: 72px;
  height: 210px;

  background: #8f8bc7;
}

.building-three {
  right: 10px;

  width: 75px;
  height: 130px;

  background: #b8acd7;
}

.city-building::after {
  position: absolute;

  inset: 15px;

  background:
    repeating-linear-gradient(
      to bottom,
      #ffe8a9 0 8px,
      transparent 8px 23px
    );

  content: "";
}

.city-phone {
  position: absolute;

  z-index: 4;

  top: 18px;
  right: -25px;

  width: 86px;
  height: 125px;

  border: 4px solid #4b435c;
  border-radius: 18px;

  display: flex;
  flex-direction: column;

  align-items: center;
  justify-content: center;

  color: #705675;

  background: #fff6fa;

  box-shadow:
    5px 7px 15px rgba(51,42,68,.13);

  transform: rotate(8deg);
}

.city-phone > span {
  color: #e89749;

  font-size: 29px;
}

.city-phone small {
  margin-top: 5px;

  font-family: "DM Mono";
  font-size: 6px;

  text-align: center;
}


/* ==================================================
   VILLAGE
================================================== */

.village-world {
  position: absolute;

  left: 48px;
  bottom: 34px;

  width: 230px;
  height: 180px;
}

.village-house {
  position: absolute;

  left: 60px;
  bottom: 0;

  width: 120px;
  height: 115px;
}

.house-roof {
  position: absolute;

  top: 0;
  left: 5px;

  width: 110px;
  height: 58px;

  background: #ca795d;

  clip-path:
    polygon(
      50% 0,
      100% 100%,
      0 100%
    );
}

.house-body {
  position: absolute;

  bottom: 0;
  left: 20px;

  width: 80px;
  height: 70px;

  border: 3px solid #735a4f;

  background: #f3c991;
}

.house-body > span {
  position: absolute;

  bottom: 0;
  left: 30px;

  width: 27px;
  height: 45px;

  background: #885c4c;
}

.village-tree {
  position: absolute;

  left: 0;
  bottom: 5px;

  width: 75px;
  height: 130px;
}

.tree-trunk {
  position: absolute;

  left: 34px;
  bottom: 0;

  width: 12px;
  height: 65px;

  background: #765448;
}

.tree-top {
  position: absolute;

  border-radius: 50%;

  background: #6fa276;
}

.tree-one {
  top: 10px;

  width: 70px;
  height: 70px;
}

.tree-two {
  top: 0;
  left: 24px;

  width: 55px;
  height: 55px;

  background: #80ad76;
}


/* ==================================================
   PATH
================================================== */

.village-path {
  position: absolute;

  left: 250px;
  bottom: -25px;

  width: 180px;
  height: 290px;

  background:
    linear-gradient(
      #ffe6a9,
      #dbae76
    );

  clip-path:
    polygon(
      45% 0,
      54% 0,
      100% 100%,
      0 100%
    );

  opacity: .75;
}


/* ==================================================
   HERO QUESTION
================================================== */

.sadhana-question {
  position: absolute;

  z-index: 20;

  top: 48px;
  left: 44px;

  width: 315px;

  padding: 22px;

  border: 1px solid rgba(68,54,91,.1);
  border-radius: 18px;

  background: rgba(255,255,255,.88);

  box-shadow:
    0 18px 38px rgba(62,48,91,.11);

  backdrop-filter: blur(13px);

  transform: rotate(-2deg);
}

.sadhana-question small,
.tired-note small,
.human-question small,
.india-idea small,
.weekend-heading small,
.pocket-test small,
.big-question small,
.final-weekend-question small {
  color: #8875aa;

  font-family: "DM Mono";
  font-size: 6px;

  letter-spacing: .8px;
}

.sadhana-question > p {
  margin: 8px 0 14px;

  color: #504757;

  font-family: "Patrick Hand";
  font-size: 19px;

  line-height: 1.12;
}

.sadhana-options {
  display: grid;

  grid-template-columns: 1fr 1fr;

  gap: 7px;
}

.sadhana-options button {
  padding: 10px;

  border: 1px solid #ded7e5;
  border-radius: 10px;

  color: #696171;
  background: white;

  font-size: 8px;
}

.sadhana-options button.selected {
  border-color: #94b899;

  color: #55715a;
  background: #eaf6e8;
}

.sadhana-response {
  margin-top: 9px;
  padding: 9px 10px;

  border-radius: 9px;

  color: #75566b;
  background: #fff0f5;

  font-family: "Patrick Hand";
  font-size: 13px;
}

.hero-hand-note {
  position: absolute;

  z-index: 10;

  right: 24px;
  top: 28px;

  color: #745e76;

  font-family: "Patrick Hand";
  font-size: 17px;

  line-height: 1.05;

  text-align: right;

  transform: rotate(5deg);
}


/* ==================================================
   BLOG
================================================== */

.sadhana-tag {
  color: #a65374 !important;

  background: #ffe2eb !important;
}

.sadhana-author {
  background: #7aaf80;
}


/* ==================================================
   TIRED NOTE
================================================== */

.tired-note {
  margin: 27px 0;
  padding: 21px;

  border-radius: 14px;

  display: flex;
  align-items: center;

  gap: 14px;

  background:
    linear-gradient(
      135deg,
      #e6e4ff,
      #f3eaff
    );
}

.tired-note > span {
  color: #7769ad;

  font-size: 28px;
}

.tired-note p {
  margin: 0;

  color: #554b5d;

  font-family: "Patrick Hand";
  font-size: 18px;

  line-height: 1.15;
}


/* ==================================================
   HUMAN QUESTION
================================================== */

.human-question {
  margin: 28px 0;
  padding: 23px;

  border-radius: 15px;

  color: white;

  background:
    linear-gradient(
      135deg,
      #6572ac,
      #8869ad 55%,
      #b9719b
    );

  box-shadow:
    0 13px 27px rgba(78,68,120,.16);
}

.human-question small {
  color: rgba(255,255,255,.68);
}

.human-question p {
  margin: 9px 0 0;

  font-family: "Patrick Hand";
  font-size: 19px;

  line-height: 1.15;
}


/* ==================================================
   INSTANT GRID
================================================== */

.instant-grid {
  margin: 27px 0;

  display: grid;

  grid-template-columns: 1fr 1fr;

  gap: 10px;
}

.instant-item {
  padding: 17px;

  border-radius: 13px;

  background:
    linear-gradient(
      145deg,
      #f6f3ff,
      #fff2f5
    );
}

.instant-item > span {
  display: block;

  margin-bottom: 7px;

  font-size: 22px;
}

.instant-item strong {
  display: block;

  color: #514955;

  font-size: 9px;
}

.instant-item p {
  margin: 4px 0 0;

  color: #83808a;

  font-size: 7px;
}


.command-note {
  width: fit-content;

  margin: 27px auto;
  padding: 17px 28px;

  border-radius: 12px;

  color: white;

  background: #27253f;

  box-shadow:
    4px 6px 0 #ddd5ff;

  font-family: "Patrick Hand";
  font-size: 20px;
}


/* ==================================================
   HUMAN API
================================================== */

.body-api {
  margin: 28px 0;

  overflow: hidden;

  border-radius: 14px;

  color: #e6deff;
  background: #25233c;

  box-shadow:
    0 15px 31px rgba(36,30,58,.17);
}

.body-api header {
  padding: 10px 13px;

  display: flex;
  align-items: center;

  gap: 5px;

  background: #322e49;
}

.body-api header > span {
  width: 8px;
  height: 8px;

  border-radius: 50%;
}

.body-api header > span:first-child {
  background: #ef7277;
}

.body-api header > span:nth-child(2) {
  background: #efc65e;
}

.body-api header > span:nth-child(3) {
  background: #75bd79;
}

.body-api header small {
  margin-left: auto;

  color: #aba5b9;

  font-family: "DM Mono";
  font-size: 7px;
}

.body-api code {
  padding: 21px;

  display: flex;
  flex-direction: column;

  gap: 5px;

  font-family: "DM Mono";
  font-size: 9px;
}

.body-api b {
  color: #b7a3ff;
}

.api-error {
  margin-bottom: 7px;

  color: #ef8fb7;
}


/* ==================================================
   BEAUTY
================================================== */

.beauty-note {
  margin: 29px 0;
  padding: 22px;

  border-radius: 14px;

  display: flex;
  align-items: center;

  gap: 14px;

  background: #e8f4e6;
}

.beauty-note > span {
  color: #e27299;

  font-size: 27px;
}

.beauty-note small {
  color: #78917a;

  font-family: "DM Mono";
  font-size: 6px;
}

.beauty-note p {
  margin: 6px 0 0;

  color: #4d5e50;

  font-family: "Patrick Hand";
  font-size: 18px;

  line-height: 1.15;
}


/* ==================================================
   INDIA IDEA
================================================== */

.india-idea {
  position: relative;

  margin: 32px 0;
  padding: 30px 24px;

  background: #ffe5a6;

  box-shadow:
    4px 6px 15px rgba(66,53,38,.09);

  text-align: center;

  transform: rotate(-1deg);
}

.india-tape {
  position: absolute;

  top: -13px;
  left: calc(50% - 40px);

  width: 80px;
  height: 26px;

  background: rgba(208,192,240,.7);

  transform: rotate(3deg);
}

.india-idea p {
  max-width: 400px;

  margin: 9px auto 0;

  color: #5b4d54;

  font-family: "Patrick Hand";
  font-size: 20px;

  line-height: 1.12;
}

.india-heart {
  position: absolute;

  right: 15px;
  bottom: 9px;

  color: #df6797;

  font-size: 21px;
}


/* ==================================================
   WEEKEND
================================================== */

.weekend-card {
  margin: 27px 0;
  padding: 23px;

  border: 1px solid #dcd8e4;
  border-radius: 17px;

  background: #fffafd;
}

.weekend-heading {
  margin-bottom: 15px;

  display: flex;
  align-items: center;

  gap: 12px;
}

.weekend-heading > span {
  font-size: 27px;
}

.weekend-heading strong {
  display: block;

  margin-top: 4px;

  color: #4e4751;

  font-size: 11px;
}

.weekend-step {
  padding: 14px 0;

  border-bottom: 1px dashed #ddd6df;

  display: grid;

  grid-template-columns: 50px 1fr;

  gap: 10px;
}

.weekend-step:last-child {
  border-bottom: 0;
}

.weekend-step > span {
  color: #836eb0;

  font-family: "DM Mono";
  font-size: 7px;
}

.weekend-step strong {
  display: block;

  color: #514a54;

  font-size: 9px;
}

.weekend-step p {
  margin: 4px 0 0;

  color: #85808a;

  font-size: 7px;
}


/* ==================================================
   NIGHT
================================================== */

.night-note {
  margin: 28px 0;
  padding: 24px;

  border-radius: 15px;

  display: flex;
  align-items: center;

  gap: 14px;

  color: #eee9ff;

  background:
    linear-gradient(
      135deg,
      #282743,
      #4f4166
    );
}

.night-note > span {
  color: #ffdb83;

  font-size: 30px;
}

.night-note p {
  margin: 0;

  font-family: "Patrick Hand";
  font-size: 20px;

  line-height: 1.1;
}


/* ==================================================
   COMMUNITY
================================================== */

.community-grid {
  margin: 27px 0;

  display: grid;

  grid-template-columns: 1fr 1fr;

  gap: 10px;
}

.community-grid > div {
  padding: 18px;

  border-radius: 13px;

  background:
    linear-gradient(
      145deg,
      #edf6e9,
      #f8fff5
    );
}

.community-grid span {
  display: block;

  margin-bottom: 8px;

  font-size: 22px;
}

.community-grid strong {
  color: #526055;

  font-size: 9px;
}

.community-grid p {
  margin: 4px 0 0;

  color: #818981;

  font-size: 7px;
}


/* ==================================================
   POCKET EXPERIMENT
================================================== */

.pocket-test {
  margin: 28px 0;
  padding: 26px;

  border-radius: 16px;

  background:
    linear-gradient(
      135deg,
      #e9e5ff,
      #ffe8f1
    );

  text-align: center;
}

.pocket-icon {
  display: block;

  margin-bottom: 9px;

  font-size: 30px;
}

.pocket-test p {
  margin: 10px auto;

  max-width: 400px;

  color: #5d5362;

  font-family: "Patrick Hand";
  font-size: 18px;

  line-height: 1.15;
}

.time-options {
  margin: 14px 0;

  display: flex;
  justify-content: center;

  gap: 8px;
}

.time-options span {
  padding: 7px 11px;

  border-radius: 50px;

  color: #6d6095;
  background: white;

  font-family: "DM Mono";
  font-size: 7px;
}

.pocket-test > strong {
  color: #55465d;

  font-size: 10px;
}


/* ==================================================
   WHAT APPEARS
================================================== */

.what-appears {
  margin: 25px 0;

  display: flex;
  flex-wrap: wrap;

  justify-content: center;

  gap: 8px;
}

.what-appears span {
  padding: 8px 12px;

  border: 1px solid #e0d9e4;
  border-radius: 50px;

  color: #766d7a;
  background: white;

  font-family: "Patrick Hand";
  font-size: 13px;
}


/* ==================================================
   BIG QUESTION
================================================== */

.big-question {
  margin: 30px 0;
  padding: 29px;

  border-radius: 15px;

  color: white;

  background:
    linear-gradient(
      135deg,
      #6276ad,
      #8068ad 52%,
      #b86f9b
    );

  text-align: center;
}

.big-question small {
  color: rgba(255,255,255,.67);
}

.big-question p {
  margin: 9px 0 0;

  font-family: "Patrick Hand";
  font-size: 27px;
}


/* ==================================================
   SADHANA
================================================== */

.sadhana-definition {
  margin: 28px 0;
  padding: 23px;

  border-radius: 14px;

  display: flex;
  align-items: center;

  gap: 15px;

  background: #fff1dc;
}

.sadhana-definition > span {
  color: #af805a;

  font-size: 30px;
}

.sadhana-definition p {
  margin: 0;

  color: #604f4b;

  font-family: "Patrick Hand";
  font-size: 19px;

  line-height: 1.13;
}


/* ==================================================
   FINAL QUESTION
================================================== */

.final-weekend-question {
  margin: 34px 0;
  padding: 28px;

  border: 1px solid #ddd6e4;
  border-radius: 17px;

  background:
    linear-gradient(
      145deg,
      #f4f1ff,
      #fff4f7
    );

  text-align: center;
}

.final-weekend-question h3 {
  margin: 8px 0 15px;

  color: #4f4656;

  font-family: "Patrick Hand";
  font-size: 26px;
  font-weight: 500;
}

.weekend-features {
  margin-bottom: 18px;

  display: flex;
  flex-wrap: wrap;

  justify-content: center;

  gap: 7px;
}

.weekend-features span {
  padding: 7px 10px;

  border-radius: 50px;

  color: #625b68;
  background: white;

  font-size: 7px;
}

.final-weekend-question p {
  margin: 8px auto;

  max-width: 450px;

  color: #77717c;

  font-size: 9px;

  line-height: 1.55;
}

.sadhana-finish {
  background:
    linear-gradient(
      135deg,
      #fff9e8,
      #eaf4e9,
      #eeeaff
    );
}


/* ==================================================
   MOBILE
================================================== */

@media (max-width: 600px) {

  .sadhana-hero {
    min-height: 475px;
  }

  .sadhana-question {
    top: 25px;
    left: 16px;
    right: 16px;

    width: auto;

    padding: 18px;
  }

  .sadhana-question > p {
    font-size: 16px;
  }

  .sadhana-options {
    grid-template-columns: 1fr;
  }

  .city-world {
    right: -45px;
    bottom: 18px;

    transform: scale(.63);

    transform-origin: bottom right;
  }

  .village-world {
    left: -35px;
    bottom: 18px;

    transform: scale(.63);

    transform-origin: bottom left;
  }

  .village-path {
    left: calc(50% - 75px);
    bottom: -40px;

    width: 150px;
    height: 190px;
  }

  .hero-hand-note {
    display: none;
  }

  .instant-grid,
  .community-grid {
    grid-template-columns: 1fr 1fr;
  }

  .time-options {
    flex-wrap: wrap;
  }

}
</style>
