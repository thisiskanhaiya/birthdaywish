<script setup>
import { nextTick, onBeforeUnmount, onMounted, ref } from "vue";
import Recursion from "./blogs/Recursion.vue";

const activeBlog = ref(null);
const mobileMenuOpen = ref(false);
let revealObserver;

const blogs = [
  {
    id: "recursion",
    number: "01",
    title: "Finding the Base Condition",
    excerpt:
      "Some life patterns keep calling themselves. Maybe the answer is not another attempt, but knowing when to return.",
    category: "Mindful Code",
    readTime: "3 min",
    icon: "↻",
    gradient: "gradient-purple",
    component: Recursion,
  },
];

const upcomingBlogs = [
  {
    id: "timeout",
    number: "02",
    title: "Not Everything Deserves Infinite Waiting",
    category: "Coming soon",
    icon: "⏳",
    gradient: "gradient-sunset",
  },
  {
    id: "exceptions",
    number: "03",
    title: "Life Does Not Always Follow the Happy Path",
    category: "Coming soon",
    icon: "✦",
    gradient: "gradient-blue",
  },
  {
    id: "commits",
    number: "04",
    title: "Commit the Change",
    category: "Coming soon",
    icon: "✓",
    gradient: "gradient-green",
  },
];

const setupRevealObserver = () => {
  revealObserver?.disconnect();

  revealObserver = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("is-visible");
          revealObserver.unobserve(entry.target);
        }
      });
    },
    {
      threshold: 0.12,
      rootMargin: "0px 0px -35px 0px",
    }
  );

  document.querySelectorAll(".reveal:not(.is-visible)").forEach((element) => {
    revealObserver.observe(element);
  });
};

const refreshReveal = async () => {
  await nextTick();
  setupRevealObserver();
};

const openBlog = async (blogId) => {
  activeBlog.value = blogs.find((blog) => blog.id === blogId) || null;
  mobileMenuOpen.value = false;

  window.scrollTo({
    top: 0,
    behavior: "smooth",
  });

  await refreshReveal();
};

const goHome = async () => {
  activeBlog.value = null;
  mobileMenuOpen.value = false;

  window.scrollTo({
    top: 0,
    behavior: "smooth",
  });

  await refreshReveal();
};

const scrollToStories = async () => {
  mobileMenuOpen.value = false;

  if (activeBlog.value) {
    activeBlog.value = null;
    await nextTick();
  }

  document.querySelector("#stories")?.scrollIntoView({
    behavior: "smooth",
  });
};

const scrollToAbout = async () => {
  mobileMenuOpen.value = false;

  if (activeBlog.value) {
    activeBlog.value = null;
    await nextTick();
  }

  document.querySelector("#about")?.scrollIntoView({
    behavior: "smooth",
  });
};

onMounted(setupRevealObserver);

onBeforeUnmount(() => {
  revealObserver?.disconnect();
});
</script>

<template>
  <div class="site-shell">
    <div class="ambient-background" aria-hidden="true">
      <div class="ambient-blob blob-one"></div>
      <div class="ambient-blob blob-two"></div>
      <div class="ambient-blob blob-three"></div>
      <div class="noise-layer"></div>
    </div>

    <!-- Navigation -->
    <nav class="site-nav">
      <div class="nav-inner">
        <button class="brand" type="button" @click="goHome">
          <span class="brand-symbol">l</span>

          <span class="brand-copy">
            <strong>little.log</strong>
            <small>life between the lines</small>
          </span>
        </button>

        <div class="desktop-navigation">
          <button type="button" @click="goHome">Home</button>
          <button type="button" @click="scrollToStories">Explore</button>
          <button type="button" @click="scrollToAbout">Our idea</button>
        </div>

        <button
          class="mobile-menu-button"
          type="button"
          :aria-expanded="mobileMenuOpen"
          aria-label="Open navigation"
          @click="mobileMenuOpen = !mobileMenuOpen"
        >
          <span :class="{ active: mobileMenuOpen }"></span>
          <span :class="{ active: mobileMenuOpen }"></span>
        </button>
      </div>

      <Transition name="menu">
        <div v-if="mobileMenuOpen" class="mobile-navigation">
          <button type="button" @click="goHome">Home</button>
          <button type="button" @click="scrollToStories">Explore stories</button>
          <button type="button" @click="scrollToAbout">Our idea</button>
        </div>
      </Transition>
    </nav>

    <!-- Landing page -->
    <main v-if="!activeBlog">
      <section class="hero-section">
        <div class="hero-grid">
          <div class="hero-copy reveal is-visible">
            <div class="hero-badge">
              <span class="badge-dot"></span>
              For people who think in code and feel in stories
            </div>

            <h1>
              Tiny tech ideas.
              <span>Very human stories.</span>
            </h1>

            <p>
              A colourful reading space where loops, errors, commits and
              timeouts become small reflections about everyday life.
            </p>

            <div class="hero-actions">
              <button class="primary-button" type="button" @click="scrollToStories">
                Start reading
                <span>↘</span>
              </button>

              <div class="reader-note">
                <div class="reader-faces">
                  <span>☻</span>
                  <span>✦</span>
                  <span>♡</span>
                </div>

                <small>Short reads for thoughtful breaks</small>
              </div>
            </div>
          </div>

          <div class="hero-visual reveal is-visible">
            <div class="visual-orbit orbit-one"></div>
            <div class="visual-orbit orbit-two"></div>

            <div class="floating-card mini-card mini-card-one">
              <span>if</span>
              <p>life !== expected</p>
            </div>

            <div class="floating-card main-visual-card">
              <div class="visual-window">
                <span></span>
                <span></span>
                <span></span>
              </div>

              <div class="visual-code">
                <span class="code-line code-pink">while (growing) {</span>
                <span class="code-line code-purple"> &nbsp;learn();</span>
                <span class="code-line code-blue"> &nbsp;pause();</span>
                <span class="code-line code-orange"> &nbsp;beginAgain();</span>
                <span class="code-line code-pink">}</span>
              </div>

              <div class="visual-message">
                <span>✿</span>
                <p>There is a little life inside every line.</p>
              </div>
            </div>

            <div class="floating-card mini-card mini-card-two">
              <span>404</span>
              <p>clarity not found</p>
            </div>

            <span class="floating-spark spark-one">✦</span>
            <span class="floating-spark spark-two">✿</span>
          </div>
        </div>

        <button class="hero-scroll" type="button" @click="scrollToStories">
          <span>Scroll to explore</span>
          <i>↓</i>
        </button>
      </section>

      <!-- Categories -->
      <section class="category-strip reveal">
        <div class="category-track">
          <span>TECH × LIFE</span>
          <i>✦</i>
          <span>SMALL THOUGHTS</span>
          <i>✿</i>
          <span>MINDFUL CODE</span>
          <i>♡</i>
          <span>QUICK READS</span>
          <i>✦</i>
        </div>
      </section>

      <!-- Blog grid -->
      <section id="stories" class="stories-section">
        <div class="section-header reveal">
          <div>
            <span class="eyebrow">Fresh from little.log</span>
            <h2>Pick a thought.</h2>
            <p>
              Compact stories made for a tea break, commute or quiet moment.
            </p>
          </div>

          <div class="story-total">
            <strong>01</strong>
            <span>published story</span>
          </div>
        </div>

        <div class="blog-grid">
          <!-- Published blogs -->
          <article
            v-for="blog in blogs"
            :key="blog.id"
            class="blog-card published-card reveal"
            tabindex="0"
            @click="openBlog(blog.id)"
            @keydown.enter="openBlog(blog.id)"
          >
            <div class="card-cover" :class="blog.gradient">
              <div class="cover-grid"></div>

              <span class="card-number">{{ blog.number }}</span>
              <span class="cover-icon">{{ blog.icon }}</span>

              <div class="cover-code">
                <span>function life() {</span>
                <span>&nbsp;&nbsp;return perspective;</span>
                <span>}</span>
              </div>

              <span class="cover-pill">New thought</span>
            </div>

            <div class="card-copy">
              <div class="card-meta">
                <span>{{ blog.category }}</span>
                <span>{{ blog.readTime }} read</span>
              </div>

              <h3>{{ blog.title }}</h3>
              <p>{{ blog.excerpt }}</p>

              <button type="button" @click.stop="openBlog(blog.id)">
                Read story
                <span>→</span>
              </button>
            </div>
          </article>

          <!-- Future preview cards -->
          <article
            v-for="blog in upcomingBlogs"
            :key="blog.id"
            class="blog-card upcoming-card reveal"
          >
            <div class="upcoming-cover" :class="blog.gradient">
              <span class="card-number">{{ blog.number }}</span>
              <span class="upcoming-icon">{{ blog.icon }}</span>

              <div class="coming-chip">
                Coming soon
              </div>
            </div>

            <div class="upcoming-copy">
              <span>{{ blog.category }}</span>
              <h3>{{ blog.title }}</h3>
            </div>
          </article>
        </div>
      </section>

      <!-- About -->
      <section id="about" class="about-section reveal">
        <div class="about-art">
          <div class="about-card about-card-one">
            <span>&lt;/&gt;</span>
          </div>

          <div class="about-card about-card-two">
            <span>♡</span>
          </div>

          <div class="about-connector"></div>
        </div>

        <div class="about-copy">
          <span class="eyebrow">The idea behind it</span>

          <h2>
            Somewhere between
            <span>logic and living.</span>
          </h2>

          <p>
            We spend a lot of time debugging systems. Eventually, code starts
            explaining our habits, choices and emotions too.
          </p>

          <p>
            Little.log keeps those observations short, relatable and easy to
            carry into the rest of your day.
          </p>
        </div>
      </section>

      <footer class="site-footer reveal">
        <div>
          <strong>little.log</strong>
          <span>Thoughts worth saving.</span>
        </div>

        <p>
          Built between <code>console.log()</code> and overthinking.
        </p>

        <button type="button" @click="scrollToStories">
          Read something
          <span>↑</span>
        </button>
      </footer>
    </main>

    <!-- Dynamically selected blog -->
    <main v-else>
      <component :is="activeBlog.component" @back="goHome" />
    </main>
  </div>
</template>
