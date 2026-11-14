<script setup>
import { ref } from "vue";

const isReading = ref(false);

const openBlog = () => {
  isReading.value = true;
  window.scrollTo({ top: 0, behavior: "smooth" });
};

const closeBlog = () => {
  isReading.value = false;
  window.scrollTo({ top: 0, behavior: "smooth" });
};
</script>

<template>
  <main class="app">
    <nav class="navbar">
      <button class="brand" @click="closeBlog">
        <span class="brand-icon">↻</span>
        <span>Soft Loops</span>
      </button>

      <span class="nav-note">Thoughts about life, one loop at a time.</span>
    </nav>

    <!-- HOME PAGE -->
    <section v-if="!isReading" class="home-page">
      <div class="floating-shape shape-one"></div>
      <div class="floating-shape shape-two"></div>
      <div class="floating-shape shape-three"></div>

      <header class="hero">
        <span class="eyebrow">A small corner for thoughtful minds</span>

        <h1>
          Some loops repeat<br />
          until we understand them.
        </h1>

        <p class="hero-description">
          A gentle blog about patterns, pauses, growth and the base
          conditions that help us move forward.
        </p>

        <div class="scroll-hint">
          <span>Today’s reflection</span>
          <span class="arrow">↓</span>
        </div>
      </header>

      <section class="featured-section">
        <article class="blog-card" @click="openBlog">
          <div class="card-visual">
            <div class="loop-art">
              <span class="loop loop-one"></span>
              <span class="loop loop-two"></span>
              <span class="loop loop-three"></span>
              <div class="center-message">
                <span>repeat</span>
                <strong>↻</strong>
                <span>reflect</span>
              </div>
            </div>
          </div>

          <div class="card-content">
            <div class="post-meta">
              <span class="category">Life Notes</span>
              <span>5 min read</span>
            </div>

            <h2>Finding the Base Condition</h2>

            <p>
              Sometimes life feels like recursion. We repeat the same routines,
              thoughts and situations without knowing when or how to stop.
            </p>

            <button class="read-button" @click.stop="openBlog">
              Read this reflection
              <span>→</span>
            </button>
          </div>
        </article>
      </section>

      <footer class="home-footer">
        <span>Made with calm thoughts</span>
        <span class="tiny-flower">✿</span>
        <span>and a little recursion</span>
      </footer>
    </section>

    <!-- BLOG READING PAGE -->
    <section v-else class="article-page">
      <button class="back-button" @click="closeBlog">
        <span>←</span>
        Back to home
      </button>

      <article class="article">
        <header class="article-header">
          <div class="article-tag">Life Notes · 5 min read</div>

          <h1>Finding the Base Condition</h1>

          <p class="article-introduction">
            Maybe we are not always stuck. Maybe we are simply repeating the
            same function while waiting to discover what can help us return.
          </p>

          <div class="author-row">
            <div class="author-avatar">↻</div>
            <div>
              <strong>Soft Loops</strong>
              <span>A reflection on recursion and real life</span>
            </div>
          </div>
        </header>

        <div class="article-divider">
          <span>✿</span>
        </div>

        <div class="article-content">
          <p class="opening-paragraph">
            In programming, recursion happens when a function calls itself.
            Without a base condition, that function continues calling itself
            until the system runs out of space.
          </p>

          <p>
            Life can sometimes feel surprisingly similar.
          </p>

          <p>
            We wake up, follow the same routine, carry the same thoughts and
            react to situations in the same familiar way. The days keep
            repeating. We remain inside the loop, hoping that the next
            iteration will somehow feel different.
          </p>

          <blockquote>
            “When life begins to feel recursive, do not only ask why the loop
            exists. Ask what your base condition could be.”
          </blockquote>

          <h2>What is your base condition?</h2>

          <p>
            A base condition is the point where recursion stops. In real life,
            it might be a decision, an honest conversation, a boundary, a
            change in routine or simply accepting that something is no longer
            working.
          </p>

          <p>
            If a situation is draining your energy, increasing your frustration
            and slowly burning you out, you may not need another iteration.
            You may need a base condition.
          </p>

          <div class="reflection-box">
            <span class="reflection-icon">☁</span>

            <div>
              <h3>A small pause</h3>
              <p>
                Ask yourself: “What needs to become true for me to leave this
                loop?”
              </p>
            </div>
          </div>

          <h2>Not every recursion is bad</h2>

          <p>
            Some loops are worth continuing. Practising a skill, caring for
            someone, building a meaningful habit or returning to something that
            brings peace can add value with every repetition.
          </p>

          <p>
            When each iteration helps you learn, heal or grow, you may not want
            to reach the base condition too quickly.
          </p>

          <p>
            Still, it is important to know that the base condition exists. Even
            a beautiful loop should have an exit available. Knowing that you
            can stop allows you to continue by choice instead of continuing
            because you feel trapped.
          </p>

          <div class="comparison">
            <div class="comparison-card growing">
              <span class="comparison-emoji">🌱</span>
              <h3>A growing loop</h3>
              <p>
                Each repetition adds knowledge, strength, connection or peace.
              </p>
              <span class="loop-result">Continue with awareness</span>
            </div>

            <div class="comparison-card draining">
              <span class="comparison-emoji">🍂</span>
              <h3>A draining loop</h3>
              <p>
                Each repetition reduces your energy, confidence or happiness.
              </p>
              <span class="loop-result">Find the base condition</span>
            </div>
          </div>

          <h2>Pause before the next call</h2>

          <p>
            Before repeating the same response, decision or routine again,
            pause for a moment.
          </p>

          <ul class="questions">
            <li>Is this loop still adding value to my life?</li>
            <li>Am I continuing because I choose to, or because I feel stuck?</li>
            <li>What is decreasing with every repetition?</li>
            <li>What condition would allow me to exit peacefully?</li>
          </ul>

          <p>
            You do not have to escape every loop. You only need to notice what
            each iteration is doing to you.
          </p>

          <p>
            Continue the recursions that help you grow. For the ones that leave
            you tired, frustrated and smaller than before, define your base
            condition and allow yourself to return.
          </p>

          <div class="final-thought">
            <span>↻</span>
            <p>
              Some patterns deserve another iteration.<br />
              Others are waiting for you to finally say,
              <strong>“This is where I stop.”</strong>
            </p>
          </div>
        </div>

        <footer class="article-footer">
          <span>Thank you for spending a quiet moment here.</span>

          <button @click="closeBlog">
            Read again from the beginning
            <span>↑</span>
          </button>
        </footer>
      </article>
    </section>
  </main>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Playfair+Display:ital,wght@0,600;1,500&display=swap");

:root {
  font-family: "DM Sans", sans-serif;
  color: #433b47;
  background: #fffaf7;
  font-synthesis: none;
  text-rendering: optimizeLegibility;
}

* {
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  min-width: 320px;
  min-height: 100vh;
  margin: 0;
  background:
    radial-gradient(circle at 10% 10%, #fce8eb 0, transparent 26%),
    radial-gradient(circle at 90% 30%, #e7f2e5 0, transparent 23%),
    #fffaf7;
}

button {
  font: inherit;
}

.app {
  min-height: 100vh;
  overflow: hidden;
}

.navbar {
  position: relative;
  z-index: 10;
  width: min(1180px, calc(100% - 40px));
  margin: 0 auto;
  padding: 28px 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.brand {
  border: 0;
  padding: 0;
  display: flex;
  align-items: center;
  gap: 10px;
  color: #554654;
  background: transparent;
  font-size: 19px;
  font-weight: 600;
  cursor: pointer;
}

.brand-icon {
  width: 38px;
  height: 38px;
  display: grid;
  place-items: center;
  border: 1px solid #d8bdc5;
  border-radius: 50%;
  color: #b76e7e;
  background: rgba(255, 255, 255, 0.62);
  font-size: 23px;
}

.nav-note {
  color: #93858c;
  font-size: 13px;
}

/* Home */

.home-page {
  position: relative;
}

.hero {
  max-width: 820px;
  min-height: 570px;
  margin: 0 auto;
  padding: 105px 24px 50px;
  text-align: center;
}

.eyebrow {
  display: inline-flex;
  padding: 9px 17px;
  border: 1px solid #ead5da;
  border-radius: 100px;
  color: #a15f70;
  background: rgba(255, 255, 255, 0.58);
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 1.25px;
  text-transform: uppercase;
}

.hero h1,
.article-header h1 {
  margin: 28px 0 22px;
  color: #4f424d;
  font-family: "Playfair Display", serif;
  font-size: clamp(48px, 7vw, 78px);
  font-weight: 600;
  line-height: 1.06;
  letter-spacing: -2px;
}

.hero-description {
  max-width: 620px;
  margin: 0 auto;
  color: #81747b;
  font-size: 18px;
  line-height: 1.8;
}

.scroll-hint {
  margin-top: 65px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  color: #a28e96;
  font-size: 12px;
  letter-spacing: 1px;
  text-transform: uppercase;
}

.arrow {
  color: #b76e7e;
  font-size: 20px;
  animation: bounce 1.8s infinite;
}

.floating-shape {
  position: absolute;
  border-radius: 50%;
  pointer-events: none;
  filter: blur(1px);
}

.shape-one {
  top: 90px;
  left: 7%;
  width: 110px;
  height: 110px;
  border: 1px dashed #e5c5cd;
  animation: float 7s ease-in-out infinite;
}

.shape-two {
  top: 350px;
  right: 8%;
  width: 42px;
  height: 42px;
  background: #e5f0df;
  animation: float 5s ease-in-out infinite reverse;
}

.shape-three {
  top: 160px;
  right: 20%;
  width: 18px;
  height: 18px;
  background: #f3d8b9;
}

.featured-section {
  width: min(1000px, calc(100% - 40px));
  margin: 0 auto;
  padding-bottom: 100px;
}

.blog-card {
  display: grid;
  grid-template-columns: 0.9fr 1.1fr;
  overflow: hidden;
  border: 1px solid #eedfe2;
  border-radius: 32px;
  background: rgba(255, 255, 255, 0.78);
  box-shadow: 0 25px 70px rgba(94, 65, 76, 0.1);
  cursor: pointer;
  transition:
    transform 0.35s ease,
    box-shadow 0.35s ease;
}

.blog-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 32px 80px rgba(94, 65, 76, 0.15);
}

.card-visual {
  min-height: 430px;
  padding: 45px;
  display: grid;
  place-items: center;
  background: #f4e5e8;
}

.loop-art {
  position: relative;
  width: 275px;
  height: 275px;
}

.loop {
  position: absolute;
  inset: 0;
  border: 2px solid rgba(174, 105, 122, 0.35);
  border-radius: 43% 57% 48% 52% / 56% 43% 57% 44%;
}

.loop-one {
  animation: rotateLoop 14s linear infinite;
}

.loop-two {
  inset: 30px;
  border-color: rgba(174, 105, 122, 0.5);
  animation: rotateLoop 10s linear infinite reverse;
}

.loop-three {
  inset: 60px;
  border-color: rgba(174, 105, 122, 0.7);
  animation: rotateLoop 8s linear infinite;
}

.center-message {
  position: absolute;
  inset: 85px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  color: #9c6673;
  background: rgba(255, 250, 247, 0.85);
  font-size: 10px;
  letter-spacing: 1px;
  text-transform: uppercase;
}

.center-message strong {
  margin: 2px 0;
  font-size: 28px;
}

.card-content {
  padding: 70px 65px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.post-meta {
  display: flex;
  align-items: center;
  gap: 16px;
  color: #998b91;
  font-size: 12px;
}

.category {
  padding: 7px 12px;
  border-radius: 100px;
  color: #94606d;
  background: #f6e8eb;
  font-weight: 600;
}

.card-content h2 {
  margin: 25px 0 18px;
  color: #51444e;
  font-family: "Playfair Display", serif;
  font-size: 42px;
  line-height: 1.12;
}

.card-content p {
  margin: 0;
  color: #7b6e74;
  font-size: 16px;
  line-height: 1.8;
}

.read-button {
  width: fit-content;
  margin-top: 32px;
  padding: 0 0 8px;
  border: 0;
  border-bottom: 1px solid #c9919e;
  display: flex;
  align-items: center;
  gap: 16px;
  color: #995f6d;
  background: transparent;
  font-weight: 600;
  cursor: pointer;
}

.read-button span {
  transition: transform 0.25s ease;
}

.read-button:hover span {
  transform: translateX(6px);
}

.home-footer {
  padding: 35px 20px 45px;
  display: flex;
  justify-content: center;
  gap: 10px;
  color: #a09298;
  font-size: 12px;
}

.tiny-flower {
  color: #bf7c8c;
}

/* Article */

.article-page {
  width: min(880px, calc(100% - 40px));
  margin: 0 auto;
  padding: 55px 0 90px;
}

.back-button {
  margin-bottom: 55px;
  padding: 10px 0;
  border: 0;
  display: inline-flex;
  align-items: center;
  gap: 12px;
  color: #96747e;
  background: transparent;
  font-weight: 600;
  cursor: pointer;
}

.back-button span {
  font-size: 21px;
  transition: transform 0.25s ease;
}

.back-button:hover span {
  transform: translateX(-5px);
}

.article {
  overflow: hidden;
  border: 1px solid #efe1e4;
  border-radius: 35px;
  background: rgba(255, 255, 255, 0.86);
  box-shadow: 0 30px 90px rgba(93, 65, 75, 0.09);
}

.article-header {
  padding: 90px 90px 40px;
  text-align: center;
}

.article-tag {
  color: #a66e7b;
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 1.5px;
  text-transform: uppercase;
}

.article-header h1 {
  margin: 23px auto;
  font-size: clamp(48px, 7vw, 72px);
}

.article-introduction {
  max-width: 650px;
  margin: 0 auto;
  color: #796c72;
  font-family: "Playfair Display", serif;
  font-size: 21px;
  font-style: italic;
  line-height: 1.7;
}

.author-row {
  margin-top: 35px;
  display: inline-flex;
  align-items: center;
  gap: 13px;
  text-align: left;
}

.author-avatar {
  width: 45px;
  height: 45px;
  display: grid;
  place-items: center;
  border-radius: 50%;
  color: #9b6572;
  background: #f5e4e8;
  font-size: 24px;
}

.author-row strong,
.author-row span {
  display: block;
}

.author-row strong {
  color: #574b51;
  font-size: 13px;
}

.author-row span {
  margin-top: 4px;
  color: #a09298;
  font-size: 11px;
}

.article-divider {
  display: flex;
  align-items: center;
  gap: 15px;
  color: #c98797;
}

.article-divider::before,
.article-divider::after {
  height: 1px;
  flex: 1;
  background: #f0e4e6;
  content: "";
}

.article-content {
  padding: 45px 100px 80px;
  color: #5f5359;
}

.article-content p {
  margin: 0 0 25px;
  font-size: 17px;
  line-height: 1.95;
}

.article-content .opening-paragraph::first-letter {
  padding-right: 7px;
  float: left;
  color: #a76273;
  font-family: "Playfair Display", serif;
  font-size: 62px;
  line-height: 0.9;
}

.article-content h2 {
  margin: 55px 0 20px;
  color: #53454d;
  font-family: "Playfair Display", serif;
  font-size: 32px;
}

blockquote {
  position: relative;
  margin: 50px 0;
  padding: 38px 45px;
  border: 0;
  border-radius: 22px;
  color: #765964;
  background: #f8eaed;
  font-family: "Playfair Display", serif;
  font-size: 24px;
  font-style: italic;
  line-height: 1.65;
  text-align: center;
}

.reflection-box {
  margin: 45px 0;
  padding: 28px 30px;
  border: 1px solid #dce8d8;
  border-radius: 20px;
  display: flex;
  gap: 20px;
  background: #f1f6ee;
}

.reflection-icon {
  font-size: 32px;
}

.reflection-box h3 {
  margin: 0 0 8px;
  color: #5d7257;
  font-family: "Playfair Display", serif;
  font-size: 21px;
}

.reflection-box p {
  margin: 0;
  color: #6f7c6b;
  font-size: 15px;
}

.comparison {
  margin: 45px 0;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 18px;
}

.comparison-card {
  padding: 32px 26px;
  border-radius: 22px;
}

.comparison-card.growing {
  border: 1px solid #dce8d7;
  background: #f0f5ed;
}

.comparison-card.draining {
  border: 1px solid #efdfd3;
  background: #fbf1e9;
}

.comparison-emoji {
  font-size: 30px;
}

.comparison-card h3 {
  margin: 15px 0 10px;
  color: #55494f;
  font-family: "Playfair Display", serif;
  font-size: 21px;
}

.comparison-card p {
  margin: 0 0 20px;
  font-size: 14px;
  line-height: 1.7;
}

.loop-result {
  color: #92717a;
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 0.7px;
  text-transform: uppercase;
}

.questions {
  margin: 30px 0 35px;
  padding: 0;
  list-style: none;
}

.questions li {
  position: relative;
  margin-bottom: 13px;
  padding: 17px 20px 17px 48px;
  border: 1px solid #eee2e4;
  border-radius: 14px;
  color: #665960;
  background: #fffaf9;
  line-height: 1.6;
}

.questions li::before {
  position: absolute;
  top: 17px;
  left: 20px;
  color: #bd7889;
  content: "↻";
}

.final-thought {
  margin-top: 60px;
  padding: 46px;
  border-radius: 25px;
  color: #694d57;
  background: #f3dfe4;
  text-align: center;
}

.final-thought > span {
  display: block;
  margin-bottom: 15px;
  font-size: 40px;
}

.final-thought p {
  margin: 0;
  font-family: "Playfair Display", serif;
  font-size: 23px;
  line-height: 1.7;
}

.article-footer {
  padding: 30px 45px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  color: #a19097;
  background: #fff8f6;
  font-size: 12px;
}

.article-footer button {
  padding: 10px 0;
  border: 0;
  display: flex;
  gap: 10px;
  color: #9a6170;
  background: transparent;
  font-weight: 600;
  cursor: pointer;
}

@keyframes rotateLoop {
  to {
    transform: rotate(360deg);
  }
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0) rotate(0);
  }

  50% {
    transform: translateY(-18px) rotate(12deg);
  }
}

@keyframes bounce {
  0%,
  100% {
    transform: translateY(0);
  }

  50% {
    transform: translateY(6px);
  }
}

@media (max-width: 780px) {
  .nav-note,
  .floating-shape {
    display: none;
  }

  .hero {
    min-height: 510px;
    padding-top: 80px;
  }

  .hero h1 {
    font-size: 48px;
  }

  .blog-card {
    grid-template-columns: 1fr;
  }

  .card-visual {
    min-height: 320px;
  }

  .loop-art {
    width: 225px;
    height: 225px;
  }

  .center-message {
    inset: 70px;
  }

  .card-content {
    padding: 45px 35px;
  }

  .card-content h2 {
    font-size: 36px;
  }

  .article-page {
    padding-top: 30px;
  }

  .article-header {
    padding: 60px 30px 35px;
  }

  .article-content {
    padding: 35px 30px 60px;
  }

  .comparison {
    grid-template-columns: 1fr;
  }

  blockquote {
    padding: 30px 25px;
    font-size: 21px;
  }

  .article-footer {
    flex-direction: column;
    gap: 15px;
    text-align: center;
  }
}

@media (max-width: 480px) {
  .navbar {
    width: calc(100% - 28px);
  }

  .hero {
    padding-right: 18px;
    padding-left: 18px;
  }

  .hero h1 {
    font-size: 41px;
    letter-spacing: -1px;
  }

  .hero-description {
    font-size: 16px;
  }

  .featured-section,
  .article-page {
    width: calc(100% - 24px);
  }

  .blog-card,
  .article {
    border-radius: 24px;
  }

  .card-content {
    padding: 38px 25px;
  }

  .card-content h2 {
    font-size: 32px;
  }

  .article-header h1 {
    font-size: 43px;
    letter-spacing: -1px;
  }

  .article-introduction {
    font-size: 18px;
  }

  .article-content {
    padding-right: 22px;
    padding-left: 22px;
  }

  .article-content p {
    font-size: 16px;
  }

  .article-content h2 {
    font-size: 29px;
  }

  .reflection-box {
    flex-direction: column;
  }

  .final-thought {
    padding: 35px 24px;
  }

  .final-thought p {
    font-size: 20px;
  }

  .home-footer {
    flex-wrap: wrap;
  }
}
</style>
