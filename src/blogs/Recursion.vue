<script setup>
import { onBeforeUnmount, onMounted, ref } from "vue";

defineEmits(["back"]);

const readingProgress = ref(0);

const updateReadingProgress = () => {
  const scrollTop = window.scrollY;
  const scrollHeight =
    document.documentElement.scrollHeight - window.innerHeight;

  readingProgress.value =
    scrollHeight > 0 ? Math.min((scrollTop / scrollHeight) * 100, 100) : 0;
};

onMounted(() => {
  window.addEventListener("scroll", updateReadingProgress, {
    passive: true,
  });

  updateReadingProgress();
});

onBeforeUnmount(() => {
  window.removeEventListener("scroll", updateReadingProgress);
});
</script>

<template>
  <article class="article-page">
    <div
      class="reading-progress"
      :style="{ width: `${readingProgress}%` }"
    ></div>

    <header class="article-topbar">
      <button type="button" @click="$emit('back')">
        <span>←</span>
        Back to stories
      </button>

      <div class="article-mini-brand">
        <span>l</span>
        little.log
      </div>

      <span class="article-top-number">01 / 01</span>
    </header>

    <section class="article-hero">
      <div class="article-hero-copy">
        <div class="article-label">
          <span>Mindful code</span>
          <i></i>
          <span>3 min read</span>
        </div>

        <h1>
          Finding the
          <span>Base Condition.</span>
        </h1>

        <p>
          When life keeps repeating the same pattern, maybe you do not need
          another iteration. Maybe you need to know when to return.
        </p>
      </div>

      <div class="article-hero-art">
        <div class="recursive-ring ring-one"></div>
        <div class="recursive-ring ring-two"></div>
        <div class="recursive-ring ring-three"></div>

        <div class="recursive-center">
          <span>if</span>
          <strong>enough</strong>
          <small>return;</small>
        </div>

        <span class="article-spark article-spark-one">✦</span>
        <span class="article-spark article-spark-two">✿</span>
      </div>
    </section>

    <div class="article-content">
      <p class="article-lead">
        Recursion is beautiful because a function can solve something by
        calling itself. But without a base condition, it never knows when to
        stop.
      </p>

      <p>
        Some parts of life feel the same. The same routine, thought or
        situation returns, and we enter it with the same response.
      </p>

      <div class="code-thought">
        <div class="code-thought-header">
          <span></span>
          <span></span>
          <span></span>
          <small>life.js</small>
        </div>

        <code>
          <span>function repeat(pattern) {</span>
          <span>&nbsp;&nbsp;if (pattern.isDraining) return;</span>
          <span>&nbsp;&nbsp;return repeat(pattern);</span>
          <span>}</span>
        </code>
      </div>

      <h2>Your exit can be simple.</h2>

      <p>
        A base condition in life may be a boundary, an honest conversation, a
        change in routine or finally accepting that something is no longer
        working.
      </p>

      <aside class="article-highlight">
        <span>✿</span>

        <p>
          Ask yourself: “What needs to become true for me to stop repeating
          this?”
        </p>
      </aside>

      <h2>But some loops are worth keeping.</h2>

      <p>
        Repeating is not always bad. Practice, care, learning and meaningful
        habits can add something with every iteration.
      </p>

      <div class="loop-choice">
        <div class="choice-card value-card">
          <span class="choice-icon">🌱</span>

          <div>
            <small>Continue</small>
            <h3>When it adds value</h3>
            <p>More clarity, skill, peace or connection.</p>
          </div>
        </div>

        <div class="choice-card drain-card">
          <span class="choice-icon">🍂</span>

          <div>
            <small>Return</small>
            <h3>When it drains you</h3>
            <p>Less energy, confidence, patience or joy.</p>
          </div>
        </div>
      </div>

      <div class="article-question">
        <span>Before the next call...</span>

        <h2>
          Is this loop growing you,
          or only repeating you?
        </h2>
      </div>

      <p>
        Keep the recursions that help you become more. For the ones slowly
        burning you out, define the base condition and allow yourself to exit.
      </p>

      <div class="article-ending">
        <span class="ending-symbol">↻</span>

        <p>
          You do not need to debug your whole life today.
        </p>

        <strong>
          Just notice the loop you are currently inside.
        </strong>
      </div>

      <div class="article-actions">
        <button type="button" @click="$emit('back')">
          <span>←</span>
          Discover more thoughts
        </button>

        <span>Thanks for reading ✿</span>
      </div>
    </div>
  </article>
</template>
