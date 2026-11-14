<script setup>
defineEmits(["back"]);
</script>

<template>
  <article class="blog-page">

    <!-- BACK -->
    <div class="blog-topbar">

      <button
        class="blog-back"
        @click="$emit('back')"
      >
        <span>←</span>
        all little thoughts
      </button>

      <div class="blog-top-mark">
        little.log / 01
      </div>

    </div>


    <!-- BLOG HEADER -->
    <header class="blog-header">

      <div class="blog-category">
        TECH × LIFE
      </div>

      <h1>
        Finding the<br />
        <em>Base Condition.</em>
      </h1>

      <p class="blog-subtitle">
        Sometimes life feels a lot like recursion.
        We keep calling the same version of ourselves,
        hoping the next iteration somehow returns something different.
      </p>

      <div class="blog-info">

        <div class="blog-avatar">
          ↻
        </div>

        <div>
          <strong>little.log</strong>
          <span>5 min read · thought #01</span>
        </div>

      </div>

    </header>


    <!-- ARTICLE -->
    <div class="blog-body">

      <p class="blog-lead">
        In programming, recursion happens when a function calls itself.
        It can be elegant, powerful and surprisingly simple.
      </p>

      <p>
        But there is one thing recursion cannot survive without:
        a <strong>base condition.</strong>
      </p>

      <p>
        Without it, the function keeps calling itself again and again.
        Deeper. And deeper. And deeper.
      </p>


      <!-- VISUAL -->
      <div class="recursion-visual">

        <span>call()</span>

        <div class="visual-arrow">↓</div>

        <span>call()</span>

        <div class="visual-arrow">↓</div>

        <span>call()</span>

        <div class="visual-arrow">↓</div>

        <span class="visual-question">
          ...until when?
        </span>

      </div>


      <p>
        And sometimes, life behaves exactly the same way.
      </p>

      <p>
        We wake up. Follow the same routine. Carry the same thoughts.
        Meet the same situation. Give the same response.
      </p>

      <p>
        Tomorrow arrives and somehow the function gets called again.
      </p>


      <blockquote class="blog-quote">
        Maybe we aren't always stuck.
        <strong>
          Maybe we simply haven't found our base condition yet.
        </strong>
      </blockquote>


      <h2>
        So... what is a base condition in life?
      </h2>

      <p>
        In code, the base condition tells the recursion:
        <em>this is enough, return now.</em>
      </p>

      <p>
        Life probably needs those conditions too.
      </p>

      <p>
        Maybe your base condition is finally having the conversation
        you've been avoiding.
      </p>

      <p>
        Maybe it's setting a boundary.
      </p>

      <p>
        Maybe it's changing your routine, walking away from something,
        asking for help, accepting what you cannot change, or simply admitting:
      </p>


      <div class="soft-note">

        <span class="soft-note-icon">
          🌷
        </span>

        <p>
          “This iteration is no longer giving me anything new.”
        </p>

      </div>


      <h2>
        But not every recursion needs to stop.
      </h2>

      <p>
        That's the interesting part.
      </p>

      <p>
        Some loops are beautiful.
      </p>

      <p>
        Reading every evening. Practising something you love.
        Meeting people who make you feel lighter. Building a skill.
        Starting again after failing.
      </p>

      <p>
        These are repetitions too.
      </p>

      <p>
        But every iteration leaves something behind.
      </p>


      <!-- TWO LOOP CARDS -->
      <div class="loop-comparison">

        <div class="loop-card good-loop">

          <span class="loop-emoji">
            🌱
          </span>

          <h3>
            The good recursion
          </h3>

          <p>
            Each iteration adds something.
          </p>

          <ul>
            <li>+ experience</li>
            <li>+ peace</li>
            <li>+ skill</li>
            <li>+ connection</li>
          </ul>

          <span class="loop-caption">
            maybe don't return yet.
          </span>

        </div>


        <div class="loop-card bad-loop">

          <span class="loop-emoji">
            🍂
          </span>

          <h3>
            The draining recursion
          </h3>

          <p>
            Each iteration takes something.
          </p>

          <ul>
            <li>- energy</li>
            <li>- patience</li>
            <li>- confidence</li>
            <li>- yourself</li>
          </ul>

          <span class="loop-caption">
            find the base condition.
          </span>

        </div>

      </div>


      <p>
        The important thing is not to stop every loop.
      </p>

      <p>
        It is to notice what the loop is doing to you.
      </p>


      <h2>
        Before the next recursive call...
      </h2>

      <div class="reflection-list">

        <div class="reflection-item">
          <span>01</span>

          <p>
            Is this repetition still adding something to me?
          </p>
        </div>

        <div class="reflection-item">
          <span>02</span>

          <p>
            Am I continuing because I want to,
            or because I don't know how to stop?
          </p>
        </div>

        <div class="reflection-item">
          <span>03</span>

          <p>
            What becomes smaller in me after every iteration?
          </p>
        </div>

        <div class="reflection-item">
          <span>04</span>

          <p>
            What would my base condition look like?
          </p>
        </div>

      </div>


      <p>
        Maybe we don't need to debug our whole life at once.
      </p>

      <p>
        Sometimes we only need to look at the loop we're currently
        inside and ask whether another iteration is really necessary.
      </p>


      <!-- ENDING -->
      <div class="blog-ending">

        <div class="ending-loop">
          ↻
        </div>

        <p>
          Keep the recursions that help you grow.
        </p>

        <p>
          For the ones slowly burning you out,
          <strong>find your base condition.</strong>
        </p>

        <span>
          and let yourself return.
        </span>

      </div>


      <div class="blog-signoff">
        <span>✿</span>
        <p>
          Thanks for reading this little thought.
        </p>
      </div>

    </div>


    <!-- BLOG FOOTER -->
    <footer class="blog-footer">

      <button @click="$emit('back')">
        ← back to little.log
      </button>

      <span>
        thought #01
      </span>

    </footer>

  </article>
</template>
