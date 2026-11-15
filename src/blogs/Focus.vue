<script setup>
import { ref } from "vue";

defineEmits(["back"]);

const priorities = ref([]);
const choices = [
  "Learn one useful thing",
  "Finish what I already started",
  "Practise without switching",
  "Improve one small weakness",
  "Rest without feeling guilty",
];

const togglePriority = (choice) => {
  if (priorities.value.includes(choice)) {
    priorities.value = priorities.value.filter(
      (priority) => priority !== choice
    );
    return;
  }

  if (priorities.value.length < 3) {
    priorities.value.push(choice);
  }
};
</script>

<template>
  <article class="reader focus-reader">

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


    <!-- HERO -->
    <section class="focus-blog-hero">

      <span class="focus-blog-spark focus-spark-one">✦</span>
      <span class="focus-blog-spark focus-spark-two">♡</span>

      <div class="focus-orbit orbit-large"></div>
      <div class="focus-orbit orbit-small"></div>

      <div class="focus-target">
        <span>01</span>
        <small>one thing</small>
      </div>


      <div class="focus-question-card">
        <small>A SMALL CHALLENGE</small>

        <p>
          If you could keep only three priorities this week,
          which three would survive?
        </p>

        <div class="priority-options">
          <button
            v-for="choice in choices"
            :key="choice"
            type="button"
            :class="{
              selected: priorities.includes(choice),
              disabled:
                priorities.length === 3 &&
                !priorities.includes(choice),
            }"
            @click="togglePriority(choice)"
          >
            <span>
              {{ priorities.includes(choice) ? "✓" : "+" }}
            </span>

            {{ choice }}
          </button>
        </div>

        <div class="priority-count">
          {{ priorities.length }} / 3 chosen
        </div>
      </div>

    </section>


    <!-- ARTICLE -->
    <section class="reader-content">

      <div class="reader-meta">
        <span class="focus-tag">Growth</span>
        <small>2 min read</small>
      </div>

      <h1>
        Don’t Rush.<br />
        Focus on One Thing<br />
        at a Time.
      </h1>

      <p class="reader-subtitle">
        Being busy doesn’t always mean being productive.
      </p>


      <div class="author">
        <span class="author-circle focus-author">
          l
        </span>

        <div>
          <strong>by little.log</strong>
          <small>Thought #02</small>
        </div>

        <div class="reactions">
          <span>♡ 268</span>
          <span>◯ 17</span>
        </div>
      </div>


      <div class="story">

        <p>
          Last January, I started the year with a long list
          of things I wanted to achieve.
        </p>

        <p>
          So many plans. So many ideas. And somehow,
          everything felt important at the same time.
        </p>


        <div class="focus-human-question">
          <small>QUICK CHECK...</small>

          <p>
            Have you ever had such a long to-do list that
            you spent more time choosing what to do than
            actually doing it?
          </p>
        </div>


        <p>
          I kept saying yes because I thought doing more
          meant achieving more.
        </p>

        <p>
          But at the end of the month, I had started many
          things and given enough attention to none of them.
        </p>


        <aside class="focus-line">
          <span>✦</span>

          <p>
            I wasn’t lacking effort.<br />
            I was spreading it too thin.
          </p>
        </aside>


        <h2>
          So I tried one simple rule.
        </h2>


        <div class="three-rule">

          <div class="three-rule-title">
            <span>3</span>

            <div>
              <small>THE WEEKLY RULE</small>

              <strong>
                Choose only three things.
              </strong>
            </div>
          </div>


          <div class="three-rule-item">
            <span>01</span>

            <div>
              <strong>Choose deliberately.</strong>

              <p>
                Pick three things that genuinely matter
                this week.
              </p>
            </div>
          </div>


          <div class="three-rule-item">
            <span>02</span>

            <div>
              <strong>Give focused time.</strong>

              <p>
                Spend 40–50 minutes on each one every day.
              </p>
            </div>
          </div>


          <div class="three-rule-item">
            <span>03</span>

            <div>
              <strong>Finish before adding.</strong>

              <p>
                Move something forward before replacing it
                with the next interesting idea.
              </p>
            </div>
          </div>

        </div>


        <p>
          Interesting doesn’t always mean
          <strong>important right now.</strong>
        </p>

        <p>
          You can write a new idea down without immediately
          giving it your attention.
        </p>


        <div class="idea-note">
          <span class="idea-tape"></span>

          <small>IDEA PARKING LOT</small>

          <p>
            “Good idea.<br />
            Not this week.” ♡
          </p>
        </div>


        <h2>
          Exploration is good.
          Endless starting isn’t.
        </h2>

        <p>
          Trying different things helps us discover what we
          enjoy. But exploration should not become a reason
          for never developing depth.
        </p>


        <div class="focus-shift">

          <div class="focus-shift-side scattered-side">
            <span>↗</span>
            <small>TOO MANY DIRECTIONS</small>
            <strong>Busy energy</strong>
            <p>Ten starts. Very little progress.</p>
          </div>

          <div class="focus-shift-arrow">→</div>

          <div class="focus-shift-side clear-side">
            <span>◎</span>
            <small>ONE CLEAR DIRECTION</small>
            <strong>Focused progress</strong>
            <p>A few priorities. Full attention.</p>
          </div>

        </div>


        <div class="focus-final-question">
          <small>BEFORE SAYING YES AGAIN...</small>

          <p>
            Will this move my current priorities forward,
            or only pull my attention away?
          </p>
        </div>


        <p>
          The goal isn’t to do everything.
        </p>

        <p>
          The goal is to do a few things well, build confidence
          and then move to the next three.
        </p>


        <div class="story-finish focus-finish">
          <span>◎</span>

          <p>
            Slow down. Prioritise. Focus.
          </p>

          <strong>
            One meaningful step at a time. ♡
          </strong>
        </div>

      </div>


      <footer class="reader-footer">
        <button type="button" @click="$emit('back')">
          ← Back to all thoughts
        </button>

        <span>
          less rush,<br />
          more depth ♡
        </span>
      </footer>

    </section>

  </article>
</template>

<style scoped>
.focus-blog-hero {
  position: relative;
  min-height: 475px;
  overflow: hidden;
  background:
    radial-gradient(circle at 82% 18%, #ffe7a2 0 9%, transparent 23%),
    linear-gradient(145deg, #dcefff, #e5ddff 36%, #ffdce9 68%, #ffe6bd);
}

.focus-blog-spark {
  position: absolute;
  z-index: 5;
  color: #8e74bd;
  font-size: 24px;
}

.focus-spark-one {
  top: 42px;
  left: 44px;
}

.focus-spark-two {
  top: 93px;
  left: 91px;
  color: #e66d9d;
}

.focus-orbit {
  position: absolute;
  border: 2px dashed rgba(111, 87, 179, 0.22);
  border-radius: 50%;
}

.orbit-large {
  top: 55px;
  right: 58px;
  width: 245px;
  height: 245px;
  animation: focus-spin 30s linear infinite;
}

.orbit-small {
  top: 91px;
  right: 94px;
  width: 173px;
  height: 173px;
  border-color: rgba(236, 103, 157, 0.27);
  animation: focus-spin 19s linear infinite reverse;
}

.focus-target {
  position: absolute;
  top: 128px;
  right: 129px;
  z-index: 4;
  width: 105px;
  height: 105px;
  border-radius: 37px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: white;
  background: linear-gradient(145deg, #7360bf, #d9689e);
  box-shadow: 0 18px 36px rgba(98, 74, 147, 0.23);
  transform: rotate(5deg);
}

.focus-target span {
  font-family: "Patrick Hand", cursive;
  font-size: 34px;
  line-height: 1;
}

.focus-target small {
  margin-top: 5px;
  font-size: 7px;
}

.focus-question-card {
  position: absolute;
  left: 42px;
  bottom: 35px;
  z-index: 8;
  width: 350px;
  padding: 23px;
  border: 1px solid rgba(73, 56, 96, 0.1);
  border-radius: 19px;
  background: rgba(255, 255, 255, 0.87);
  box-shadow: 0 18px 38px rgba(62, 48, 91, 0.11);
  backdrop-filter: blur(13px);
  transform: rotate(-1.5deg);
}

.focus-question-card > small,
.focus-human-question small,
.three-rule small,
.idea-note small,
.focus-shift-side small,
.focus-final-question small {
  color: #8975aa;
  font-family: "DM Mono", monospace;
  font-size: 6px;
  letter-spacing: 0.8px;
}

.focus-question-card > p {
  margin: 8px 0 14px;
  color: #504757;
  font-family: "Patrick Hand", cursive;
  font-size: 18px;
  line-height: 1.12;
}

.priority-options {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 7px;
}

.priority-options button {
  padding: 8px;
  border: 1px solid #ded7e5;
  border-radius: 9px;
  display: flex;
  align-items: center;
  gap: 7px;
  color: #6b6472;
  background: white;
  font-size: 7px;
  text-align: left;
}

.priority-options button > span {
  width: 17px;
  height: 17px;
  flex: 0 0 auto;
  border-radius: 50%;
  display: grid;
  place-items: center;
  color: #816ab2;
  background: #eee9ff;
  font-size: 8px;
}

.priority-options button.selected {
  border-color: #8fb993;
  color: #58705b;
  background: #edf7eb;
}

.priority-options button.selected > span {
  color: white;
  background: #78ab7c;
}

.priority-options button.disabled {
  opacity: 0.42;
}

.priority-count {
  margin-top: 9px;
  color: #9991a0;
  font-size: 7px;
  text-align: right;
}

.focus-author {
  background: #7cad81;
}

.focus-human-question {
  margin: 29px 0;
  padding: 23px;
  border-radius: 15px;
  background: linear-gradient(135deg, #edf0ff, #ffe8f0);
}

.focus-human-question p {
  margin: 8px 0 0;
  color: #554b5c;
  font-family: "Patrick Hand", cursive;
  font-size: 19px;
  line-height: 1.16;
}

.focus-line {
  margin: 29px 0;
  padding: 22px;
  border-radius: 14px;
  display: flex;
  align-items: center;
  gap: 14px;
  background: #e8f4e6;
}

.focus-line > span {
  color: #6f9d73;
  font-size: 25px;
}

.focus-line p {
  margin: 0;
  color: #4f5e50;
  font-family: "Patrick Hand", cursive;
  font-size: 18px;
  line-height: 1.13;
}

.three-rule {
  margin: 28px 0;
  padding: 24px;
  border: 1px solid #ded7e6;
  border-radius: 17px;
  background: #fffafd;
}

.three-rule-title {
  margin-bottom: 13px;
  display: flex;
  align-items: center;
  gap: 13px;
}

.three-rule-title > span {
  width: 50px;
  height: 50px;
  flex: 0 0 auto;
  border-radius: 50%;
  display: grid;
  place-items: center;
  color: white;
  background: #7663c1;
  box-shadow: 3px 4px 0 #dcd4ff;
  font-family: "Patrick Hand", cursive;
  font-size: 27px;
}

.three-rule-title strong {
  display: block;
  margin-top: 4px;
  color: #403846;
  font-size: 12px;
}

.three-rule-item {
  padding: 14px 0;
  border-bottom: 1px dashed #ddd5e1;
  display: grid;
  grid-template-columns: 37px 1fr;
  gap: 10px;
}

.three-rule-item:last-child {
  border-bottom: 0;
  padding-bottom: 0;
}

.three-rule-item > span {
  color: #9077c1;
  font-family: "DM Mono", monospace;
  font-size: 8px;
}

.three-rule-item strong {
  display: block;
  color: #504854;
  font-size: 10px;
}

.three-rule-item p {
  margin: 4px 0 0;
  color: #837e88;
  font-size: 8px;
  line-height: 1.45;
}

.idea-note {
  position: relative;
  margin: 34px 0;
  padding: 29px 24px;
  background: #ffe7a8;
  box-shadow: 4px 6px 15px rgba(65, 53, 38, 0.09);
  text-align: center;
  transform: rotate(-1deg);
}

.idea-tape {
  position: absolute;
  top: -13px;
  left: calc(50% - 38px);
  width: 76px;
  height: 26px;
  background: rgba(202, 187, 239, 0.72);
  transform: rotate(3deg);
}

.idea-note p {
  margin: 9px 0 0;
  color: #5e4d57;
  font-family: "Patrick Hand", cursive;
  font-size: 20px;
  line-height: 1.1;
}

.focus-shift {
  margin: 29px 0;
  display: grid;
  grid-template-columns: 1fr 34px 1fr;
  align-items: center;
  gap: 8px;
}

.focus-shift-side {
  min-height: 142px;
  padding: 19px;
  border-radius: 14px;
}

.scattered-side {
  background: #ffeddf;
}

.clear-side {
  background: #e8f4e6;
}

.focus-shift-side > span {
  display: block;
  margin-bottom: 9px;
  color: #997083;
  font-size: 23px;
}

.clear-side > span {
  color: #6d9871;
}

.focus-shift-side strong {
  display: block;
  margin-top: 5px;
  color: #4b444e;
  font-size: 10px;
}

.focus-shift-side p {
  margin: 7px 0 0;
  color: #817a82;
  font-size: 8px;
  line-height: 1.45;
}

.focus-shift-arrow {
  color: #a093a5;
  text-align: center;
}

.focus-final-question {
  margin: 32px 0;
  padding: 27px;
  border-radius: 15px;
  color: white;
  background: linear-gradient(135deg, #6757ae, #9068b2 52%, #ca769d);
  box-shadow: 0 13px 27px rgba(95, 75, 132, 0.18);
  text-align: center;
}

.focus-final-question small {
  color: rgba(255, 255, 255, 0.7);
}

.focus-final-question p {
  margin: 9px 0 0;
  font-family: "Patrick Hand", cursive;
  font-size: 20px;
  line-height: 1.15;
}

.focus-finish {
  background: linear-gradient(135deg, #fff9e9, #eeeaff);
}

@keyframes focus-spin {
  to {
    transform: rotate(360deg);
  }
}

@media (max-width: 600px) {
  .focus-blog-hero {
    min-height: 510px;
  }

  .orbit-large {
    top: 28px;
    right: -25px;
    width: 190px;
    height: 190px;
  }

  .orbit-small {
    top: 58px;
    right: 5px;
    width: 130px;
    height: 130px;
  }

  .focus-target {
    top: 87px;
    right: 37px;
    width: 73px;
    height: 73px;
  }

  .focus-target span {
    font-size: 26px;
  }

  .focus-question-card {
    left: 16px;
    right: 16px;
    bottom: 23px;
    width: auto;
    padding: 18px;
  }

  .priority-options {
    grid-template-columns: 1fr;
  }

  .focus-shift {
    grid-template-columns: 1fr;
  }

  .focus-shift-side {
    min-height: auto;
  }

  .focus-shift-arrow {
    transform: rotate(90deg);
  }
}
</style>
