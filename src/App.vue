<script setup>
import { computed, ref } from "vue";
import Recursion from "./blogs/Recursion.vue";

const activeBlog = ref(null);
const activeCategory = ref("All");

const blogs = [
  {
    id: "recursion",
    title: "Finding the Base Condition",
    hook: "Sometimes you just need to return.",
    category: "Life",
    readTime: "3 min",
    color: "lilac",
    sticker: "↻",
    component: Recursion,
  },
];

// Add future blogs here only.
const comingSoon = [
  {
    id: "waiting",
    title: "Not Everything Deserves Infinite Waiting",
    hook: "Some responses are timeouts for a reason.",
    category: "Mindset",
    readTime: "3 min",
    color: "peach",
    sticker: "⌛",
  },
  {
    id: "happy-path",
    title: "Life Doesn't Always Follow the Happy Path",
    hook: "Errors are part of the process.",
    category: "Growth",
    readTime: "4 min",
    color: "mint",
    sticker: "✦",
  },
  {
    id: "commit",
    title: "Commit the Change",
    hook: "A new version of you is always possible.",
    category: "Life",
    readTime: "3 min",
    color: "sky",
    sticker: "✓",
  },
];

const categories = ["All", "Life", "Tech", "Growth", "Mindset"];

const filteredBlogs = computed(() => {
  if (activeCategory.value === "All") return blogs;

  return blogs.filter(
    (blog) => blog.category === activeCategory.value
  );
});

function selectBlog(blog) {
  activeBlog.value = blog;
  window.scrollTo({ top: 0 });
}

function goHome() {
  activeBlog.value = null;
  window.scrollTo({ top: 0 });
}

function scrollToExplore() {
  document
    .querySelector("#explore")
    ?.scrollIntoView({ behavior: "smooth" });
}
</script>

<template>
  <div class="site">

    <!-- =========================
         TOP NAV
    ========================== -->

    <header class="top-nav">
      <button class="logo" @click="goHome">
        little.log <span>♡</span>
      </button>

      <div class="nav-actions">
        <button
          v-if="!activeBlog"
          class="round-button"
          @click="scrollToExplore"
          aria-label="Explore"
        >
          ⌕
        </button>

        <button
          v-if="!activeBlog"
          class="round-button"
          aria-label="Menu"
        >
          ☰
        </button>
      </div>
    </header>


    <!-- =========================
         HOME
    ========================== -->

    <main v-if="!activeBlog">

      <!-- HERO -->

      <section class="cute-hero">

        <span class="doodle doodle-star">✦</span>
        <span class="doodle doodle-heart">♡</span>
        <span class="doodle doodle-flower">✿</span>

        <div class="hero-copy">

          <div class="tiny-label">
            TECH THOUGHTS · REAL FEELINGS
          </div>

          <h1>
            Same scroll.<br />
            <span>New perspective.</span>
          </h1>

          <p>
            Small relatable reads for builders,
            overthinkers, dreamers and people who
            occasionally find life inside code.
          </p>

          <button
            class="explore-button"
            @click="scrollToExplore"
          >
            Explore blogs
            <span>→</span>
          </button>

        </div>


        <!-- CHARACTER / STICKER ART -->

        <div class="hero-art">

          <div class="sun-blob"></div>

          <div class="laptop-sticker">

            <div class="person-head">
              <div class="hair hair-left"></div>
              <div class="hair hair-right"></div>

              <div class="face">
                <span class="eye">•</span>
                <span class="eye">•</span>
                <span class="smile">⌣</span>
              </div>

              <div class="bun"></div>
            </div>

            <div class="person-body">
              <div class="sleeve left-sleeve"></div>
              <div class="sleeve right-sleeve"></div>
            </div>

            <div class="laptop">
              <span class="laptop-heart">♡</span>

              <div class="laptop-text">
                good ideas<br />
                better days
              </div>

              <span class="tiny-flower">✿</span>
            </div>

          </div>


          <div class="sticky-note">
            <span>♡</span>

            It's not<br />
            just code.<br />
            <strong>it's life too.</strong>
          </div>

        </div>

      </section>


      <!-- CATEGORY BUBBLES -->

      <section class="category-bubbles">

        <button
          v-for="category in categories.slice(1)"
          :key="category"
          class="bubble-item"
          @click="
            activeCategory = category;
            scrollToExplore();
          "
        >
          <span
            class="bubble-icon"
            :class="`bubble-${category.toLowerCase()}`"
          >
            {{
              category === "Life"
                ? "☕"
                : category === "Tech"
                ? "⌨"
                : category === "Growth"
                ? "☘"
                : "♡"
            }}
          </span>

          {{ category }}
        </button>

      </section>


      <!-- TODAY PICK -->

      <section class="today-section">

        <div class="section-title-row">

          <div>
            <span class="section-mini">START HERE</span>

            <h2>
              Today's Pick
              <span>✦</span>
            </h2>
          </div>

          <span class="scribble">
            short & sweet
          </span>

        </div>


        <article
          class="today-card"
          @click="selectBlog(blogs[0])"
        >

          <!-- ART -->

          <div class="today-art">

            <span class="cloud cloud-one">☁</span>
            <span class="cloud cloud-two">☁</span>

            <div class="sun"></div>

            <div class="mountain mountain-back"></div>
            <div class="mountain mountain-front"></div>

            <div class="road"></div>

            <div class="sign-post">
              <div>continue →</div>
              <div>← return</div>
              <span></span>
            </div>

          </div>


          <div class="today-content">

            <span class="blog-tag">
              Life × Tech
            </span>

            <h3>
              Finding the<br />
              Base Condition
            </h3>

            <p>
              Sometimes you just need to return.
            </p>

            <div class="today-footer">

              <span>3 min read</span>

              <button
                @click.stop="selectBlog(blogs[0])"
              >
                Read →
              </button>

            </div>

          </div>

        </article>

      </section>


      <!-- DAILY NOTE -->

      <section class="daily-note">

        <span class="tape"></span>

        <small>daily reminder</small>

        <p>
          “Not every loop is a trap.
          <strong>Some loops are how you grow.</strong>”
        </p>

        <span class="note-heart">♡</span>

      </section>


      <!-- EXPLORE -->

      <section
        id="explore"
        class="explore-section"
      >

        <div class="explore-heading">

          <div>
            <span class="section-mini">
              LITTLE THOUGHTS
            </span>

            <h2>
              Explore ♡
            </h2>
          </div>

          <p>
            same tech.<br />
            different lens.
          </p>

        </div>


        <!-- FILTERS -->

        <div class="filter-row">

          <button
            v-for="category in categories"
            :key="category"
            :class="[
              'filter-pill',
              {
                active:
                  activeCategory === category,
              },
            ]"
            @click="activeCategory = category"
          >
            {{ category }}
          </button>

        </div>


        <!-- BLOG FEED -->

        <div class="blog-feed">

          <article
            v-for="blog in filteredBlogs"
            :key="blog.id"
            class="feed-card"
            @click="selectBlog(blog)"
          >

            <div
              class="feed-art"
              :class="blog.color"
            >
              <span class="feed-sticker">
                {{ blog.sticker }}
              </span>

              <div class="mini-landscape">
                <div class="mini-sun"></div>
                <div class="mini-hill one"></div>
                <div class="mini-hill two"></div>
              </div>
            </div>


            <div class="feed-content">

              <span class="feed-category">
                {{ blog.category }}
              </span>

              <h3>
                {{ blog.title }}
              </h3>

              <p>
                {{ blog.hook }}
              </p>

              <div class="feed-footer">
                <span>
                  {{ blog.readTime }} read
                </span>

                <span class="bookmark">
                  ♡
                </span>
              </div>

            </div>

          </article>


          <!-- COMING SOON -->

          <article
            v-for="blog in comingSoon"
            :key="blog.id"
            class="feed-card coming-card"
          >

            <div
              class="feed-art"
              :class="blog.color"
            >
              <span class="feed-sticker">
                {{ blog.sticker }}
              </span>

              <div class="coming-label">
                brewing ♡
              </div>
            </div>


            <div class="feed-content">

              <span class="feed-category">
                {{ blog.category }}
              </span>

              <h3>
                {{ blog.title }}
              </h3>

              <p>
                {{ blog.hook }}
              </p>

              <div class="feed-footer">
                <span>coming soon</span>
                <span>✦</span>
              </div>

            </div>

          </article>

        </div>

      </section>


      <!-- END STICKERS -->

      <section class="closing-area">

        <div class="pink-note">
          Good blogs.<br />
          brighter days.
          <span>☺</span>
        </div>

        <div class="yellow-note">
          stay a little<br />
          longer ♡
        </div>

        <span class="closing-flower">
          ❀
        </span>

      </section>

    </main>


    <!-- =========================
         BLOG
    ========================== -->

    <main v-else>

      <component
        :is="activeBlog.component"
        @back="goHome"
      />

    </main>

  </div>
</template>
