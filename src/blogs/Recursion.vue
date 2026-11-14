<script setup>
defineEmits(["back"]);
</script>

<template>

  <article class="reader">

    <!-- Reader navbar -->

    <header class="reader-nav">

      <button @click="$emit('back')">
        ←
      </button>

      <strong>
        little.log <span>♡</span>
      </strong>

      <button>
        ♡
      </button>

    </header>


    <!-- ==================================================
         PURE CSS HERO
    =================================================== -->

    <section class="reader-hero">

      <div class="reader-sun"></div>

      <div class="reader-cloud rc-one">
        <i></i><i></i><i></i>
      </div>

      <div class="reader-cloud rc-two">
        <i></i><i></i><i></i>
      </div>

      <div class="reader-mountain rm-one"></div>
      <div class="reader-mountain rm-two"></div>
      <div class="reader-mountain rm-three"></div>

      <div class="reader-hill"></div>


      <!-- Small seated sticker -->

      <div class="traveller">

        <div class="traveller-head"></div>
        <div class="traveller-hair"></div>
        <div class="traveller-bun"></div>

        <div class="traveller-body"></div>

        <div class="backpack">
          <span>♡</span>
        </div>

      </div>


      <p>
        Some loops<br />
        are meant to end<br />
        so you can<br />
        begin again ♡
      </p>

    </section>


    <!-- ==================================================
         CONTENT
    =================================================== -->

    <section class="reader-content">

      <div class="reader-meta">

        <span>
          Life × Tech
        </span>

        <small>
          3 min read
        </small>

      </div>


      <h1>
        Finding the<br />
        Base Condition
      </h1>


      <p class="reader-subtitle">
        Sometimes you just need to return.
      </p>


      <div class="author">

        <span class="author-circle">
          l
        </span>

        <div>
          <strong>
            by little.log
          </strong>

          <small>
            Thought #01
          </small>
        </div>

        <div class="reactions">
          <span>♡ 412</span>
          <span>◯ 28</span>
        </div>

      </div>


      <div class="story">

        <p>
          In programming, recursion happens when a function
          calls itself. It's powerful, but without a
          <strong>base condition</strong>, it never stops.
        </p>

        <p>
          Life can feel the same sometimes. The same routine,
          thought or situation returns, and we enter it with
          the same response.
        </p>


        <!-- CODE -->

        <div class="code-card">

          <header>

            <div>
              <i></i>
              <i></i>
              <i></i>
            </div>

            <small>
              life.js
            </small>

          </header>

          <pre><code><b>function</b> repeat(pattern) {
  <b>if</b> (pattern.isDraining) <em>return</em>;
  <b>return</b> repeat(pattern);
}</code></pre>

        </div>


        <!-- NOTE -->

        <aside class="story-note">

          <span>♡</span>

          <p>
            Maybe the question isn't
            “Why am I in this loop?” but
            <strong>
              “What will help me return?”
            </strong>
          </p>

        </aside>


        <h2>
          Some loops are worth keeping.
        </h2>

        <p>
          Practicing, learning and caring can add something
          with every iteration.
        </p>


        <!-- TWO CARDS -->

        <div class="decision-grid">

          <div class="decision keep">

            <span>🌱</span>

            <div>
              <small>
                CONTINUE
              </small>

              <strong>
                It adds value.
              </strong>

              <p>
                More clarity, skill, peace or connection.
              </p>
            </div>

          </div>


          <div class="decision leave">

            <span>🍂</span>

            <div>
              <small>
                RETURN
              </small>

              <strong>
                It drains you.
              </strong>

              <p>
                Less energy, confidence, patience or joy.
              </p>
            </div>

          </div>

        </div>


        <div class="story-question">

          <small>
            BEFORE THE NEXT CALL...
          </small>

          <p>
            Is this loop
            <strong>growing you</strong>
            or only repeating you?
          </p>

        </div>


        <p>
          You don't need to escape every recursion.
          Keep the ones that help you become more.
        </p>

        <p>
          But if every iteration takes more than it gives,
          maybe you've already found your base condition.
        </p>


        <div class="story-finish">

          <span>↻</span>

          <p>
            Find the base condition.
          </p>

          <strong>
            And let yourself return. ♡
          </strong>

        </div>

      </div>


      <footer class="reader-footer">

        <button @click="$emit('back')">
          ← Back to all thoughts
        </button>

        <span>
          keep going ♡
        </span>

      </footer>

    </section>

  </article>

</template>
