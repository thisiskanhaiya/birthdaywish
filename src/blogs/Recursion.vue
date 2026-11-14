<script setup>
import { onBeforeUnmount, onMounted, ref } from "vue";
import recursionHero from "../assets/recursion-hero.png";

defineEmits(["back"]);

const readingProgress = ref(0);

function updateReadingProgress() {
  const pageHeight =
    document.documentElement.scrollHeight -
    window.innerHeight;

  readingProgress.value =
    pageHeight > 0
      ? Math.min((window.scrollY / pageHeight) * 100, 100)
      : 0;
}

onMounted(() => {
  updateReadingProgress();

  window.addEventListener(
    "scroll",
    updateReadingProgress,
    { passive: true }
  );
});

onBeforeUnmount(() => {
  window.removeEventListener(
    "scroll",
    updateReadingProgress
  );
});
</script>

<template>
  <article class="blog-reading-page">
    <div
      class="reading-progress"
      :style="{ width: `${readingProgress}%` }"
    ></div>

    <!-- ARTICLE NAVIGATION -->
    <header class="article-navigation">
      <button
        type="button"
        aria-label="Back to all blogs"
        @click="$emit('back')"
      >
        ←
      </button>

      <strong>
        little.log <span>♡</span>
      </strong>

      <div>
        <button type="button" aria-label="Save article">
          ♡
        </button>

        <button type="button" aria-label="More options">
          •••
        </button>
      </div>
    </header>

    <!-- ARTICLE HERO -->
    <section class="article-hero-image">
      <img
        :src="recursionHero"
        alt="A person looking toward a mountain landscape"
      />

      <p>
        Some loops<br />
        are meant to end<br />
        so you can<br />
        begin again ♡
      </p>
    </section>

    <!-- ARTICLE CONTENT -->
    <section class="article-content">
      <div class="article-meta">
        <span>Life × Tech</span>
        <small>3 min read</small>
      </div>

      <h1>
        Finding the<br />
        Base Condition
      </h1>

      <p class="article-subtitle">
        Sometimes you just need to return.
      </p>

      <div class="article-author">
        <div class="author-avatar">
          l
        </div>

        <div>
          <strong>by little.log</strong>
          <small>Thought #01</small>
        </div>

        <div class="article-reactions">
          <span>♡ 412</span>
          <span>◯ 28</span>
          <span>⇧</span>
        </div>
      </div>

      <div class="article-body">
        <p>
          In programming, recursion happens when a function
          calls itself. It’s powerful, but without a base
          condition, it never stops.
        </p>

        <p>
          Life can feel the same sometimes. The same routine,
          thought or situation returns, and we enter it with
          the same response.
        </p>

        <div class="article-code">
          <header>
            <div>
              <span></span>
              <span></span>
              <span></span>
            </div>

            <small>life.js</small>
          </header>

          <pre><code><span class="code-purple">function</span> repeat(pattern) {
  <span class="code-purple">if</span> (pattern.isDraining) <span class="code-pink">return</span>;
  <span class="code-purple">return</span> repeat(pattern);
}</code></pre>
        </div>

        <aside class="article-note">
          <span>♡</span>

          <p>
            Maybe the question isn’t
            “Why am I in this loop?” but
            <strong>“What will help me return?”</strong>
          </p>
        </aside>

        <h2>Some loops are worth keeping.</h2>

        <p>
          Practicing, learning and caring can add something
          with every iteration. The point is not to escape
          every loop. The point is to notice what the loop is
          doing to you.
        </p>

        <div class="article-choices">
          <div class="article-choice continue">
            <span>🌱</span>

            <div>
              <small>Continue</small>
              <strong>When it adds value</strong>
              <p>
                More clarity, skill, peace or connection.
              </p>
            </div>
          </div>

          <div class="article-choice return">
            <span>🍂</span>

            <div>
              <small>Return</small>
              <strong>When it drains you</strong>
              <p>
                Less energy, confidence, patience or joy.
              </p>
            </div>
          </div>
        </div>

        <div class="article-question">
          <small>Before the next call...</small>

          <p>
            Is this loop growing you or only repeating you?
          </p>
        </div>

        <p>
          Keep the recursions that help you grow. When every
          iteration takes more than it gives, define the base
          condition and allow yourself to return.
        </p>

        <div class="article-ending">
          <span>↻</span>

          <p>
            You do not need to debug your entire life today.
          </p>

          <strong>
            Just notice the loop you are currently inside.
          </strong>
        </div>
      </div>

      <footer class="article-footer">
        <button type="button" @click="$emit('back')">
          ← Back to all thoughts
        </button>

        <span>
          keep<br />
          going ♡
        </span>
      </footer>
    </section>
  </article>
</template>
