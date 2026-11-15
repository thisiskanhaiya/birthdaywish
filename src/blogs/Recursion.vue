<script setup>
defineEmits(["back"]);

const selectAnswer = (event) => {
  document
    .querySelectorAll(".recursion-option")
    .forEach((button) => button.classList.remove("selected"));

  event.currentTarget.classList.add("selected");
};
</script>

<template>
  <article class="reader recursion-reader">

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
    <section class="recursion-hero">

      <span class="recursion-spark spark-one">✦</span>
      <span class="recursion-spark spark-two">♡</span>

      <div class="loop loop-one"></div>
      <div class="loop loop-two"></div>
      <div class="loop loop-three"></div>

      <div class="loop-center">
        <small>same pattern</small>
        <strong>↻</strong>
        <span>again?</span>
      </div>

      <div class="recursion-question-card">
        <small>QUICK QUESTION</small>

        <p>
          If tomorrow looked exactly like today,
          would that be okay?
        </p>

        <div class="recursion-options">
          <button
            class="recursion-option"
            type="button"
            @click="selectAnswer"
          >
            yes, keep going 🌱
          </button>

          <button
            class="recursion-option"
            type="button"
            @click="selectAnswer"
          >
            no, something must change 🍂
          </button>
        </div>
      </div>

    </section>


    <!-- ARTICLE -->
    <section class="reader-content">

      <div class="reader-meta">
        <span>Life × Tech</span>
        <small>2 min read</small>
      </div>

      <h1>
        Finding the<br />
        Base Condition
      </h1>

      <p class="reader-subtitle">
        Sometimes you just need to return.
      </p>


      <div class="author">
        <span class="author-circle recursion-author">
          l
        </span>

        <div>
          <strong>by little.log</strong>
          <small>Thought #01</small>
        </div>

        <div class="reactions">
          <span>♡ 412</span>
          <span>◯ 28</span>
        </div>
      </div>


      <div class="story">

        <p>
          In programming, recursion happens when a function
          calls itself.
        </p>

        <p>
          It can be elegant and powerful. But without a
          <strong>base condition</strong>, it never knows
          when to stop.
        </p>


        <div class="recursion-code">
          <div class="code-top">
            <span></span>
            <span></span>
            <span></span>
            <small>life.js</small>
          </div>

          <code>
            <span>function repeat(pattern) {</span>
            <span>&nbsp;&nbsp;if (pattern.isDraining) return;</span>
            <span>&nbsp;&nbsp;return repeat(pattern);</span>
            <span>}</span>
          </code>
        </div>


        <p>
          Life does this too.
        </p>

        <p>
          Same morning. Same thought. Same situation.
          Same response. And tomorrow, the function gets
          called again.
        </p>


        <div class="human-question recursion-human-question">
          <small>BUT WAIT...</small>

          <p>
            Are you continuing because the pattern is helping
            you, or because you haven't decided how to leave it?
          </p>
        </div>


        <h2>
          Find your base condition.
        </h2>

        <p>
          Maybe it is a boundary. A conversation. A decision.
          A pause. Or simply accepting that this loop has
          already taught you enough.
        </p>


        <div class="recursion-choices">

          <div class="recursion-choice keep-loop">
            <span>🌱</span>

            <div>
              <small>KEEP THE LOOP</small>

              <strong>
                When each round adds something.
              </strong>

              <p>
                More skill, peace, connection or clarity.
              </p>
            </div>
          </div>


          <div class="recursion-choice leave-loop">
            <span>🍂</span>

            <div>
              <small>FIND THE EXIT</small>

              <strong>
                When each round takes something.
              </strong>

              <p>
                Less energy, confidence, patience or joy.
              </p>
            </div>
          </div>

        </div>


        <div class="recursion-sticky">
          <span class="sticky-tape"></span>

          <small>BEFORE THE NEXT CALL...</small>

          <p>
            Is this loop growing you,
            or only repeating you?
          </p>

          <span class="sticky-heart">♡</span>
        </div>


        <p>
          Not every recursion is bad. Some routines build us.
          Some people make every iteration better.
        </p>

        <p>
          Keep those.
        </p>

        <p>
          But when every iteration takes more than it gives,
          you don't need another call.
        </p>


        <div class="story-finish recursion-finish">
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
        <button type="button" @click="$emit('back')">
          ← Back to all thoughts
        </button>

        <span>
          some loops<br />
          can end ♡
        </span>
      </footer>

    </section>

  </article>
</template>

<style scoped>
.recursion-hero {
  position: relative;
  min-height: 385px;
  overflow: hidden;
  background:
    radial-gradient(circle at 82% 18%, #fff0a9 0 8%, transparent 22%),
    linear-gradient(145deg, #d9efff, #e4dcff 38%, #ffdce8 72%, #ffe7bd);
}

.recursion-spark {
  position: absolute;
  z-index: 5;
  color: #8d72bd;
  font-size: 24px;
}

.spark-one {
  top: 38px;
  left: 42px;
}

.spark-two {
  top: 88px;
  left: 90px;
  color: #e66b9c;
}

.loop {
  position: absolute;
  border: 2px solid rgba(113, 89, 180, 0.24);
  border-radius: 47% 53% 58% 42%;
}

.loop-one {
  top: 37px;
  right: 75px;
  width: 245px;
  height: 245px;
  animation: recursion-spin 18s linear infinite;
}

.loop-two {
  top: 76px;
  right: 113px;
  width: 170px;
  height: 170px;
  border-color: rgba(235, 102, 156, 0.3);
  animation: recursion-spin 13s linear infinite reverse;
}

.loop-three {
  top: 111px;
  right: 148px;
  width: 100px;
  height: 100px;
  border-color: rgba(255, 160, 89, 0.35);
  animation: recursion-spin 9s linear infinite;
}

.loop-center {
  position: absolute;
  top: 127px;
  right: 162px;
  z-index: 4;
  width: 72px;
  height: 72px;
  border-radius: 25px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: white;
  background: linear-gradient(145deg, #755fc2, #dd68a0);
  box-shadow: 0 15px 30px rgba(101, 77, 153, 0.23);
  transform: rotate(5deg);
}

.loop-center small,
.loop-center span {
  font-size: 6px;
}

.loop-center strong {
  font-size: 25px;
  line-height: 1;
}

.recursion-question-card {
  position: absolute;
  left: 42px;
  bottom: 38px;
  z-index: 8;
  width: 295px;
  padding: 22px;
  border: 1px solid rgba(73, 56, 96, 0.1);
  border-radius: 18px;
  background: rgba(255, 255, 255, 0.84);
  box-shadow: 0 17px 35px rgba(62, 48, 91, 0.11);
  backdrop-filter: blur(12px);
  transform: rotate(-2deg);
}

.recursion-question-card small,
.human-question small,
.recursion-sticky small,
.recursion-choice small {
  color: #8c78ad;
  font-family: "DM Mono", monospace;
  font-size: 6px;
  letter-spacing: 0.8px;
}

.recursion-question-card p {
  margin: 8px 0 14px;
  color: #514858;
  font-family: "Patrick Hand", cursive;
  font-size: 18px;
  line-height: 1.12;
}

.recursion-options {
  display: flex;
  flex-direction: column;
  gap: 7px;
}

.recursion-option {
  padding: 9px 11px;
  border: 1px solid #dfd7e8;
  border-radius: 10px;
  color: #686071;
  background: white;
  font-size: 8px;
  text-align: left;
}

.recursion-option.selected {
  border-color: #ab91d0;
  color: #6852a5;
  background: #f0ebff;
}

.recursion-author {
  background: #7864c3;
}

.recursion-code {
  margin: 28px 0;
  overflow: hidden;
  border-radius: 14px;
  color: #ded6ff;
  background: #25233c;
  box-shadow: 0 15px 32px rgba(37, 31, 59, 0.17);
}

.code-top {
  padding: 10px 13px;
  display: flex;
  gap: 5px;
  background: #312e49;
}

.code-top > span {
  width: 8px;
  height: 8px;
  border-radius: 50%;
}

.code-top > span:first-child {
  background: #ef7277;
}

.code-top > span:nth-child(2) {
  background: #efc65e;
}

.code-top > span:nth-child(3) {
  background: #76c27c;
}

.code-top small {
  margin-left: auto;
  color: #aaa4b8;
  font-family: "DM Mono", monospace;
  font-size: 7px;
}

.recursion-code code {
  padding: 20px;
  display: flex;
  flex-direction: column;
  font-family: "DM Mono", monospace;
  font-size: 9px;
  line-height: 1.8;
}

.recursion-code code span:nth-child(2) {
  color: #f28eb7;
}

.human-question {
  margin: 29px 0;
  padding: 23px;
  border-radius: 15px;
}

.recursion-human-question {
  background: linear-gradient(135deg, #eee8ff, #ffe7f0);
}

.human-question p {
  margin: 8px 0 0;
  color: #554b5c;
  font-family: "Patrick Hand", cursive;
  font-size: 19px;
  line-height: 1.16;
}

.recursion-choices {
  margin: 28px 0;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 11px;
}

.recursion-choice {
  padding: 18px;
  border-radius: 14px;
  display: flex;
  gap: 11px;
}

.keep-loop {
  background: #e8f5e6;
}

.leave-loop {
  background: #fff0dd;
}

.recursion-choice > span {
  font-size: 23px;
}

.recursion-choice strong {
  display: block;
  margin-top: 4px;
  color: #504950;
  font-size: 10px;
}

.recursion-choice p {
  margin: 6px 0 0;
  color: #7e7880;
  font-size: 8px;
  line-height: 1.45;
}

.recursion-sticky {
  position: relative;
  margin: 34px 0;
  padding: 29px 23px;
  background: #ffe7a8;
  box-shadow: 4px 6px 15px rgba(65, 53, 38, 0.09);
  text-align: center;
  transform: rotate(-1deg);
}

.sticky-tape {
  position: absolute;
  top: -13px;
  left: calc(50% - 38px);
  width: 76px;
  height: 26px;
  background: rgba(203, 189, 239, 0.73);
  transform: rotate(3deg);
}

.recursion-sticky p {
  margin: 9px 0 0;
  color: #5e4d57;
  font-family: "Patrick Hand", cursive;
  font-size: 20px;
  line-height: 1.1;
}

.sticky-heart {
  position: absolute;
  right: 15px;
  bottom: 9px;
  color: #df6797;
  font-size: 20px;
}

.recursion-finish {
  background: linear-gradient(135deg, #fff9e9, #eeeaff);
}

@keyframes recursion-spin {
  to {
    transform: rotate(360deg);
  }
}

@media (max-width: 600px) {
  .recursion-hero {
    min-height: 330px;
  }

  .loop-one {
    top: 24px;
    right: -10px;
    width: 190px;
    height: 190px;
  }

  .loop-two {
    top: 55px;
    right: 21px;
    width: 128px;
    height: 128px;
  }

  .loop-three {
    top: 81px;
    right: 47px;
    width: 76px;
    height: 76px;
  }

  .loop-center {
    top: 91px;
    right: 55px;
    width: 60px;
    height: 60px;
  }

  .recursion-question-card {
    left: 17px;
    right: 17px;
    bottom: 24px;
    width: auto;
    padding: 18px;
  }

  .recursion-question-card p {
    font-size: 16px;
  }

  .recursion-choices {
    grid-template-columns: 1fr;
  }
}
</style>
