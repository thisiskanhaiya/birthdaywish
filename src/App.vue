<script setup>
import { computed, ref } from "vue";
import Recursion from "./blogs/Recursion.vue";

import homeGirl from "./assets/home-girl.png";
import recursionCard from "./assets/recursion-card.png";

const activeBlog = ref(null);
const activeCategory = ref("All");
const mobileMenuOpen = ref(false);

const categories = [
  { name: "All", icon: "✦" },
  { name: "Life", icon: "☕" },
  { name: "Tech", icon: "⌨" },
  { name: "Growth", icon: "🌱" },
  { name: "Mindset", icon: "♡" },
];

const blogs = [
  {
    id: "recursion",
    title: "Finding the Base Condition",
    description: "Sometimes you just need to return.",
    category: "Life",
    readTime: "3 min",
    image: recursionCard,
    component: Recursion,
  },
];

const upcomingBlogs = [
  {
    id: "waiting",
    title: "Not Everything Deserves Infinite Waiting",
    description: "Some responses are timeouts for a reason.",
    category: "Mindset",
    readTime: "3 min",
    artwork: "waiting",
  },
  {
    id: "happy-path",
    title: "Life Doesn't Always Follow the Happy Path",
    description: "Errors are part of the process.",
    category: "Growth",
    readTime: "4 min",
    artwork: "error",
  },
  {
    id: "commit",
    title: "Commit the Change",
    description: "A new version of you is always possible.",
    category: "Life",
    readTime: "3 min",
    artwork: "commit",
  },
];

const filteredBlogs = computed(() => {
  if (activeCategory.value === "All") {
    return blogs;
  }

  return blogs.filter(
    (blog) => blog.category === activeCategory.value
  );
});

function openBlog(blog) {
  activeBlog.value = blog;
  mobileMenuOpen.value = false;

  window.scrollTo({
    top: 0,
    behavior: "smooth",
  });
}

function goHome() {
  activeBlog.value = null;
  mobileMenuOpen.value = false;

  window.scrollTo({
    top: 0,
    behavior: "smooth",
  });
}

function scrollToExplore() {
  mobileMenuOpen.value = false;

  document.querySelector("#explore")?.scrollIntoView({
    behavior: "smooth",
  });
}

function chooseCategory(category) {
  activeCategory.value = category;
  scrollToExplore();
}
</script>

<template>
  <div class="app-shell">
    <!-- TOP NAVIGATION -->
    <header class="top-navigation">
      <div class="navigation-inner">
        <button class="site-logo" type="button" @click="goHome">
          little.log <span>♡</span>
        </button>

        <div v-if="!activeBlog" class="navigation-actions">
          <button
            class="navigation-icon"
            type="button"
            aria-label="Explore blogs"
            @click="scrollToExplore"
          >
            <svg
              viewBox="0 0 24 24"
              aria-hidden="true"
            >
              <circle cx="11" cy="11" r="6"></circle>
              <path d="m16 16 4 4"></path>
            </svg>
          </button>

          <button
            class="navigation-icon menu-button"
            type="button"
            aria-label="Open menu"
            @click="mobileMenuOpen = !mobileMenuOpen"
          >
            <span></span>
            <span></span>
            <span></span>
          </button>
        </div>
      </div>

      <Transition name="menu">
        <div v-if="mobileMenuOpen" class="navigation-menu">
          <button type="button" @click="goHome">
            Home
          </button>

          <button type="button" @click="scrollToExplore">
            Explore thoughts
          </button>

          <button type="button">
            Saved thoughts
          </button>
        </div>
      </Transition>
    </header>

    <!-- HOME PAGE -->
    <main v-if="!activeBlog" class="home-page">
      <!-- HERO -->
      <section class="home-hero">
        <div class="hero-copy">
          <span class="eyebrow">
            TECH THOUGHTS · REAL FEELINGS
          </span>

          <h1>
            Same scroll.
            <span>New perspective.</span>
          </h1>

          <p>
            Small relatable reads for builders, overthinkers,
            dreamers and people who occasionally find life
            inside code.
          </p>

          <button
            class="dark-button"
            type="button"
            @click="scrollToExplore"
          >
            Explore blogs
            <span>→</span>
          </button>
        </div>

        <div class="hero-image-area">
          <span class="hero-pastel-circle circle-one"></span>
          <span class="hero-pastel-circle circle-two"></span>

          <img
            class="home-girl-image"
            :src="homeGirl"
            alt="Little.log reader behind a laptop"
          />

          <div class="yellow-sticky-note">
            <span class="sticky-heart">♡</span>

            It's not<br />
            just code,<br />
            <strong>it's life too.</strong>
          </div>

          <span class="hero-doodle doodle-one">⌁</span>
          <span class="hero-doodle doodle-two">✦</span>
        </div>
      </section>

      <!-- CATEGORY ICONS -->
      <section class="category-icons">
        <button
          v-for="category in categories.slice(1)"
          :key="category.name"
          class="category-icon-button"
          type="button"
          @click="chooseCategory(category.name)"
        >
          <span
            class="category-icon-circle"
            :class="`category-${category.name.toLowerCase()}`"
          >
            {{ category.icon }}
          </span>

          <span>{{ category.name }}</span>
        </button>
      </section>

      <!-- TODAY'S PICK -->
      <section class="today-section">
        <div class="section-heading">
          <div>
            <span class="section-label">START HERE</span>

            <h2>
              Today’s Pick
              <span class="sparkle">✦</span>
            </h2>
          </div>

          <span class="handwritten-note">
            short &amp; sweet
          </span>
        </div>

        <article
          class="featured-card"
          tabindex="0"
          @click="openBlog(blogs[0])"
          @keydown.enter="openBlog(blogs[0])"
        >
          <div class="featured-image">
            <img
              :src="recursionCard"
              alt="A road with continue and return signs"
            />
          </div>

          <div class="featured-copy">
            <span class="pink-pill">Life × Tech</span>

            <h3>Finding the Base Condition</h3>

            <p>
              Sometimes you just need to return.
            </p>

            <div class="featured-footer">
              <span>3 min read</span>

              <button
                type="button"
                @click.stop="openBlog(blogs[0])"
              >
                Read
                <span>→</span>
              </button>
            </div>
          </div>
        </article>
      </section>

      <!-- DAILY REMINDER -->
      <section class="daily-reminder">
        <span class="reminder-tape"></span>

        <span class="reminder-label">
          DAILY REMINDER
        </span>

        <p>
          “Not every loop is a trap.<br />
          Some loops are how you grow.”
        </p>

        <span class="reminder-heart">♡</span>
      </section>

      <!-- EXPLORE -->
      <section id="explore" class="explore-section">
        <div class="explore-title">
          <div>
            <span class="section-label">
              LITTLE THOUGHTS
            </span>

            <h2>More Thoughts for You</h2>
          </div>

          <span class="see-all">see all →</span>
        </div>

        <div class="category-filter">
          <button
            v-for="category in categories"
            :key="category.name"
            type="button"
            :class="{ active: activeCategory === category.name }"
            @click="activeCategory = category.name"
          >
            {{ category.name }}
          </button>
        </div>

        <div class="thoughts-row">
          <article
            v-for="blog in filteredBlogs"
            :key="blog.id"
            class="thought-card available"
            @click="openBlog(blog)"
          >
            <div class="thought-image">
              <img :src="blog.image" :alt="blog.title" />

              <span class="status-pill">
                Read now
              </span>
            </div>

            <div class="thought-copy">
              <span>{{ blog.category }}</span>

              <h3>{{ blog.title }}</h3>

              <p>{{ blog.description }}</p>

              <footer>
                <small>{{ blog.readTime }} read</small>
                <span>♡</span>
              </footer>
            </div>
          </article>

          <article
            v-for="blog in upcomingBlogs"
            :key="blog.id"
            class="thought-card coming-soon"
          >
            <div
              class="thought-placeholder"
              :class="`placeholder-${blog.artwork}`"
            >
              <div
                v-if="blog.artwork === 'waiting'"
                class="hourglass-illustration"
              >
                <span class="hourglass-top"></span>
                <span class="hourglass-center"></span>
                <span class="hourglass-bottom"></span>
              </div>

              <div
                v-if="blog.artwork === 'error'"
                class="error-sign"
              >
                ERROR<br />
                ≠<br />
                END
              </div>

              <div
                v-if="blog.artwork === 'commit'"
                class="commit-art"
              >
                <span class="commit-head"></span>
                <span class="commit-body"></span>
                <span class="commit-bag"></span>
              </div>

              <span class="status-pill">
                Coming soon
              </span>
            </div>

            <div class="thought-copy">
              <span>{{ blog.category }}</span>

              <h3>{{ blog.title }}</h3>

              <p>{{ blog.description }}</p>

              <footer>
                <small>{{ blog.readTime }} read</small>
                <span>♡</span>
              </footer>
            </div>
          </article>
        </div>

        <p class="swipe-hint">
          Swipe to discover more
          <span>→</span>
        </p>
      </section>

      <!-- MOBILE BOTTOM NAVIGATION -->
      <nav class="bottom-navigation">
        <button class="active" type="button" @click="goHome">
          <span>⌂</span>
          Home
        </button>

        <button type="button" @click="scrollToExplore">
          <span>⌕</span>
          Explore
        </button>

        <button class="create-button" type="button">
          <span>＋</span>
        </button>

        <button type="button">
          <span>♡</span>
          Saved
        </button>

        <button type="button">
          <span>☺</span>
          Profile
        </button>
      </nav>
    </main>

    <!-- SELECTED BLOG -->
    <main v-else>
      <component
        :is="activeBlog.component"
        @back="goHome"
      />
    </main>
  </div>
</template>
