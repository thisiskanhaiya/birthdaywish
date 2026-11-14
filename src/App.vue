<script setup>
import { computed, ref } from "vue";
import Recursion from "./blogs/Recursion.vue";

const activeBlog = ref(null);
const category = ref("All");

const blogs = [
  {
    id: "recursion",
    title: "Finding the Base Condition",
    description: "Sometimes you just need to return.",
    category: "Life",
    readTime: "3 min",
    component: Recursion,
  },
];

const upcoming = [
  {
    id: "waiting",
    title: "Not Everything Deserves Infinite Waiting",
    description: "Some responses are timeouts for a reason.",
    category: "Mindset",
    readTime: "3 min",
    art: "hourglass",
  },
  {
    id: "happy",
    title: "Life Doesn't Always Follow the Happy Path",
    description: "Errors are part of the process.",
    category: "Growth",
    readTime: "4 min",
    art: "error",
  },
  {
    id: "commit",
    title: "Commit the Change",
    description: "A new version of you is always possible.",
    category: "Life",
    readTime: "3 min",
    art: "commit",
  },
];

const categories = ["All", "Life", "Tech", "Growth", "Mindset"];

const filteredBlogs = computed(() => {
  if (category.value === "All") return blogs;
  return blogs.filter((blog) => blog.category === category.value);
});

function openBlog(blog) {
  activeBlog.value = blog;
  window.scrollTo({ top: 0, behavior: "smooth" });
}

function goHome() {
  activeBlog.value = null;
  window.scrollTo({ top: 0, behavior: "smooth" });
}

function explore() {
  document.querySelector("#explore")?.scrollIntoView({
    behavior: "smooth",
  });
}
</script>

<template>
  <div class="little-app">

    <!-- LANDING -->
    <template v-if="!activeBlog">

      <header class="topbar">
        <button class="logo" @click="goHome">
          little.log <span>♡</span>
        </button>

        <div class="top-actions">
          <button @click="explore">⌕</button>
          <button>☰</button>
        </div>
      </header>


      <main>

        <!-- ==================================================
             COMPACT HERO
        =================================================== -->

        <section class="hero">

          <div class="hero-text">

            <span class="micro-title">
              TECH THOUGHTS · REAL FEELINGS
            </span>

            <h1>
              Same scroll.
              <em>New perspective.</em>
            </h1>

            <p>
              Small relatable reads for builders,
              overthinkers, dreamers and people who
              occasionally find life inside code.
            </p>

            <button class="primary-btn" @click="explore">
              Explore blogs
              <span>→</span>
            </button>

          </div>


          <!-- CODE-ONLY CUTE STICKER -->

          <div class="desk-sticker">

            <div class="pastel-blob"></div>

            <span class="spark spark-a">✦</span>
            <span class="spark spark-b">♡</span>

            <!-- sticky note -->

            <div class="hero-note">
              <span>♡</span>

              It's not<br />
              just code,<br />
              <strong>it's life too.</strong>
            </div>


            <!-- plant -->

            <div class="plant">
              <div class="leaf leaf-left"></div>
              <div class="leaf leaf-right"></div>
              <div class="stem"></div>
              <div class="pot"></div>
            </div>


            <!-- CHARACTER STICKER -->

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


            <!-- laptop -->

            <div class="cute-laptop">
              <span class="laptop-heart">♡</span>
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
             CATEGORIES
        =================================================== -->

        <section class="quick-categories">

          <button @click="category = 'Life'; explore()">
            <span class="circle peach">☕</span>
            Life
          </button>

          <button @click="category = 'Tech'; explore()">
            <span class="circle blue">⌨</span>
            Tech
          </button>

          <button @click="category = 'Growth'; explore()">
            <span class="circle green">🌱</span>
            Growth
          </button>

          <button @click="category = 'Mindset'; explore()">
            <span class="circle pink">♡</span>
            Mindset
          </button>

        </section>


        <!-- ==================================================
             TODAY
        =================================================== -->

        <section class="today">

          <div class="section-head">

            <div>
              <span>START HERE</span>

              <h2>
                Today's Pick
                <b>✦</b>
              </h2>
            </div>

            <small>
              short &amp; sweet
              ↘
            </small>

          </div>


          <article
            class="featured"
            @click="openBlog(blogs[0])"
          >

            <!-- CSS LANDSCAPE -->

            <div class="landscape">

              <div class="sky-sun"></div>

              <div class="sky-cloud cloud-left">
                <i></i><i></i><i></i>
              </div>

              <div class="sky-cloud cloud-right">
                <i></i><i></i><i></i>
              </div>

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

              <span class="land-flower flower-a">✿</span>
              <span class="land-flower flower-b">✿</span>

            </div>


            <div class="featured-copy">

              <span class="tag">
                Life × Tech
              </span>

              <h3>
                Finding the<br />
                Base Condition
              </h3>

              <p>
                Sometimes you just need to return.
              </p>

              <div class="featured-bottom">

                <small>
                  3 min read
                </small>

                <button @click.stop="openBlog(blogs[0])">
                  Read →
                </button>

              </div>

            </div>

          </article>

        </section>


        <!-- ==================================================
             QUOTE
        =================================================== -->

        <section class="reminder">

          <span class="tape"></span>

          <small>
            DAILY REMINDER
          </small>

          <p>
            “Not every loop is a trap.<br />
            Some loops are how you grow.”
          </p>

          <span class="reminder-heart">
            ♡
          </span>

        </section>


        <!-- ==================================================
             EXPLORE
        =================================================== -->

        <section id="explore" class="explore">

          <div class="section-head">

            <div>
              <span>LITTLE THOUGHTS</span>

              <h2>
                More Thoughts
              </h2>
            </div>

            <small>
              different lens ♡
            </small>

          </div>


          <div class="category-tabs">

            <button
              v-for="item in categories"
              :key="item"
              :class="{ active: category === item }"
              @click="category = item"
            >
              {{ item }}
            </button>

          </div>


          <!-- MOBILE HORIZONTAL / DESKTOP GRID -->

          <div class="thought-list">

            <!-- Actual blog -->

            <article
              v-for="blog in filteredBlogs"
              :key="blog.id"
              class="thought-card"
              @click="openBlog(blog)"
            >

              <div class="thought-art recursion-mini">

                <div class="mini-sun"></div>

                <div class="mini-mountain one"></div>
                <div class="mini-mountain two"></div>

                <div class="mini-sign">
                  <span>continue →</span>
                  <span>← return</span>
                  <i></i>
                </div>

              </div>


              <div class="thought-content">

                <span class="tag">
                  Life × Tech
                </span>

                <h3>
                  {{ blog.title }}
                </h3>

                <p>
                  {{ blog.description }}
                </p>

                <footer>
                  <small>
                    {{ blog.readTime }} read
                  </small>

                  <span>♡</span>
                </footer>

              </div>

            </article>


            <!-- Upcoming -->

            <article
              v-for="blog in upcoming"
              :key="blog.id"
              class="thought-card upcoming"
            >

              <div
                class="thought-art"
                :class="blog.art"
              >

                <!-- HOURGLASS -->

                <div
                  v-if="blog.art === 'hourglass'"
                  class="css-hourglass"
                >
                  <span class="glass-top"></span>
                  <span class="glass-middle"></span>
                  <span class="glass-bottom"></span>
                </div>


                <!-- ERROR -->

                <div
                  v-if="blog.art === 'error'"
                  class="error-laptop"
                >
                  <div class="error-screen">
                    ERROR
                    <span>≠</span>
                    LEARNING
                  </div>

                  <div class="error-keyboard"></div>
                </div>


                <!-- COMMIT -->

                <div
                  v-if="blog.art === 'commit'"
                  class="version-art"
                >
                  <div class="version-circle">
                    ↑
                  </div>

                  <span>
                    new<br />
                    version<br />
                    of me ♡
                  </span>
                </div>


                <span class="coming-pill">
                  coming soon
                </span>

              </div>


              <div class="thought-content">

                <span class="tag">
                  {{ blog.category }}
                </span>

                <h3>
                  {{ blog.title }}
                </h3>

                <p>
                  {{ blog.description }}
                </p>

                <footer>
                  <small>
                    {{ blog.readTime }} read
                  </small>

                  <span>♡</span>
                </footer>

              </div>

            </article>

          </div>

        </section>


        <!-- FOOT NOTE -->

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


      <!-- MOBILE TAB BAR -->

      <nav class="mobile-tabs">

        <button class="active" @click="goHome">
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


    <!-- BLOG -->

    <component
      v-else
      :is="activeBlog.component"
      @back="goHome"
    />

  </div>
</template>
