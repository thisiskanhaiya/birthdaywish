<script setup>
defineEmits(["back"]);
</script>

<template>

  <article class="reading-page">

    <!-- ARTICLE NAV -->

    <div class="reading-nav">

      <button
        class="back-button"
        @click="$emit('back')"
      >
        ←
      </button>

      <span>
        little.log ♡
      </span>

      <button class="bookmark-button">
        ♡
      </button>

    </div>


    <!-- ILLUSTRATION -->

    <section class="reading-art">

      <div class="article-sky">

        <span class="article-cloud cloud-a">
          ☁
        </span>

        <span class="article-cloud cloud-b">
          ☁
        </span>

        <div class="article-sun"></div>

        <span class="article-quote-art">
          some loops are<br />
          meant to end<br />
          so you can<br />
          begin again ♡
        </span>

      </div>


      <div class="big-mountain mountain-a"></div>
      <div class="big-mountain mountain-b"></div>

      <div class="sitting-person">
        <div class="person-mini-head"></div>
        <div class="person-mini-body"></div>
        <div class="person-bag"></div>
      </div>

    </section>


    <!-- ARTICLE -->

    <section class="reading-content">

      <div class="reading-meta">
        <span class="pink-tag">Life</span>
        <span>3 min read</span>
      </div>

      <h1>
        Finding the
        <span>Base Condition</span>
      </h1>

      <p class="reading-subtitle">
        Sometimes you just need to return.
      </p>


      <div class="author-line">

        <div class="author-avatar">
          l
        </div>

        <div>
          <strong>little.log</strong>
          <small>thought #01</small>
        </div>

      </div>


      <div class="article-text">

        <p>
          In programming, recursion happens when
          something keeps calling itself.
        </p>

        <p>
          Beautiful idea.
          <strong>
            Until there's no base condition.
          </strong>
        </p>


        <div class="tiny-code">

          <span>
            life();
          </span>

          <span class="code-arrow">
            ↓
          </span>

          <span>
            life();
          </span>

          <span class="code-arrow">
            ↓
          </span>

          <span>
            life();
          </span>

          <small>
            ...okay, but until when?
          </small>

        </div>


        <p>
          Life does this too.
        </p>

        <p>
          Same morning. Same thought.
          Same situation. Same response.
        </p>

        <div class="article-sticky pink-sticky">

          <span>♡</span>

          <p>
            Maybe the question isn't
            <strong>“Why am I in this loop?”</strong>
          </p>

          <p>
            Maybe it's
            <strong>“What will help me return?”</strong>
          </p>

        </div>


        <h2>
          Find your base condition.
        </h2>

        <p>
          Maybe it's a boundary.
          A conversation.
          A decision.
          A pause.
          Or simply accepting that you've
          learned everything this loop had to teach.
        </p>


        <div class="little-choice">

          <div class="choice grow-choice">

            <span>🌱</span>

            <div>
              <strong>Still growing?</strong>
              <p>
                Maybe one more iteration is worth it.
              </p>
            </div>

          </div>


          <div class="choice exit-choice">

            <span>🍂</span>

            <div>
              <strong>Only draining?</strong>
              <p>
                Maybe you've found the base condition.
              </p>
            </div>

          </div>

        </div>


        <div class="final-question">

          <small>
            before calling yourself again...
          </small>

          <p>
            Is this loop
            <strong>growing you</strong>
            or only
            <strong>repeating you?</strong>
          </p>

        </div>


        <p>
          Not every recursion is bad.
          Some routines build us.
          Some people make every iteration better.
          Some practices deserve repeating.
        </p>

        <p>
          Keep those.
        </p>

        <p>
          But when each iteration takes more than
          it gives, you don't need another call.
        </p>


        <div class="end-note">

          <span class="end-loop">
            ↻
          </span>

          <p>
            Find the base condition.
          </p>

          <strong>
            And let yourself return.
          </strong>

          <span class="tiny-heart">
            ♡
          </span>

        </div>

      </div>


      <div class="article-bottom">

        <span>
          ✿ thanks for reading
        </span>

        <button
          @click="$emit('back')"
        >
          more little thoughts →
        </button>

      </div>

    </section>

  </article>

</template>
