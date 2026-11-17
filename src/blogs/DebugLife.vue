<script setup>
import { ref } from "vue";

defineEmits(["back"]);

const selectedProblem = ref("");
const debugStarted = ref(false);

const selectProblem = (problem) => {
  selectedProblem.value = problem;
  debugStarted.value = true;
};
</script>

<template>
  <article class="reader debug-reader">

    <!-- =========================
         NAVIGATION
    ========================== -->

    <header class="reader-nav">

      <button
        type="button"
        aria-label="वापस जाएँ"
        @click="$emit('back')"
      >
        ←
      </button>

      <strong>
        little.log <span>♡</span>
      </strong>

      <button
        type="button"
        aria-label="सेव करें"
      >
        ♡
      </button>

    </header>


    <!-- =========================
         INTERACTIVE HERO
    ========================== -->

    <section class="debug-hero">

      <span class="debug-spark debug-spark-one">✦</span>
      <span class="debug-spark debug-spark-two">♡</span>

      <!-- Cute bug -->

      <div class="cute-bug">

        <span class="bug-antenna antenna-left"></span>
        <span class="bug-antenna antenna-right"></span>

        <div class="bug-head">
          <span class="bug-eye eye-one"></span>
          <span class="bug-eye eye-two"></span>
        </div>

        <div class="bug-body">
          <span class="bug-line"></span>
          <span class="bug-dot dot-one"></span>
          <span class="bug-dot dot-two"></span>
        </div>

        <span class="bug-leg leg-one"></span>
        <span class="bug-leg leg-two"></span>
        <span class="bug-leg leg-three"></span>
        <span class="bug-leg leg-four"></span>

      </div>


      <!-- Terminal -->

      <div class="debug-terminal">

        <div class="terminal-header">
          <div>
            <span></span>
            <span></span>
            <span></span>
          </div>

          <small>
            life.log
          </small>
        </div>

        <div class="terminal-body">

          <span class="terminal-muted">
            expected:
          </span>

          <strong>
            life = sorted :)
          </strong>

          <span class="terminal-muted">
            actual:
          </span>

          <strong class="terminal-error">
            yeh kya ho raha hai bhai? 😭
          </strong>

          <span class="terminal-cursor">
            _
          </span>

        </div>

      </div>


      <!-- Question -->

      <div class="debug-question-card">

        <small>
          आज का QUICK DEBUG
        </small>

        <p>
          अभी life में कौन-सा module
          expected output नहीं दे रहा?
        </p>

        <div class="debug-options">

          <button
            type="button"
            :class="{ selected: selectedProblem === 'focus' }"
            @click="selectProblem('focus')"
          >
            Focus 🧠
          </button>

          <button
            type="button"
            :class="{ selected: selectedProblem === 'sleep' }"
            @click="selectProblem('sleep')"
          >
            Sleep ☾
          </button>

          <button
            type="button"
            :class="{ selected: selectedProblem === 'career' }"
            @click="selectProblem('career')"
          >
            Career 💻
          </button>

          <button
            type="button"
            :class="{ selected: selectedProblem === 'routine' }"
            @click="selectProblem('routine')"
          >
            Routine ↻
          </button>

        </div>


        <div
          v-if="debugStarted"
          class="debug-response"
        >
          ठीक है। पूरी life मत तोड़ो।
          पहले बस इस module को देखते हैं. 🔍
        </div>

      </div>


      <p class="debug-hero-note">
        rebuild नहीं...<br />
        पहले debug. ♡
      </p>

    </section>


    <!-- =========================
         ARTICLE
    ========================== -->

    <section class="reader-content">

      <div class="reader-meta">

        <span class="debug-tag">
          Tech Therapy
        </span>

        <small>
          Day 11 · 3 min read
        </small>

      </div>


      <h1>
        Life को Rebuild नहीं,<br />
        Debug करो. 🐞
      </h1>


      <p class="reader-subtitle">
        हर गलत output का मतलब यह नहीं कि
        पूरा system खराब है।
      </p>


      <!-- AUTHOR -->

      <div class="author">

        <span class="author-circle debug-author">
          l
        </span>

        <div>
          <strong>
            by little.log
          </strong>

          <small>
            Tech Therapy · Day 11
          </small>
        </div>

        <div class="reactions">
          <span>♡ 341</span>
          <span>◯ 26</span>
        </div>

      </div>


      <!-- =========================
           STORY
      ========================== -->

      <div class="story">

        <p>
          कभी ऐसा होता है कि life का expected output
          कुछ और होता है...
        </p>

        <p>
          और actual output देखकर बस एक ही सवाल आता है:
        </p>


        <div class="output-card">

          <div class="output-line expected">

            <small>EXPECTED</small>

            <strong>
              सब smoothly चलेगा. ✨
            </strong>

          </div>


          <div class="output-arrow">
            ↓
          </div>


          <div class="output-line actual">

            <small>ACTUAL</small>

            <strong>
              भाई, ये क्या हो रहा है? 😭
            </strong>

          </div>

        </div>


        <p>
          Interview अच्छा नहीं गया।
        </p>

        <p>
          काम में motivation नहीं आ रहा।
        </p>

        <p>
          किसी के साथ equation अचानक खराब हो गई।
        </p>

        <p>
          या technically सब कुछ ठीक है...
          फिर भी अंदर से output सही नहीं लग रहा।
        </p>


        <!-- HUMAN QUESTION -->

        <div class="debug-human-question">

          <small>
            और फिर हम क्या करते हैं?
          </small>

          <p>
            एक bug मिला और conclusion निकाल लिया:
            <strong>“शायद problem मैं ही हूँ।”</strong>
          </p>

        </div>


        <p>
          थोड़ा dramatic नहीं हो गया? 😭
        </p>


        <h2>
          Tech में तो हम ऐसा नहीं करते।
        </h2>


        <p>
          सोचो, तुमने एक पूरा application बनाया।
        </p>


        <div class="payment-example">

          <div>
            <small>EXPECTED</small>

            <strong class="success">
              Payment Successful ✓
            </strong>
          </div>

          <span>→</span>

          <div>
            <small>ACTUAL</small>

            <strong class="failure">
              Payment Failed ✕
            </strong>
          </div>

        </div>


        <p>
          क्या programmer बोलेगा:
        </p>


        <div class="funny-note">

          <span class="note-tape"></span>

          <p>
            “Bug आया है...
            चलो पूरा application delete करके
            फिर से बनाते हैं।” 😭
          </p>

        </div>


        <p>
          Hopefully नहीं।
        </p>


        <h2>
          Programmer पहले debug करता है. 🔍
        </h2>


        <div class="debug-flow">

          <div>
            <span>01</span>

            <p>
              Logs क्या बोल रहे हैं?
            </p>
          </div>

          <i>↓</i>

          <div>
            <span>02</span>

            <p>
              Issue reproduce हो रहा है?
            </p>
          </div>

          <i>↓</i>

          <div>
            <span>03</span>

            <p>
              Last change क्या था?
            </p>
          </div>

          <i>↓</i>

          <div>
            <span>04</span>

            <p>
              Exactly break कहाँ हुआ?
            </p>
          </div>

        </div>


        <!-- =========================
             LIFE DEBUGGING
        ========================== -->

        <h2>
          फिर life में debugging क्यों भूल जाते हैं?
        </h2>


        <div class="life-errors">

          <div class="life-error">

            <span>01</span>

            <div>
              <small>ONE BAD DAY</small>

              <p>
                “मेरी पूरी life ही खराब चल रही है।”
              </p>
            </div>

          </div>


          <div class="life-error">

            <span>02</span>

            <div>
              <small>ONE REJECTION</small>

              <p>
                “शायद मैं capable ही नहीं हूँ।”
              </p>
            </div>

          </div>


          <div class="life-error">

            <span>03</span>

            <div>
              <small>ONE UNPRODUCTIVE WEEK</small>

              <p>
                “मेरे अंदर discipline ही नहीं है।”
              </p>
            </div>

          </div>

        </div>


        <div class="single-test-note">

          <span>✦</span>

          <p>
            एक failing test case का मतलब
            पूरा application corrupt नहीं होता।
          </p>

        </div>


        <p>
          शायद पूरी life problem नहीं है।
        </p>

        <p>
          शायद सिर्फ एक module attention मांग रहा है।
        </p>


        <!-- =========================
             LOGS
        ========================== -->

        <h2>
          चलो logs देखते हैं.
        </h2>


        <div class="life-logs">

          <div class="log-window">

            <div class="log-title">
              sleep.log
            </div>

            <code>
              <span>sleep_hours = 5.2</span>
              <span>phone_before_bed = 75min</span>
              <span class="log-comment">// hmm... 👀</span>
            </code>

          </div>


          <div class="log-window">

            <div class="log-title">
              body.log
            </div>

            <code>
              <span>exercise = 0</span>
              <span>sunlight = laptop_brightness</span>
              <span class="log-comment">// interesting...</span>
            </code>

          </div>


          <div class="log-window">

            <div class="log-title">
              mind.log
            </div>

            <code>
              <span>work_stress = HIGH</span>
              <span>breaks = LOW</span>
              <span>comparison = VERY_HIGH</span>
            </code>

          </div>

        </div>


        <p>
          अब थोड़ा picture clear हो रहा है ना?
        </p>

        <p>
          शायद bug:
        </p>

        <div class="not-life-code">

          <code>
            life.exe
          </code>

          <span>नहीं है.</span>

        </div>

        <p>
          शायद कुछ छोटे components overloaded हैं।
        </p>


        <!-- =========================
             IDENTITY
        ========================== -->

        <h2>
          Problem को identity मत बनाओ.
        </h2>


        <div class="identity-compare">

          <div class="identity-bad">

            <small>❌ DON'T SAY</small>

            <p>
              “मैं failure हूँ।”
            </p>

          </div>


          <span class="identity-arrow">
            →
          </span>


          <div class="identity-good">

            <small>✓ DEBUG IT</small>

            <p>
              “मेरा एक attempt fail हुआ।”
            </p>

          </div>

        </div>


        <div class="identity-compare">

          <div class="identity-bad">

            <small>❌ DON'T SAY</small>

            <p>
              “मैं lazy हूँ।”
            </p>

          </div>


          <span class="identity-arrow">
            →
          </span>


          <div class="identity-good">

            <small>✓ DEBUG IT</small>

            <p>
              “कुछ दिनों से consistency नहीं रही।”
            </p>

          </div>

        </div>


        <p>
          फर्क छोटा लगता है।
        </p>

        <p>
          लेकिन पहला statement identity बन जाता है।
        </p>

        <p>
          दूसरा...
          <strong>debuggable.</strong>
        </p>


        <!-- =========================
             BUG REPORT
        ========================== -->

        <div class="bug-report">

          <span class="bug-report-tape"></span>

          <small>
            आज का TECH THERAPY EXPERIMENT
          </small>

          <h3>
            अपना bug report लिखो.
          </h3>


          <div class="bug-field">

            <label>
              Expected:
            </label>

            <span>
              __________________
            </span>

          </div>


          <div class="bug-field">

            <label>
              Actual:
            </label>

            <span>
              __________________
            </span>

          </div>


          <div class="bug-field">

            <label>
              कब शुरू हुआ?
            </label>

            <span>
              __________________
            </span>

          </div>


          <div class="bug-field">

            <label>
              Recently क्या बदला?
            </label>

            <span>
              __________________
            </span>

          </div>


          <div class="bug-field">

            <label>
              एक छोटा test:
            </label>

            <span>
              __________________
            </span>

          </div>


          <span class="bug-report-heart">
            ♡
          </span>

        </div>


        <p>
          बस।
        </p>

        <p>
          Life का Jira board मत बना देना. 😭
        </p>


        <!-- =========================
             SAMPLE DEBUG
        ========================== -->

        <h2>
          Example?
        </h2>


        <div class="sample-debug">

          <small>
            BUG: “आजकल focus नहीं हो रहा।”
          </small>


          <div>
            <span>Expected</span>
            <strong>45 min focused work</strong>
          </div>

          <div>
            <span>Actual</span>
            <strong>हर 6–7 min phone</strong>
          </div>

          <div>
            <span>Possible trigger</span>
            <strong>Notifications nearby</strong>
          </div>

          <div class="test-row">
            <span>Small test</span>
            <strong>
              Phone दूसरे room में,
              सिर्फ 30 min.
            </strong>
          </div>

        </div>


        <p>
          Test run करो।
        </p>

        <p>
          Improvement हुआ? Great.
        </p>

        <p>
          नहीं हुआ?
        </p>

        <p>
          वो भी useful है।
        </p>


        <div class="failed-experiment">

          <span>⌁</span>

          <p>
            Debugging में failed experiment भी
            <strong>information</strong> होता है।
          </p>

        </div>


        <!-- =========================
             ROLLBACK
        ========================== -->

        <h2>
          कभी-कभी rollback भी allowed है.
        </h2>


        <p>
          Latest version हमेशा best version नहीं होता।
        </p>


        <div class="rollback-card">

          <small>OLDER VERSION OF YOU</small>


          <div class="rollback-list">

            <span>✓ थोड़ा जल्दी सोते थे</span>
            <span>✓ walk पर जाते थे</span>
            <span>✓ Sunday को laptop बंद रहता था</span>
            <span>✓ सुबह phone तुरंत नहीं उठाते थे</span>

          </div>


          <button type="button">
            rollback();
          </button>

        </div>


        <p>
          हर progress forward नहीं होती।
        </p>

        <p>
          कभी-कभी healthy rollback भी debugging है।
        </p>


        <!-- =========================
             REBUILD?
        ========================== -->

        <h2>
          और हाँ... कभी rebuild भी करना पड़ता है.
        </h2>


        <p>
          Toxic job.
        </p>

        <p>
          Harmful relationship.
        </p>

        <p>
          Health की repeated warnings.
        </p>

        <p>
          Fundamentally wrong environment.
        </p>


        <div class="refactor-options">

          <div>
            <small>SMALL BUG</small>
            <code>debug();</code>
          </div>

          <div>
            <small>MESSY DESIGN</small>
            <code>refactor();</code>
          </div>

          <div>
            <small>WRONG SYSTEM</small>
            <code>rebuild();</code>
          </div>

          <div>
            <small>HARMFUL SYSTEM</small>
            <code>exit();</code>
          </div>

        </div>


        <div class="diagnosis-note">

          <span>☝</span>

          <p>
            लेकिन याद रखो:
            <strong>
              diagnosis पहले,
              destruction बाद में।
            </strong>
          </p>

        </div>


        <!-- =========================
             FINAL QUESTION
        ========================== -->

        <div class="debug-final-question">

          <small>
            आज का TECH THERAPY QUESTION ♡
          </small>

          <h3>
            अभी कौन-सी एक चीज expected output
            नहीं दे रही?
          </h3>


          <div class="final-tags">

            <span>Career?</span>
            <span>Sleep?</span>
            <span>Focus?</span>
            <span>Fitness?</span>
            <span>Relationship?</span>
            <span>Routine?</span>

          </div>


          <p>
            अब खुद से पूछो:
          </p>


          <strong>
            “क्या मुझे पूरी life बदलनी है...
            या बस एक bug debug करना है?”
          </strong>

        </div>


        <p>
          शायद answer surprisingly छोटा होगा।
        </p>

        <p>
          एक conversation.
        </p>

        <p>
          एक boundary.
        </p>

        <p>
          एक extra hour of sleep.
        </p>

        <p>
          एक habit.
        </p>

        <p>
          एक छोटा fix.
        </p>


        <!-- END -->

        <div class="story-finish debug-finish">

          <span>
            🐞
          </span>

          <p>
            You are not broken.
          </p>

          <strong>
            कुछ बस attention मांग रहा है।
          </strong>


          <div class="debug-ending-code">

            <code>
              observe();
            </code>

            <code>
              test();
            </code>

            <code>
              learn();
            </code>

            <code>
              adjust();
            </code>

            <code>
              runAgain(); ♡
            </code>

          </div>

        </div>


        <div class="very-end">

          Life को हर बार rebuild करने की
          जरूरत नहीं होती।

          <strong>
            कभी-कभी बस debug करना होता है. 🐞
          </strong>

        </div>

      </div>


      <!-- FOOTER -->

      <footer class="reader-footer">

        <button
          type="button"
          @click="$emit('back')"
        >
          ← सारे thoughts
        </button>

        <span>
          debug gently ♡
        </span>

      </footer>

    </section>

  </article>
</template>


<style scoped>

/* ==================================================
   HERO
================================================== */

.debug-hero {
  position: relative;

  min-height: 490px;

  overflow: hidden;

  background:
    radial-gradient(
      circle at 80% 15%,
      #fff0a5 0 9%,
      transparent 22%
    ),
    linear-gradient(
      145deg,
      #cef2ff,
      #dcdcff 35%,
      #ffdbe8 69%,
      #ffe9bc
    );
}

.debug-spark {
  position: absolute;

  z-index: 10;

  color: #8068ae;

  font-size: 24px;
}

.debug-spark-one {
  top: 40px;
  left: 40px;
}

.debug-spark-two {
  top: 90px;
  left: 90px;

  color: #e56a9b;
}


/* ==================================================
   BUG
================================================== */

.cute-bug {
  position: absolute;

  z-index: 7;

  right: 95px;
  top: 60px;

  width: 120px;
  height: 135px;
}

.bug-head {
  position: absolute;

  top: 18px;
  left: 37px;

  width: 50px;
  height: 45px;

  border: 3px solid #52455e;
  border-radius: 50%;

  background: #f092ae;
}

.bug-eye {
  position: absolute;

  top: 17px;

  width: 6px;
  height: 7px;

  border-radius: 50%;

  background: #3b3445;
}

.bug-eye.eye-one {
  left: 12px;
}

.bug-eye.eye-two {
  right: 12px;
}

.bug-body {
  position: absolute;

  top: 57px;
  left: 27px;

  width: 70px;
  height: 67px;

  border: 3px solid #52455e;
  border-radius: 50% 50% 45% 45%;

  background:
    linear-gradient(
      90deg,
      #ef769e,
      #dd6593
    );
}

.bug-line {
  position: absolute;

  left: 32px;

  width: 3px;
  height: 62px;

  background: #52455e;
}

.bug-dot {
  position: absolute;

  width: 10px;
  height: 10px;

  border-radius: 50%;

  background: #77475e;
}

.dot-one {
  top: 20px;
  left: 14px;
}

.dot-two {
  bottom: 17px;
  right: 14px;
}

.bug-antenna {
  position: absolute;

  top: 2px;

  width: 3px;
  height: 28px;

  background: #52455e;

  transform-origin: bottom;
}

.antenna-left {
  left: 47px;

  transform: rotate(-30deg);
}

.antenna-right {
  right: 47px;

  transform: rotate(30deg);
}

.bug-leg {
  position: absolute;

  width: 34px;
  height: 3px;

  background: #52455e;
}

.leg-one {
  top: 76px;
  left: 5px;

  transform: rotate(25deg);
}

.leg-two {
  top: 103px;
  left: 4px;

  transform: rotate(-20deg);
}

.leg-three {
  top: 76px;
  right: 2px;

  transform: rotate(-25deg);
}

.leg-four {
  top: 103px;
  right: 2px;

  transform: rotate(20deg);
}


/* ==================================================
   TERMINAL
================================================== */

.debug-terminal {
  position: absolute;

  right: 47px;
  bottom: 53px;

  width: 290px;

  overflow: hidden;

  border-radius: 16px;

  color: #e8e4ff;
  background: #25243e;

  box-shadow:
    0 17px 35px rgba(37,31,61,.18);

  transform: rotate(3deg);
}

.terminal-header {
  padding: 10px 13px;

  display: flex;
  align-items: center;

  background: #32304d;
}

.terminal-header > div {
  display: flex;

  gap: 5px;
}

.terminal-header span {
  width: 8px;
  height: 8px;

  border-radius: 50%;
}

.terminal-header span:first-child {
  background: #ef7377;
}

.terminal-header span:nth-child(2) {
  background: #efc65e;
}

.terminal-header span:nth-child(3) {
  background: #78be7b;
}

.terminal-header small {
  margin-left: auto;

  color: #aca6b9;

  font-family: "DM Mono";
  font-size: 7px;
}

.terminal-body {
  padding: 20px;

  display: flex;
  flex-direction: column;

  gap: 5px;

  font-family: "DM Mono";
  font-size: 9px;
}

.terminal-muted {
  color: #948fa5;
}

.terminal-error {
  color: #f28eb6;
}

.terminal-cursor {
  color: #ffda8c;

  animation: blink 1s infinite;
}


/* ==================================================
   HERO QUESTION
================================================== */

.debug-question-card {
  position: absolute;

  top: 52px;
  left: 42px;

  z-index: 20;

  width: 320px;

  padding: 22px;

  border: 1px solid rgba(67,54,90,.1);
  border-radius: 18px;

  background: rgba(255,255,255,.88);

  box-shadow:
    0 18px 38px rgba(62,48,91,.11);

  backdrop-filter: blur(12px);

  transform: rotate(-2deg);
}

.debug-question-card > small,
.debug-human-question small,
.life-error small,
.bug-report small,
.sample-debug > small,
.refactor-options small,
.debug-final-question small {
  color: #8875aa;

  font-family: "DM Mono";
  font-size: 6px;

  letter-spacing: .8px;
}

.debug-question-card > p {
  margin: 8px 0 14px;

  color: #504757;

  font-family: "Patrick Hand";
  font-size: 19px;

  line-height: 1.12;
}

.debug-options {
  display: grid;

  grid-template-columns: 1fr 1fr;

  gap: 7px;
}

.debug-options button {
  padding: 9px;

  border: 1px solid #ddd6e4;
  border-radius: 9px;

  color: #696171;
  background: white;

  font-size: 8px;
}

.debug-options button.selected {
  border-color: #9a87c2;

  color: #6952a2;
  background: #eee9ff;
}

.debug-response {
  margin-top: 9px;
  padding: 8px 10px;

  border-radius: 9px;

  color: #725368;
  background: #fff0f5;

  font-family: "Patrick Hand";
  font-size: 13px;
}

.debug-hero-note {
  position: absolute;

  right: 25px;
  top: 20px;

  color: #776079;

  font-family: "Patrick Hand";
  font-size: 17px;

  line-height: 1.05;

  text-align: right;

  transform: rotate(4deg);
}


/* ==================================================
   TAG
================================================== */

.debug-tag {
  color: #6955a8 !important;

  background: #eee8ff !important;
}

.debug-author {
  background: #7662bd;
}


/* ==================================================
   OUTPUT
================================================== */

.output-card {
  margin: 27px 0;

  border: 1px solid #ded8e5;
  border-radius: 15px;

  overflow: hidden;

  background: #fffafd;
}

.output-line {
  padding: 17px 20px;
}

.output-line small {
  display: block;

  margin-bottom: 5px;

  color: #91899b;

  font-family: "DM Mono";
  font-size: 6px;
}

.output-line strong {
  font-size: 11px;
}

.output-line.expected {
  background: #eaf5e8;
}

.output-line.actual {
  background: #fff0e4;
}

.output-arrow {
  padding: 4px;

  color: #a098a3;

  text-align: center;
}


/* ==================================================
   QUESTION
================================================== */

.debug-human-question {
  margin: 28px 0;
  padding: 23px;

  border-radius: 15px;

  background:
    linear-gradient(
      135deg,
      #e9e5ff,
      #ffe7ef
    );
}

.debug-human-question p {
  margin: 9px 0 0;

  color: #554b5c;

  font-family: "Patrick Hand";
  font-size: 19px;

  line-height: 1.15;
}


/* ==================================================
   PAYMENT
================================================== */

.payment-example {
  margin: 26px 0;

  display: grid;

  grid-template-columns: 1fr 30px 1fr;

  align-items: center;

  gap: 8px;
}

.payment-example > div {
  min-height: 95px;

  padding: 17px;

  border-radius: 13px;

  display: flex;
  flex-direction: column;

  justify-content: center;

  background: #f7f5fb;
}

.payment-example small {
  color: #99919e;

  font-family: "DM Mono";
  font-size: 6px;
}

.payment-example strong {
  margin-top: 6px;

  font-size: 9px;
}

.success {
  color: #59865f;
}

.failure {
  color: #bd6373;
}

.payment-example > span {
  color: #9c93a2;

  text-align: center;
}


/* ==================================================
   FUNNY NOTE
================================================== */

.funny-note {
  position: relative;

  margin: 29px 0;
  padding: 28px 22px;

  background: #ffe6a6;

  box-shadow:
    4px 6px 14px rgba(64,52,38,.09);

  text-align: center;

  transform: rotate(-1deg);
}

.note-tape {
  position: absolute;

  top: -13px;
  left: calc(50% - 38px);

  width: 76px;
  height: 26px;

  background: rgba(204,189,239,.72);

  transform: rotate(3deg);
}

.funny-note p {
  margin: 0;

  color: #5c4c54;

  font-family: "Patrick Hand";
  font-size: 19px;

  line-height: 1.13;
}


/* ==================================================
   DEBUG FLOW
================================================== */

.debug-flow {
  max-width: 420px;

  margin: 27px auto;

  display: flex;
  flex-direction: column;

  align-items: center;
}

.debug-flow > div {
  width: 100%;

  padding: 13px 16px;

  border: 1px solid #ded8e4;
  border-radius: 11px;

  display: grid;

  grid-template-columns: 30px 1fr;

  align-items: center;

  gap: 9px;

  background: white;
}

.debug-flow > div > span {
  color: #806ab0;

  font-family: "DM Mono";
  font-size: 7px;
}

.debug-flow p {
  margin: 0;

  color: #5e5964;

  font-size: 9px;
}

.debug-flow > i {
  padding: 5px;

  color: #b0a6b4;

  font-style: normal;
}


/* ==================================================
   ERRORS
================================================== */

.life-errors {
  margin: 26px 0;

  border: 1px solid #e0dae5;
  border-radius: 15px;

  overflow: hidden;
}

.life-error {
  padding: 16px 18px;

  border-bottom: 1px dashed #dbd5df;

  display: grid;

  grid-template-columns: 37px 1fr;

  gap: 9px;
}

.life-error:last-child {
  border: 0;
}

.life-error > span {
  color: #8c75b9;

  font-family: "DM Mono";
  font-size: 8px;
}

.life-error p {
  margin: 5px 0 0;

  color: #5a525e;

  font-family: "Patrick Hand";
  font-size: 15px;
}

.single-test-note {
  margin: 28px 0;
  padding: 22px;

  border-radius: 14px;

  display: flex;
  align-items: center;

  gap: 13px;

  background: #e8f4e5;
}

.single-test-note > span {
  color: #719c72;

  font-size: 25px;
}

.single-test-note p {
  margin: 0;

  color: #4f5d50;

  font-family: "Patrick Hand";
  font-size: 18px;
}


/* ==================================================
   LOGS
================================================== */

.life-logs {
  margin: 27px 0;

  display: grid;

  gap: 10px;
}

.log-window {
  overflow: hidden;

  border-radius: 12px;

  color: #e9e4fb;
  background: #282640;
}

.log-title {
  padding: 8px 12px;

  color: #aca6b8;
  background: #34314c;

  font-family: "DM Mono";
  font-size: 7px;
}

.log-window code {
  padding: 15px;

  display: flex;
  flex-direction: column;

  gap: 5px;

  font-family: "DM Mono";
  font-size: 8px;
}

.log-comment {
  color: #f19aba;
}

.not-life-code {
  width: fit-content;

  margin: 23px auto;

  display: flex;
  align-items: center;

  gap: 10px;
}

.not-life-code code {
  padding: 9px 14px;

  border-radius: 9px;

  color: #d5caff;
  background: #282640;

  font-family: "DM Mono";
  font-size: 9px;
}


/* ==================================================
   IDENTITY
================================================== */

.identity-compare {
  margin: 12px 0;

  display: grid;

  grid-template-columns: 1fr 30px 1fr;

  align-items: center;

  gap: 8px;
}

.identity-bad,
.identity-good {
  min-height: 100px;

  padding: 16px;

  border-radius: 13px;
}

.identity-bad {
  background: #fff0e7;
}

.identity-good {
  background: #e9f5e7;
}

.identity-compare small {
  color: #958b92;

  font-family: "DM Mono";
  font-size: 6px;
}

.identity-compare p {
  margin: 7px 0 0;

  color: #5e555d;

  font-family: "Patrick Hand";
  font-size: 16px;

  line-height: 1.1;
}

.identity-arrow {
  color: #a096a4;

  text-align: center;
}


/* ==================================================
   BUG REPORT
================================================== */

.bug-report {
  position: relative;

  margin: 32px 0;
  padding: 28px;

  border: 1px solid #ddd6e3;

  background:
    repeating-linear-gradient(
      #fffdf8,
      #fffdf8 30px,
      #eee6ee 31px
    );

  box-shadow:
    4px 6px 14px rgba(65,54,70,.08);

  transform: rotate(-.5deg);
}

.bug-report-tape {
  position: absolute;

  top: -13px;
  left: calc(50% - 40px);

  width: 80px;
  height: 26px;

  background: rgba(255,218,132,.72);
}

.bug-report h3 {
  margin: 7px 0 19px;

  color: #4e4555;

  font-family: "Patrick Hand";
  font-size: 23px;
  font-weight: 500;
}

.bug-field {
  margin: 13px 0;

  display: grid;

  grid-template-columns: 130px 1fr;

  gap: 10px;
}

.bug-field label {
  color: #665d69;

  font-size: 9px;
}

.bug-field span {
  color: #aaa3aa;

  font-family: "DM Mono";
  font-size: 8px;
}

.bug-report-heart {
  position: absolute;

  right: 14px;
  bottom: 8px;

  color: #dc6897;

  font-size: 21px;
}


/* ==================================================
   SAMPLE
================================================== */

.sample-debug {
  margin: 27px 0;

  overflow: hidden;

  border: 1px solid #ddd7e4;
  border-radius: 15px;

  background: #fffafd;
}

.sample-debug > small {
  display: block;

  padding: 13px 16px;

  color: #745f98;
  background: #eee9ff;
}

.sample-debug > div {
  padding: 13px 16px;

  border-top: 1px dashed #ddd6e0;

  display: grid;

  grid-template-columns: 105px 1fr;

  gap: 10px;
}

.sample-debug > div > span {
  color: #918b97;

  font-size: 7px;
}

.sample-debug strong {
  color: #57515d;

  font-size: 8px;
}

.test-row {
  background: #eaf5e7;
}


/* ==================================================
   FAILED TEST
================================================== */

.failed-experiment {
  margin: 27px 0;
  padding: 22px;

  border-radius: 14px;

  display: flex;
  align-items: center;

  gap: 13px;

  background: #e8eaff;
}

.failed-experiment > span {
  color: #7766b0;

  font-size: 28px;
}

.failed-experiment p {
  margin: 0;

  color: #524f66;

  font-family: "Patrick Hand";
  font-size: 18px;
}


/* ==================================================
   ROLLBACK
================================================== */

.rollback-card {
  margin: 27px 0;
  padding: 23px;

  border-radius: 15px;

  background:
    linear-gradient(
      145deg,
      #eaf4e8,
      #f5fbf2
    );
}

.rollback-card > small {
  color: #738d73;

  font-family: "DM Mono";
  font-size: 6px;
}

.rollback-list {
  margin: 13px 0;

  display: flex;
  flex-direction: column;

  gap: 8px;

  color: #59635b;

  font-size: 9px;
}

.rollback-card button {
  padding: 8px 12px;

  border: 0;
  border-radius: 8px;

  color: #e9e4fb;
  background: #292740;

  font-family: "DM Mono";
  font-size: 8px;
}


/* ==================================================
   REFACTOR
================================================== */

.refactor-options {
  margin: 26px 0;

  display: grid;

  grid-template-columns: 1fr 1fr;

  gap: 9px;
}

.refactor-options > div {
  padding: 18px;

  border-radius: 13px;

  background: #f5f1fb;
}

.refactor-options code {
  display: block;

  margin-top: 8px;

  color: #6c58a1;

  font-family: "DM Mono";
  font-size: 9px;
}

.diagnosis-note {
  margin: 27px 0;
  padding: 22px;

  border-radius: 14px;

  display: flex;
  align-items: center;

  gap: 13px;

  background: #fff0db;
}

.diagnosis-note > span {
  font-size: 25px;
}

.diagnosis-note p {
  margin: 0;

  color: #615158;

  font-family: "Patrick Hand";
  font-size: 18px;

  line-height: 1.15;
}


/* ==================================================
   FINAL
================================================== */

.debug-final-question {
  margin: 32px 0;
  padding: 27px;

  border-radius: 16px;

  color: white;

  background:
    linear-gradient(
      135deg,
      #625eac,
      #8069ad 54%,
      #bd719c
    );

  text-align: center;
}

.debug-final-question > small {
  color: rgba(255,255,255,.65);
}

.debug-final-question h3 {
  margin: 9px auto 16px;

  max-width: 440px;

  font-family: "Patrick Hand";
  font-size: 23px;
  font-weight: 500;

  line-height: 1.1;
}

.final-tags {
  margin-bottom: 17px;

  display: flex;
  flex-wrap: wrap;

  justify-content: center;

  gap: 6px;
}

.final-tags span {
  padding: 6px 9px;

  border-radius: 50px;

  color: #5e5570;
  background: rgba(255,255,255,.88);

  font-size: 7px;
}

.debug-final-question p {
  margin: 0 0 8px;

  color: rgba(255,255,255,.75);

  font-size: 8px;
}

.debug-final-question > strong {
  display: block;

  font-family: "Patrick Hand";
  font-size: 19px;

  line-height: 1.15;
}

.debug-finish {
  background:
    linear-gradient(
      135deg,
      #fff8e6,
      #eeeaff
    );
}

.debug-ending-code {
  margin-top: 17px;

  display: flex;
  flex-wrap: wrap;

  justify-content: center;

  gap: 6px;
}

.debug-ending-code code {
  padding: 6px 8px;

  border-radius: 7px;

  color: #dcd4ff;
  background: #2a2842;

  font-family: "DM Mono";
  font-size: 6px;
}

.very-end {
  margin: 24px 0 0;

  padding: 22px;

  border-left: 4px solid #806ab7;

  color: #675e69;
  background: #f7f3fb;

  font-family: "Patrick Hand";
  font-size: 18px;

  line-height: 1.2;
}

.very-end strong {
  display: block;

  margin-top: 6px;

  color: #514456;
}


/* ==================================================
   MOBILE
================================================== */

@media (max-width: 600px) {

  .debug-hero {
    min-height: 510px;
  }

  .debug-question-card {
    top: 25px;
    left: 16px;
    right: 16px;

    width: auto;

    padding: 18px;
  }

  .debug-question-card > p {
    font-size: 16px;
  }

  .cute-bug {
    top: 215px;
    right: 20px;

    transform: scale(.72);

    transform-origin: top right;
  }

  .debug-terminal {
    left: 16px;
    right: 16px;
    bottom: 24px;

    width: auto;

    transform: rotate(1deg);
  }

  .debug-hero-note {
    display: none;
  }

  .identity-compare {
    grid-template-columns: 1fr;
  }

  .identity-arrow {
    transform: rotate(90deg);
  }

  .bug-field {
    grid-template-columns: 105px 1fr;
  }

  .refactor-options {
    grid-template-columns: 1fr 1fr;
  }

}


/* ==================================================
   CURSOR
================================================== */

@keyframes blink {

  0%,
  50% {
    opacity: 1;
  }

  51%,
  100% {
    opacity: 0;
  }

}
</style>
