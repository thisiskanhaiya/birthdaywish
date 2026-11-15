<script setup>
import { ref } from "vue";

defineEmits(["back"]);

const answer = ref("");
</script>

<template>
  <article class="reader pause-reader">

    <!-- NAVIGATION -->
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


    <!-- INTERACTIVE HERO -->
    <section class="pause-blog-hero">

      <span class="pause-spark pause-spark-one">✦</span>
      <span class="pause-spark pause-spark-two">♡</span>

      <div class="pause-sun"></div>


      <!-- Phone message -->

      <div class="message-phone">
        <div class="phone-top"></div>

        <div class="message-bubble incoming">
          Hey, can we change this again?
        </div>

        <div class="typing-indicator">
          <span></span>
          <span></span>
          <span></span>
        </div>

        <div class="phone-bottom"></div>
      </div>


      <!-- Coffee -->

      <div class="pause-coffee">
        <span class="steam steam-one"></span>
        <span class="steam steam-two"></span>

        <div class="coffee-body"></div>
        <div class="coffee-handle"></div>
      </div>


      <!-- Question -->

      <div class="pause-choice-card">
        <small>WHAT WOULD YOU DO?</small>

        <p>
          A message annoys you a little.
          Do you reply immediately?
        </p>

        <div class="pause-buttons">
          <button
            type="button"
            :class="{ selected: answer === 'now' }"
            @click="answer = 'now'"
          >
            Reply now ⚡
          </button>

          <button
            type="button"
            :class="{ selected: answer === 'wait' }"
            @click="answer = 'wait'"
          >
            Wait a little ☕
          </button>
        </div>

        <div v-if="answer" class="pause-answer">
          <template v-if="answer === 'now'">
            Maybe type it... but don't send it yet.
          </template>

          <template v-else>
            Good. Finish the coffee first.
          </template>
        </div>
      </div>


      <p class="pause-caption">
        not everything<br />
        needs you<br />
        immediately. ♡
      </p>

    </section>


    <!-- ARTICLE -->
    <section class="reader-content">

      <div class="reader-meta">
        <span class="pause-tag">Life</span>
        <small>2 min read</small>
      </div>

      <h1>
        The Quiet Advantage<br />
        of Not Rushing<br />
        Everything
      </h1>

      <p class="reader-subtitle">
        Some of the best decisions happen in the pause
        before you reply.
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
          We reply to messages within minutes.
          Decide in meetings within seconds.
          Sometimes we form an opinion from the headline.
        </p>

        <p>
          Somewhere along the way,
          <strong>speed started looking like efficiency.</strong>
        </p>


        <div class="pause-human-question">
          <small>BUT WAIT...</small>

          <p>
            Have you ever replied quickly and five minutes
            later thought,
            <strong>“I could have said that better”?</strong>
          </p>
        </div>


        <h2>
          That’s what rushing costs.
        </h2>

        <p>
          Not always a disaster. Sometimes just a slightly
          worse decision.
        </p>

        <p>
          We miss the tone in a message. We choose the first
          reasonable option. We answer what was asked instead
          of noticing what actually mattered.
        </p>


        <div class="coffee-experiment">
          <span>☕</span>

          <div>
            <small>A TINY EXPERIMENT</small>

            <p>
              Next time something makes you want to reply
              immediately...
            </p>

            <strong>Don't.</strong>

            <p>
              Finish your coffee first.
            </p>
          </div>
        </div>


        <h2>
          Try these three pauses.
        </h2>


        <div class="pause-practices">

          <div class="pause-practice">
            <span>01</span>

            <div>
              <strong>Important reply?</strong>

              <p>
                Give it an hour if you can.
                Most things can wait that long.
              </p>
            </div>
          </div>


          <div class="pause-practice">
            <span>02</span>

            <div>
              <strong>Long email?</strong>

              <p>
                Reach the last line before deciding
                what you think.
              </p>
            </div>
          </div>


          <div class="pause-practice">
            <span>03</span>

            <div>
              <strong>Silence in a meeting?</strong>

              <p>
                Let it exist. Someone may use it to say
                what actually matters.
              </p>
            </div>
          </div>

        </div>


        <div class="decision-rule">
          <span class="rule-tape"></span>

          <small>MY FAVOURITE RULE</small>

          <div class="decision-row">
            <span>Easy to undo?</span>
            <strong>Decide quickly →</strong>
          </div>

          <div class="decision-row important">
            <span>Hard to undo?</span>
            <strong>Sleep on it ☾</strong>
          </div>

          <span class="rule-heart">♡</span>
        </div>


        <div class="pause-final-question">
          <small>ONE QUESTION FOR YOU...</small>

          <p>
            What is one thing you're rushing right now
            that actually has permission to wait?
          </p>
        </div>


        <p>
          Not rushing isn't slowness.
        </p>

        <p>
          It is giving the right things
          <strong>the time they actually need.</strong>
        </p>


        <div class="story-finish pause-finish">
          <span>◷</span>

          <p>
            You don't have to react immediately.
          </p>

          <strong>
            Sometimes the pause is part of the answer. ♡
          </strong>
        </div>

      </div>


      <footer class="reader-footer">
        <button type="button" @click="$emit('back')">
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

<style scoped>
.pause-blog-hero {
  position: relative;
  min-height: 430px;
  overflow: hidden;
  background:
    radial-gradient(circle at 80% 18%, #ffeba5 0 9%, transparent 23%),
    linear-gradient(145deg, #cff2ff, #e4ddff 38%, #ffdce8 72%, #ffebc1);
}

.pause-spark {
  position: absolute;
  z-index: 5;
  color: #856eaf;
  font-size: 24px;
}

.pause-spark-one {
  top: 40px;
  left: 43px;
}

.pause-spark-two {
  top: 91px;
  left: 91px;
  color: #e66a9b;
}

.pause-sun {
  position: absolute;
  top: 46px;
  right: 58px;
  width: 85px;
  height: 85px;
  border-radius: 50%;
  background: rgba(255, 225, 129, 0.82);
}

.message-phone {
  position: absolute;
  top: 73px;
  right: 100px;
  width: 165px;
  height: 255px;
  border: 4px solid #514860;
  border-radius: 27px;
  background: linear-gradient(#fffafa, #f4f0fa);
  box-shadow: 10px 14px 0 rgba(78, 62, 98, 0.11);
  transform: rotate(6deg);
}

.phone-top {
  position: absolute;
  top: 12px;
  left: calc(50% - 22px);
  width: 44px;
  height: 5px;
  border-radius: 10px;
  background: #91899a;
}

.message-bubble {
  position: absolute;
  top: 60px;
  left: 14px;
  right: 25px;
  padding: 12px;
  border-radius: 14px 14px 14px 4px;
  color: #5d5667;
  background: #e7e1ff;
  font-size: 9px;
  line-height: 1.45;
}

.typing-indicator {
  position: absolute;
  top: 137px;
  right: 15px;
  padding: 8px 11px;
  border-radius: 14px 14px 4px 14px;
  display: flex;
  gap: 4px;
  background: #ffe0eb;
}

.typing-indicator span {
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background: #ae758c;
}

.phone-bottom {
  position: absolute;
  left: calc(50% - 11px);
  bottom: 10px;
  width: 22px;
  height: 22px;
  border: 2px solid #aaa3b1;
  border-radius: 50%;
}

.pause-coffee {
  position: absolute;
  left: 74px;
  bottom: 57px;
  width: 100px;
  height: 105px;
}

.coffee-body {
  position: absolute;
  left: 9px;
  bottom: 0;
  width: 68px;
  height: 62px;
  border: 3px solid #61556b;
  border-radius: 6px 6px 21px 21px;
  background: linear-gradient(145deg, #ffcda9, #f19dad);
}

.coffee-handle {
  position: absolute;
  bottom: 17px;
  right: 2px;
  width: 28px;
  height: 31px;
  border: 7px solid #61556b;
  border-left: 0;
  border-radius: 0 50% 50% 0;
}

.steam {
  position: absolute;
  top: 1px;
  width: 3px;
  height: 34px;
  border-radius: 50%;
  background: rgba(85, 72, 92, 0.26);
}

.steam-one {
  left: 31px;
  transform: rotate(8deg);
}

.steam-two {
  left: 53px;
  transform: rotate(-9deg);
}

.pause-choice-card {
  position: absolute;
  left: 39px;
  top: 45px;
  z-index: 8;
  width: 285px;
  padding: 22px;
  border: 1px solid rgba(70, 57, 91, 0.1);
  border-radius: 19px;
  background: rgba(255, 255, 255, 0.86);
  box-shadow: 0 18px 38px rgba(61, 48, 90, 0.1);
  backdrop-filter: blur(12px);
  transform: rotate(-2deg);
}

.pause-choice-card > small,
.pause-human-question small,
.coffee-experiment small,
.pause-practice > span,
.decision-rule > small,
.pause-final-question small {
  color: #8975aa;
  font-family: "DM Mono", monospace;
  font-size: 6px;
  letter-spacing: 0.8px;
}

.pause-choice-card > p {
  margin: 8px 0 14px;
  color: #504757;
  font-family: "Patrick Hand", cursive;
  font-size: 18px;
  line-height: 1.12;
}

.pause-buttons {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 7px;
}

.pause-buttons button {
  padding: 10px;
  border: 1px solid #ded7e4;
  border-radius: 10px;
  color: #676070;
  background: white;
  font-size: 8px;
}

.pause-buttons button.selected {
  border-color: #9f8ac5;
  color: #6650a0;
  background: #eee9ff;
}

.pause-answer {
  margin-top: 9px;
  padding: 8px 10px;
  border-radius: 9px;
  color: #75566b;
  background: #fff0f5;
  font-family: "Patrick Hand", cursive;
  font-size: 13px;
}

.pause-caption {
  position: absolute;
  right: 25px;
  bottom: 30px;
  margin: 0;
  color: #755f77;
  font-family: "Patrick Hand", cursive;
  font-size: 17px;
  line-height: 1.05;
  text-align: right;
  transform: rotate(4deg);
}

.pause-author {
  background: #df82a7;
}

.pause-human-question {
  margin: 29px 0;
  padding: 23px;
  border-radius: 15px;
  background: linear-gradient(135deg, #e6f1ff, #f0e9ff, #ffe7ef);
}

.pause-human-question p {
  margin: 8px 0 0;
  color: #554b5c;
  font-family: "Patrick Hand", cursive;
  font-size: 19px;
  line-height: 1.16;
}

.coffee-experiment {
  margin: 29px 0;
  padding: 22px;
  border-radius: 15px;
  display: flex;
  gap: 14px;
  background: #fff0dd;
}

.coffee-experiment > span {
  font-size: 30px;
}

.coffee-experiment p {
  margin: 6px 0;
  color: #695b5d;
  font-size: 9px;
  line-height: 1.45;
}

.coffee-experiment strong {
  display: block;
  color: #4f4347;
  font-family: "Patrick Hand", cursive;
  font-size: 24px;
  line-height: 1;
}

.pause-practices {
  margin: 25px 0 31px;
  border: 1px solid #e1dbe6;
  border-radius: 16px;
  overflow: hidden;
  background: #fffafd;
}

.pause-practice {
  padding: 18px 20px;
  border-bottom: 1px dashed #ddd5e1;
  display: grid;
  grid-template-columns: 38px 1fr;
  gap: 11px;
}

.pause-practice:last-child {
  border-bottom: 0;
}

.pause-practice strong {
  display: block;
  color: #524b58;
  font-size: 10px;
}

.pause-practice p {
  margin: 5px 0 0;
  color: #85808a;
  font-size: 8px;
  line-height: 1.5;
}

.decision-rule {
  position: relative;
  margin: 34px 0;
  padding: 29px 24px;
  background: #ffe6a5;
  box-shadow: 4px 6px 14px rgba(65, 52, 37, 0.09);
  transform: rotate(-0.8deg);
}

.rule-tape {
  position: absolute;
  top: -13px;
  left: calc(50% - 38px);
  width: 76px;
  height: 26px;
  background: rgba(205, 190, 240, 0.7);
  transform: rotate(3deg);
}

.decision-row {
  margin-top: 11px;
  padding: 11px 13px;
  border-radius: 10px;
  display: flex;
  justify-content: space-between;
  gap: 10px;
  color: #6e6067;
  background: rgba(255, 255, 255, 0.65);
  font-size: 9px;
}

.decision-row strong {
  color: #66528a;
}

.decision-row.important {
  background: rgba(238, 231, 255, 0.82);
}

.rule-heart {
  position: absolute;
  right: 14px;
  bottom: 8px;
  color: #df6797;
  font-size: 20px;
}

.pause-final-question {
  margin: 32px 0;
  padding: 27px;
  border-radius: 15px;
  color: white;
  background: linear-gradient(135deg, #6078ae, #8068ad 52%, #b9709d);
  box-shadow: 0 13px 27px rgba(79, 70, 120, 0.18);
  text-align: center;
}

.pause-final-question small {
  color: rgba(255, 255, 255, 0.7);
}

.pause-final-question p {
  margin: 9px 0 0;
  font-family: "Patrick Hand", cursive;
  font-size: 20px;
  line-height: 1.15;
}

.pause-finish {
  background: linear-gradient(135deg, #fff9e9, #eeeaff);
}

@media (max-width: 600px) {
  .pause-blog-hero {
    min-height: 485px;
  }

  .message-phone {
    top: 35px;
    right: 20px;
    transform: rotate(6deg) scale(0.68);
    transform-origin: top right;
  }

  .pause-choice-card {
    left: 16px;
    right: 16px;
    top: auto;
    bottom: 28px;
    width: auto;
    padding: 18px;
  }

  .pause-choice-card > p {
    font-size: 16px;
  }

  .pause-coffee {
    left: 31px;
    bottom: 215px;
    transform: scale(0.72);
    transform-origin: bottom left;
  }

  .pause-caption {
    display: none;
  }

  .pause-buttons {
    grid-template-columns: 1fr;
  }

  .decision-row {
    flex-direction: column;
    gap: 4px;
  }
}
</style>
