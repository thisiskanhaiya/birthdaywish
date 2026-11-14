<script setup>
import { ref } from "vue";
import Recursion from "./blogs/Recursion.vue";

const activeBlog = ref(null);

const openBlog = (blog) => {
  activeBlog.value = blog;
  window.scrollTo({ top: 0, behavior: "smooth" });
};

const goHome = () => {
  activeBlog.value = null;
  window.scrollTo({ top: 0, behavior: "smooth" });
};
</script>

<template>
  <div class="app-shell">

    <!-- ================= NAVBAR ================= -->
    <nav class="navbar">
      <div class="nav-container">

        <button class="logo" @click="goHome">
          <span class="logo-mark">✿</span>

          <span>
            <strong>little.log</strong>
            <small>thoughts between the lines</small>
          </span>
        </button>

        <div class="nav-links">
          <button @click="goHome">Home</button>
          <a href="#stories" @click="goHome">Stories</a>
          <a href="#about" @click="goHome">About</a>
        </div>

      </div>
    </nav>


    <!-- ================= LANDING PAGE ================= -->
    <main v-if="!activeBlog">

      <!-- HERO -->
      <section class="landing-hero">

        <div class="hero-decoration hero-flower">✿</div>
        <div class="hero-decoration hero-star">✦</div>
        <div class="hero-decoration hero-dot"></div>

        <div class="hero-content">

          <span class="hero-kicker">
            ☕ A tiny corner of the internet
          </span>

          <h1>
            Code has bugs.<br />
            <span>Life has patterns.</span>
          </h1>

          <p>
            A cozy place for techies who sometimes find pieces of life
            hiding inside code, algorithms, errors and everyday technical
            things.
          </p>

          <a href="#stories" class="hero-button">
            Read something cute
            <span>↓</span>
          </a>

        </div>

        <div class="hero-side-note">
          <span>01</span>
          <p>story<br />published</p>
        </div>

      </section>


      <!-- SMALL MANIFESTO -->
      <section class="manifesto-section">

        <div class="manifesto-line"></div>

        <p>
          Not tutorials. Not documentation.
          <strong>Just little thoughts where technology meets life.</strong>
        </p>

        <div class="manifesto-line"></div>

      </section>


      <!-- STORIES -->
      <section id="stories" class="stories-section">

        <div class="section-heading">

          <div>
            <span class="section-label">Fresh from the notebook</span>
            <h2>Latest little thoughts.</h2>
          </div>

          <span class="story-count">
            01 STORY
          </span>

        </div>


        <!-- RECURSION BLOG -->
        <article
          class="featured-story"
          @click="openBlog('recursion')"
        >

          <div class="story-art">

            <div class="paper-card paper-back"></div>

            <div class="paper-card paper-front">

              <span class="paper-small-text">
                while (life)
              </span>

              <div class="paper-loop">
                <span>↻</span>
              </div>

              <p>
                where is my<br />
                <strong>base condition?</strong>
              </p>

              <span class="paper-number">01 / thoughts</span>

            </div>

            <span class="art-flower">✿</span>

          </div>


          <div class="story-details">

            <div class="story-meta">
              <span class="story-category">
                TECH × LIFE
              </span>

              <span>5 min read</span>
            </div>

            <h3>
              Finding the<br />
              Base Condition
            </h3>

            <p class="story-description">
              Sometimes life feels suspiciously like recursion. The same
              mornings, the same thoughts, the same situations calling
              themselves again and again.
            </p>

            <p class="story-preview">
              Maybe being stuck isn't always about trying harder.
              Maybe we simply haven't defined when to return.
            </p>

            <button
              class="story-read"
              @click.stop="openBlog('recursion')"
            >
              Read the thought
              <span>→</span>
            </button>

          </div>

        </article>


        <!-- FUTURE STORIES -->
        <div class="future-note">

          <div class="future-icon">
            ♡
          </div>

          <div>
            <span>More thoughts are brewing</span>

            <p>
              Exceptions, commits, loops, timeouts and all the strange
              places where code starts sounding a little like life.
            </p>
          </div>

        </div>

      </section>


      <!-- ABOUT -->
      <section id="about" class="about-section">

        <div class="about-symbol">
          &lt;/&gt;
        </div>

        <div class="about-content">

          <span class="section-label">
            Why this little place exists
          </span>

          <h2>
            Sometimes code explains<br />
            more than computers.
          </h2>

          <p>
            We spend so much time debugging systems that eventually
            we start noticing the same ideas outside the screen.
          </p>

          <p>
            This is simply a collection of those tiny observations.
            Nothing too serious. Just technology, life and thoughts
            worth keeping somewhere.
          </p>

        </div>

      </section>


      <!-- FOOTER -->
      <footer class="site-footer">

        <div class="footer-brand">
          <span>✿</span>
          <strong>little.log</strong>
        </div>

        <p>
          built somewhere between
          <code>console.log()</code>
          and overthinking.
        </p>

        <span class="footer-heart">
          ♡
        </span>

      </footer>

    </main>


    <!-- ================= BLOG RENDERING ================= -->
    <main v-else>

      <Recursion
        v-if="activeBlog === 'recursion'"
        @back="goHome"
      />

    </main>

  </div>
</template>
