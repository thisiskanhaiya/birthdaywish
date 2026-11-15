<script setup>
defineEmits(["back"]);
</script>

<template>
  <article class="reader pause-reader">

    <!-- NAV -->
    <header class="reader-nav">
      <button
        type="button"
        aria-label="Back"
        @click="$emit('back')"
      >
        ←
      </button>

      <strong>
        little.log <span>♡</span>
      </strong>

      <button type="button" aria-label="Save">
        ♡
      </button>
    </header>


    <!-- =========================
         CSS-ONLY HERO
    ========================== -->

    <section class="pause-hero">

      <div class="pause-sun"></div>

      <span class="pause-doodle pause-doodle-one">✦</span>
      <span class="pause-doodle pause-doodle-two">♡</span>

      <!-- Coffee -->
      <div class="pause-coffee">
        <div class="coffee-steam steam-one"></div>
        <div class="coffee-steam steam-two"></div>
        <div class="coffee-cup"></div>
        <div class="coffee-handle"></div>
      </div>

      <!-- Phone -->
      <div class="pause-phone">
        <div class="phone-speaker"></div>

        <div class="phone-message msg-one">
          reply now?
        </div>

        <div class="phone-message msg-two">
          maybe pause.
        </div>

        <div class="phone-home"></div>
      </div>

      <!-- Clock -->
      <div class="pause-clock">
        <span class="clock-hand-hour"></span>
        <span class="clock-hand-minute"></span>
        <i></i>
      </div>

      <!-- Main note -->
      <div class="pause-note">
        <small>REMINDER</small>

        <strong>
          You don't have<br />
          to answer yet.
        </strong>

        <span>♡</span>
      </div>

      <p class="pause-hero-caption">
        pause.<br />
        notice.<br />
        then respond.
      </p>

    </section>


    <!-- =========================
         ARTICLE
    ========================== -->

    <section class="reader-content">

      <div class="reader-meta">
        <span class="pause-tag">
          Life
        </span>

        <small>
          3 min read
        </small>
      </div>


      <h1>
        The Quiet Advantage<br />
        of Not Rushing<br />
        Everything
      </h1>


      <p class="reader-subtitle">
        Speed is rewarded everywhere. But some of the best
        decisions happen in the pause before you reply.
      </p>


      <div class="author">
        <span class="author-circle pause-author">
          l
        </span>

        <div>
          <strong>by little.log</strong>
          <small>Thought #03</small>
        </div>

        <div class="reactions">
          <span>♡ 305</span>
          <span>◯ 21</span>
        </div>
      </div>


      <div class="story">

        <p>
          We reply to messages within minutes, decide in
          meetings within seconds and read headlines instead
          of articles.
        </p>

        <p>
          Somewhere along the way,
          <strong>speed became a kind of politeness.</strong>
        </p>


        <!-- Pause statement -->

        <aside class="pause-statement">
          <span>◌</span>

          <p>
            Quick is useful.<br />
            But quick is not always thoughtful.
          </p>
        </aside>


        <h2>
          What rushing costs
        </h2>

        <p>
          When we rush, we often choose the first reasonable
          option instead of the right one.
        </p>

        <p>
          We miss the tone in a colleague’s message.
          We answer the question that was asked, not always
          the one that actually mattered.
        </p>


        <!-- Visual contrast -->

        <div class="rush-comparison">

          <div class="rush-side fast-side">
            <span>⚡</span>

            <small>RUSH</small>

            <strong>
              First reasonable answer
            </strong>

            <p>
              Fast, convenient and sometimes incomplete.
            </p>
          </div>


          <div class="rush-arrow">
            →
          </div>


          <div class="rush-side pause-side">
            <span>◌</span>

            <small>PAUSE</small>

            <strong>
              Better considered answer
            </strong>

            <p>
              A little slower, but with more context.
            </p>
          </div>

        </div>


        <h2>
          Practising the pause
        </h2>


        <div class="pause-practices">

          <div class="pause-practice">
            <span>01</span>

            <div>
              <strong>
                Wait before an important reply.
              </strong>

              <p>
                Give it an hour when you can.
                Most things can wait that long.
              </p>
            </div>
          </div>


          <div class="pause-practice">
            <span>02</span>

            <div>
              <strong>
                Read before reacting.
              </strong>

              <p>
                Finish the full email before deciding what
                you think about it.
              </p>
            </div>
          </div>


          <div class="pause-practice">
            <span>03</span>

            <div>
              <strong>
                Let silence happen.
              </strong>

              <p>
                In a meeting, don't rush to fill every gap.
                Someone may use it to say what actually matters.
              </p>
            </div>
          </div>

        </div>


        <!-- Tip -->

        <div class="pause-tip">

          <span class="pause-tip-tape"></span>

          <small>
            A SMALL RULE
          </small>

          <p>
            Easy to reverse?
            <strong>Decide quickly.</strong>
          </p>

          <p>
            Hard to reverse?
            <strong>Give it a night.</strong>
          </p>

          <span class="pause-tip-heart">
            ♡
          </span>

        </div>


        <div class="pause-question">

          <small>
            BEFORE THE NEXT QUICK YES...
          </small>

          <p>
            Does this decision need speed,
            or does it deserve a little space?
          </p>
        </div>


        <p>
          Not rushing is not the same as being slow.
        </p>

        <p>
          It is simply giving the right things
          <strong>the time they actually need.</strong>
        </p>


        <div class="story-finish pause-finish">
          <span>◌</span>

          <p>
            You don't have to react to everything immediately.
          </p>

          <strong>
            Sometimes the pause is part of the answer. ♡
          </strong>
        </div>

      </div>


      <footer class="reader-footer">

        <button
          type="button"
          @click="$emit('back')"
        >
          ← Back to all thoughts
        </button>

        <span>
          take<br />
          your time ♡
        </span>

      </footer>

    </section>

  </article>
</template>
