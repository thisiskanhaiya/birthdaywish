<script setup>
import { computed, ref } from "vue";
   
import Sadhana from "./blogs/Sadhana.vue";
import Focus from "./blogs/Focus.vue";
import Recursion from "./blogs/Recursion.vue";
import Pause from "./blogs/Pause.vue";  

const activeBlog = ref(null);
const category = ref("All");

/*
|--------------------------------------------------------------------------
| BLOG REGISTRY
|--------------------------------------------------------------------------
|
| IMPORTANT:
| Always add the NEWEST blog at the TOP.
|
| First blog = Today's Pick automatically.
| Remaining blogs = Explore/category library automatically.
|
*/

const blogs = [
   {
    id: "sadhana",
    title: "Someone Should Build This in India",
    shortTitle: "Someone Should Build This in India",
    description:
      "We are learning to control almost everything around us. Except ourselves.",
    category: "Life",
    readTime: "5 min",
    component: Sadhana,
    art: "sadhana",
  },
   {
    id: "pause",
    title: "The Quiet Advantage of Not Rushing Everything",
    shortTitle: "The Quiet Advantage of Not Rushing",
    description:
      "Some of the best decisions happen in the pause before you reply.",
    category: "Life",
    readTime: "3 min",
    component: Pause,
    art: "pause",
    date: "16 Nov 2026",
  },
  {
    id: "focus",
    title: "Don’t Rush. Focus on One Thing at a Time.",
    shortTitle: "Don’t Rush. Focus.",
    description: "Being busy doesn’t always mean being productive.",
    category: "Growth",
    readTime: "3 min",
    component: Focus,
    art: "focus",
    date: "15 Nov 2026",
  },

  {
    id: "recursion",
    title: "Finding the Base Condition",
    shortTitle: "Finding the Base Condition",
    description: "Sometimes you just need to return.",
    category: "Life",
    readTime: "3 min",
    component: Recursion,
    art: "recursion",
    date: "14 Nov 2026",
  },
];

const categories = [
  {
    name: "All",
    icon: "✦",
  },
  {
    name: "Life",
    icon: "☕",
  },
  {
    name: "Tech",
    icon: "⌨",
  },
  {
    name: "Growth",
    icon: "🌱",
  },
  {
    name: "Mindset",
    icon: "♡",
  },
];

/*
|--------------------------------------------------------------------------
| AUTOMATIC TODAY'S PICK
|--------------------------------------------------------------------------
*/

const featuredBlog = computed(() => blogs[0]);

/*
|--------------------------------------------------------------------------
| AUTOMATIC EXPLORE LIBRARY
|--------------------------------------------------------------------------
|
| Today's Pick is removed from Explore.
| Once a newer blog is added, the current featured blog automatically
| comes back into Explore.
|
*/

const archiveBlogs = computed(() => {
  return blogs.slice(1);
});

/*
|--------------------------------------------------------------------------
| CATEGORY FILTERING
|--------------------------------------------------------------------------
*/

const filteredBlogs = computed(() => {
  if (category.value === "All") {
    return archiveBlogs.value;
  }

  return archiveBlogs.value.filter(
    (blog) => blog.category === category.value
  );
});

/*
|--------------------------------------------------------------------------
| CATEGORY COUNTS
|--------------------------------------------------------------------------
*/

const categoryCount = (categoryName) => {
  if (categoryName === "All") {
    return archiveBlogs.value.length;
  }

  return archiveBlogs.value.filter(
    (blog) => blog.category === categoryName
  ).length;
};

/*
|--------------------------------------------------------------------------
| NAVIGATION
|--------------------------------------------------------------------------
*/

function openBlog(blog) {
  activeBlog.value = blog;

  window.scrollTo({
    top: 0,
    behavior: "smooth",
  });
}

function goHome() {
  activeBlog.value = null;

  window.scrollTo({
    top: 0,
    behavior: "smooth",
  });
}

function explore() {
  document.querySelector("#explore")?.scrollIntoView({
    behavior: "smooth",
  });
}

function selectCategory(item) {
  category.value = item;
  explore();
}
</script>

<template>
  <div class="little-app">

    <!-- ======================================================
         HOME
    ======================================================= -->

    <template v-if="!activeBlog">

      <!-- NAV -->

      <header class="topbar">

        <button
          class="logo"
          type="button"
          @click="goHome"
        >
          little.log
          <span>♡</span>
        </button>


        <div class="top-actions">

          <button
            type="button"
            aria-label="Explore"
            @click="explore"
          >
            ⌕
          </button>

          <button
            type="button"
            aria-label="Menu"
          >
            ☰
          </button>

        </div>

      </header>


      <main>

        <!-- ==================================================
             HERO
        =================================================== -->

        <section class="hero">

          <div class="hero-text">

            <span class="micro-title">
              TECH THOUGHTS · REAL FEELINGS
            </span>

            <h1>
              Same scroll.

              <em>
                New perspective.
              </em>
            </h1>

            <p>
              Small relatable reads for builders,
              overthinkers, dreamers and people who
              occasionally find life inside code.
            </p>

            <button
              class="primary-btn"
              @click="explore"
            >
              Explore blogs
              <span>→</span>
            </button>

          </div>


          <!-- CSS STICKER -->

          <div class="desk-sticker">

            <div class="pastel-blob"></div>

            <span class="spark spark-a">
              ✦
            </span>

            <span class="spark spark-b">
              ♡
            </span>


            <!-- NOTE -->

            <div class="hero-note">

              <span>♡</span>

              It's not<br />
              just code,<br />

              <strong>
                it's life too.
              </strong>

            </div>


            <!-- PLANT -->

            <div class="plant">

              <div class="leaf leaf-left"></div>
              <div class="leaf leaf-right"></div>

              <div class="stem"></div>
              <div class="pot"></div>

            </div>


            <!-- CHARACTER -->

            <div class="character">

              <div class="hair-back"></div>

              <div class="head">

                <div class="fringe fringe-left"></div>
                <div class="fringe fringe-right"></div>

                <span class="character-eye eye-left"></span>
                <span class="character-eye eye-right"></span>

                <span class="blush blush-left"></span>
                <span class="blush blush-right"></span>

                <span class="character-mouth"></span>

              </div>

              <div class="bun"></div>

              <div class="body"></div>

              <div class="arm arm-left"></div>
              <div class="arm arm-right"></div>

            </div>


            <!-- LAPTOP -->

            <div class="cute-laptop">
              <span class="laptop-heart">
                ♡
              </span>
            </div>


            <!-- CAT -->

            <div class="cat">

              <span class="cat-ear ear-one"></span>
              <span class="cat-ear ear-two"></span>

              <span class="cat-head"></span>
              <span class="cat-body"></span>
              <span class="cat-tail"></span>

            </div>

          </div>

        </section>


        <!-- ==================================================
             QUICK CATEGORIES
        =================================================== -->

        <section class="quick-categories">

          <button
            v-for="item in categories.slice(1)"
            :key="item.name"
            type="button"
            @click="selectCategory(item.name)"
          >

            <span
              class="circle"
              :class="item.name.toLowerCase()"
            >
              {{ item.icon }}
            </span>

            {{ item.name }}

          </button>

        </section>


        <!-- ==================================================
             TODAY'S PICK
        =================================================== -->

        <section class="today">

          <div class="section-head">

            <div>

              <span>
                TODAY'S PICK
              </span>

              <h2>
                A little thought
                <b>✦</b>
              </h2>

            </div>


            <small>
              newest thought ↘
            </small>

          </div>


          <article
            class="featured"
            @click="openBlog(featuredBlog)"
          >

            <!-- Dynamic artwork -->

            <div
              class="featured-dynamic-art"
              :class="`featured-${featuredBlog.art}`"
            >

              <!-- FOCUS -->

              <template v-if="featuredBlog.art === 'focus'">

                <span class="featured-focus-spark focus-art-one">
                  ✦
                </span>

                <span class="featured-focus-spark focus-art-two">
                  ♡
                </span>


                <div class="focus-board">

                  <span class="board-tape"></span>

                  <small>
                    THIS WEEK
                  </small>

                  <div class="board-task completed">
                    <span>✓</span>
                    Learn
                  </div>

                  <div class="board-task active">
                    <span>02</span>
                    Practise
                  </div>

                  <div class="board-task">
                    <span>03</span>
                    Improve
                  </div>

                </div>


                <div class="focus-timer">

                  <div class="timer-ring">

                    <span>45</span>

                    <small>
                      MIN
                    </small>

                  </div>

                </div>


                <div class="featured-focus-note">
                  one thing<br />
                  at a time ♡
                </div>

              </template>


              <!-- RECURSION -->

              <template v-if="featuredBlog.art === 'recursion'">

                <div class="sky-sun"></div>

                <div class="mountain back-one"></div>
                <div class="mountain back-two"></div>

                <div class="hill hill-one"></div>
                <div class="hill hill-two"></div>

                <div class="path"></div>

                <div class="sign">

                  <span class="sign-top">
                    continue →
                  </span>

                  <span class="sign-bottom">
                    ← return
                  </span>

                  <i></i>

                </div>

              </template>

            </div>


            <!-- COPY -->

            <div class="featured-copy">

              <span
                class="tag"
                :class="`tag-${featuredBlog.category.toLowerCase()}`"
              >
                {{ featuredBlog.category }}
              </span>


              <h3>
                {{ featuredBlog.shortTitle }}
              </h3>


              <p>
                {{ featuredBlog.description }}
              </p>


              <div class="featured-bottom">

                <small>
                  {{ featuredBlog.readTime }} read
                </small>

                <button
                  type="button"
                  @click.stop="openBlog(featuredBlog)"
                >
                  Read →
                </button>

              </div>

            </div>

          </article>

        </section>


        <!-- ==================================================
             REMINDER
        =================================================== -->

        <section class="reminder">

          <span class="tape"></span>

          <small>
            DAILY REMINDER
          </small>

          <p>
            “You don't have to do everything today.<br />
            Just move something meaningful forward.”
          </p>

          <span class="reminder-heart">
            ♡
          </span>

        </section>


        <!-- ==================================================
             EXPLORE
        =================================================== -->

        <section
          id="explore"
          class="explore"
        >

          <div class="section-head">

            <div>

              <span>
                LITTLE THOUGHTS
              </span>

              <h2>
                Explore
              </h2>

            </div>


            <small>
              different lens ♡
            </small>

          </div>


          <!-- CATEGORY PILLS -->

          <div class="category-tabs">

            <button
              v-for="item in categories"
              :key="item.name"
              type="button"
              :class="{
                active: category === item.name
              }"
              @click="category = item.name"
            >

              {{ item.name }}

              <span
                v-if="categoryCount(item.name)"
                class="category-count"
              >
                {{ categoryCount(item.name) }}
              </span>

            </button>

          </div>


          <!-- RESULTS -->

          <div
            v-if="filteredBlogs.length"
            class="thought-list"
          >

            <article
              v-for="blog in filteredBlogs"
              :key="blog.id"
              class="thought-card"
              @click="openBlog(blog)"
            >

              <!-- ART -->

              <div
                class="thought-art"
                :class="`${blog.art}-mini`"
              >

                <!-- RECURSION -->

                <template v-if="blog.art === 'recursion'">

                  <div class="mini-sun"></div>

                  <div class="mini-mountain one"></div>
                  <div class="mini-mountain two"></div>

                  <div class="mini-sign">

                    <span>
                      continue →
                    </span>

                    <span>
                      ← return
                    </span>

                    <i></i>

                  </div>

                </template>


                <!-- FOCUS -->

                <template v-if="blog.art === 'focus'">

                  <div class="mini-focus-ring">
                    <span>01</span>
                  </div>

                  <div class="mini-focus-list">
                    <span>✓ learn</span>
                    <span>✓ practise</span>
                    <span>• improve</span>
                  </div>

                </template>

              </div>


              <!-- COPY -->

              <div class="thought-content">

                <span
                  class="tag"
                  :class="`tag-${blog.category.toLowerCase()}`"
                >
                  {{ blog.category }}
                </span>


                <h3>
                  {{ blog.shortTitle }}
                </h3>


                <p>
                  {{ blog.description }}
                </p>


                <footer>

                  <small>
                    {{ blog.readTime }} read
                  </small>

                  <span>
                    ♡
                  </span>

                </footer>

              </div>

            </article>

          </div>


          <!-- EMPTY CATEGORY -->

          <div
            v-else
            class="empty-category"
          >

            <span>
              ✿
            </span>

            <strong>
              Nothing here yet.
            </strong>

            <p>
              A little {{ category.toLowerCase() }}
              thought will appear here soon.
            </p>

          </div>

        </section>


        <!-- PAPER NOTE -->

        <section class="paper-note">

          <span class="paperclip">
            ♡
          </span>

          <p>
            good blogs<br />
            brighter days.
          </p>

        </section>

      </main>


      <!-- MOBILE NAV -->

      <nav class="mobile-tabs">

        <button
          class="active"
          @click="goHome"
        >
          <span>⌂</span>
          Home
        </button>

        <button @click="explore">
          <span>⌕</span>
          Explore
        </button>

        <button>
          <span>♡</span>
          Saved
        </button>

        <button>
          <span>☺</span>
          Profile
        </button>

      </nav>

    </template>


    <!-- ======================================================
         DYNAMIC BLOG
    ======================================================= -->

    <component
      v-else
      :is="activeBlog.component"
      @back="goHome"
    />

  </div>
</template>
