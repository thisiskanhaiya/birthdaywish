<script setup>
import { ref } from "vue";

defineEmits(["back"]);

const selectedValue = ref("");
const reflection = ref("");

const chooseValue = (value) => {
  selectedValue.value = value;

  if (value === "confidence") {
    reflection.value =
      "शायद आपको खुद पर थोड़ा और भरोसा करना याद रखना है।";
  }

  if (value === "generosity") {
    reflection.value =
      "शायद आपके पास देने के लिए पैसे से कहीं ज़्यादा कुछ है।";
  }

  if (value === "compassion") {
    reflection.value =
      "शायद आज किसी को solution नहीं, बस आपका attention चाहिए।";
  }
};
</script>

<template>
  <article class="reader three-reader">

    <!-- =====================================================
         NAV
    ====================================================== -->

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


    <!-- =====================================================
         FRESH HERO
    ====================================================== -->

    <section class="three-hero">

      <div class="hero-sun"></div>

      <span class="three-spark spark-one">✦</span>
      <span class="three-spark spark-two">♡</span>
      <span class="three-spark spark-three">✿</span>


      <!-- THREE FLOATING CARDS -->

      <div class="value-orbit confidence-orbit">
        <div class="value-icon">
          ◎
        </div>

        <strong>
          आत्मविश्वास
        </strong>

        <small>
          I can handle it.
        </small>
      </div>


      <div class="value-orbit generosity-orbit">
        <div class="value-icon">
          ⤴
        </div>

        <strong>
          औदार्य
        </strong>

        <small>
          I have something to give.
        </small>
      </div>


      <div class="value-orbit compassion-orbit">
        <div class="value-icon">
          ♡
        </div>

        <strong>
          कारुण्य
        </strong>

        <small>
          Your world matters too.
        </small>
      </div>


      <!-- MAIN QUESTION -->

      <div class="three-question-card">

        <small>
          आज किसकी सबसे ज़्यादा ज़रूरत है?
        </small>

        <p>
          अगर इन तीन में से आज सिर्फ एक
          अपने साथ रख सकते...
        </p>

        <div class="value-options">

          <button
            type="button"
            :class="{ selected: selectedValue === 'confidence' }"
            @click="chooseValue('confidence')"
          >
            <span>◎</span>
            आत्मविश्वास
          </button>


          <button
            type="button"
            :class="{ selected: selectedValue === 'generosity' }"
            @click="chooseValue('generosity')"
          >
            <span>⤴</span>
            औदार्य
          </button>


          <button
            type="button"
            :class="{ selected: selectedValue === 'compassion' }"
            @click="chooseValue('compassion')"
          >
            <span>♡</span>
            कारुण्य
          </button>

        </div>


        <Transition name="reflection">

          <div
            v-if="reflection"
            class="value-response"
          >
            {{ reflection }}
          </div>

        </Transition>

      </div>


      <div class="hero-handwriting">
        तीन चीज़ें.<br />
        पूरी ज़िंदगी. ♡
      </div>

    </section>


    <!-- =====================================================
         ARTICLE
    ====================================================== -->

    <section class="reader-content">

      <div class="reader-meta">

        <span class="three-tag">
          Life
        </span>

        <small>
          6 min read
        </small>

      </div>


      <h1>
        तीन चीज़ें जो हर इंसान को<br />
        अपने भीतर बचाकर रखनी चाहिए.
      </h1>


      <p class="reader-subtitle">
        आत्मविश्वास। औदार्य। कारुण्य।
      </p>


      <!-- AUTHOR -->

      <div class="author">

        <span class="author-circle three-author">
          l
        </span>

        <div>
          <strong>
            by little.log
          </strong>

          <small>
            Thought #06
          </small>
        </div>

        <div class="reactions">
          <span>♡ 417</span>
          <span>◯ 36</span>
        </div>

      </div>


      <!-- =====================================================
           STORY
      ====================================================== -->

      <div class="story">

        <p>
          हम जीवन भर बहुत कुछ जमा करते हैं।
        </p>


        <!-- OBJECTS -->

        <div class="things-we-save">

          <span>₹ Money</span>
          <span>⌂ घर</span>
          <span>◇ Gold</span>
          <span>▣ Investments</span>
          <span>⌑ Documents</span>
          <span>⌘ Passwords</span>

        </div>


        <p>
          और फिर उन सबको सुरक्षित रखने के लिए lockers,
          insurance, backups और OTPs तक रखते हैं।
        </p>

        <p>
          ज़रूरी भी है।
        </p>

        <p>
          लेकिन कभी-कभी मुझे लगता है कि हमारी सबसे valuable
          चीज़ें किसी locker में रखी ही नहीं जा सकतीं।
        </p>


        <div class="locker-thought">

          <span>🔐</span>

          <div>
            <small>
              THINK ABOUT IT...
            </small>

            <p>
              कुछ ऐसा क्या है जिसे कोई चुरा नहीं सकता,
              और currency गिरने पर जिसकी value कम नहीं होती?
            </p>
          </div>

        </div>


        <p>
          और अगर ज़िंदगी किसी दिन कह दे:
        </p>


        <div class="restart-line">
          startAgain();
        </div>


        <p>
          तो शायद वही चीज़ें आपको फिर से खड़ा करती हैं।
        </p>


        <div class="three-main-line">

          <span>01</span>
          <strong>आत्मविश्वास</strong>

          <i>·</i>

          <span>02</span>
          <strong>औदार्य</strong>

          <i>·</i>

          <span>03</span>
          <strong>कारुण्य</strong>

        </div>


        <!-- =================================================
             01 CONFIDENCE
        ================================================== -->

        <section class="value-section confidence-section">

          <div class="value-section-number">
            01
          </div>


          <div class="value-section-heading">

            <span class="value-big-icon">
              ◎
            </span>

            <div>
              <small>
                KEEP THIS INSIDE YOU
              </small>

              <h2>
                आत्मविश्वास
              </h2>

              <p>
                “जो भी होगा, मैं संभाल लूँगा।”
              </p>
            </div>

          </div>

        </section>


        <p>
          मेरे लिए आत्मविश्वास का मतलब यह नहीं है:
        </p>


        <div class="not-this">

          <span>✕</span>

          <p>
            “मैं सबसे अच्छा हूँ।”
          </p>

        </div>


        <div class="not-this">

          <span>✕</span>

          <p>
            “मुझे कभी किसी की ज़रूरत नहीं पड़ेगी।”
          </p>

        </div>


        <p>
          आत्मविश्वास शायद इससे कहीं सरल है।
        </p>


        <div class="confidence-quote">

          <span>“</span>

          <p>
            परिस्थितियाँ बदलेंगी तो मैं भी सीखूँगा,
            बदलूँगा और रास्ता निकाल लूँगा।
          </p>

        </div>


        <p>
          मान लो आज आपके पास बहुत पैसे हैं।
        </p>

        <p>
          कल उनकी value बदल सकती है।
        </p>

        <p>
          Job बदल सकती है।
        </p>

        <p>
          Company बदल सकती है।
        </p>

        <p>
          Technology बदल सकती है।
        </p>

        <p>
          आज की valuable skill पाँच साल बाद अकेली
          पर्याप्त नहीं भी हो सकती।
        </p>


        <!-- SAVE THINGS -->

        <div class="save-differently">

          <small>
            SO SAVE DIFFERENTLY...
          </small>


          <div class="save-row">

            <span>01</span>

            <div>
              <strong>
                Skills save करो.
              </strong>

              <p>
                ऐसी skills जिन्हें कोई आपसे चुरा नहीं सकता।
              </p>
            </div>

          </div>


          <div class="save-row">

            <span>02</span>

            <div>
              <strong>
                सीखने की आदत save करो.
              </strong>

              <p>
                क्योंकि tools बदलेंगे।
              </p>
            </div>

          </div>


          <div class="save-row">

            <span>03</span>

            <div>
              <strong>
                Curiosity save करो.
              </strong>

              <p>
                वही आपको अगले version तक ले जाएगी।
              </p>
            </div>

          </div>

        </div>


        <p>
          ऐसी क्षमता बनाओ कि अगर life कहे:
        </p>


        <div class="life-reset-card">

          <small>
            SYSTEM MESSAGE
          </small>

          <p>
            “चलो... फिर से शुरू करते हैं।”
          </p>

          <div class="reset-answer">
            ठीक है। कर लेंगे. ♡
          </div>

        </div>


        <p>
          पैसा खत्म हो सकता है।
        </p>

        <p>
          लेकिन अगर आपके पास कुछ useful करने की skill है...
        </p>

        <p>
          अगर आप सीख सकते हैं...
        </p>

        <p>
          मेहनत कर सकते हैं...
        </p>

        <p>
          और लोगों के लिए value बना सकते हैं...
        </p>

        <p>
          तो आपके अंदर फिर से कमाने की क्षमता है।
        </p>


        <div class="money-question">

          <span>₹</span>

          <p>
            Confidence सिर्फ यह नहीं कि
            <strong>मेरे पास कितना है.</strong>
          </p>

          <p>
            असली सवाल:
            <strong>
              अगर कम हो गया तो क्या मुझे भरोसा है
              कि मैं फिर बना सकता हूँ?
            </strong>
          </p>

        </div>


        <!-- HAPPINESS -->

        <h2>
          खुशी भी save करनी पड़ती है.
        </h2>

        <p>
          थोड़ा अजीब लगता है ना?
        </p>

        <p>
          पैसे save करना सब सीखते हैं।
        </p>

        <p>
          लेकिन happiness create करना कम लोग सीखते हैं।
        </p>


        <div class="happiness-cloud">

          <span>Walk?</span>
          <span>Music?</span>
          <span>Family?</span>
          <span>Exercise?</span>
          <span>Writing?</span>
          <span>Prayer?</span>
          <span>Nature?</span>
          <span>Silence?</span>
          <span>Friends?</span>

        </div>


        <p>
          हमें पता होना चाहिए कि हमें genuinely
          अच्छा क्या महसूस कराता है।
        </p>

        <p>
          क्योंकि हर happiness खरीदी नहीं जा सकती।
        </p>

        <p>
          और हर sadness shopping से ठीक नहीं होती।
        </p>


        <div class="inner-skills">

          <small>INNER SKILLS</small>

          <div>
            <span>◌</span>
            खुद के thoughts को observe करना
          </div>

          <div>
            <span>◌</span>
            खुद को calm करना
          </div>

          <div>
            <span>◌</span>
            अकेले comfortable होना
          </div>

          <div>
            <span>◌</span>
            बिना stimulation के भी ठीक रहना
          </div>

        </div>


        <p>
          अच्छी नींद भी सिर्फ expensive mattress का
          result नहीं है।
        </p>

        <p>
          कभी-कभी नींद उस भरोसे से भी आती है:
        </p>


        <div class="sleep-note">

          <span>☾</span>

          <p>
            “आज जितना हो सकता था, मैंने किया।
            जो कल आएगा, उसे कल देखेंगे।”
          </p>

        </div>


        <!-- BABY -->

        <h2>
          एक छोटे बच्चे को देखो.
        </h2>

        <p>
          बच्चा रात को सोने से पहले calculation नहीं करता:
        </p>


        <div class="baby-code">

          breakfast_funding_source = ???

        </div>


        <p>
          उसके अंदर एक सहज भरोसा है।
        </p>

        <p>
          माँ है।
        </p>

        <p>
          घर है।
        </p>

        <p>
          खाना मिलेगा।
        </p>

        <p>
          जीवन चल रहा है।
        </p>


        <div class="adult-note">

          <small>
            OBVIOUSLY...
          </small>

          <p>
            Adult life अलग है।
            Bills real हैं। Saving important है।
            Planning भी ज़रूरी है।
          </p>

        </div>


        <p>
          लेकिन शायद उस बच्चे वाला थोड़ा-सा भरोसा
          हमें भी बचाकर रखना चाहिए।
        </p>


        <div class="trust-yourself">

          <p>
            दुनिया में मेरे लिए भी जगह है।
          </p>

          <p>
            मैं सीख सकता हूँ।
          </p>

          <p>
            मैं value create कर सकता हूँ।
          </p>

          <p>
            मैं अपना भोजन कमा सकता हूँ।
          </p>

          <strong>
            मैं रास्ता ढूँढ सकता हूँ. ♡
          </strong>

        </div>


        <div class="gentle-joke">
          Planning करो। Saving करो।<br />
          लेकिन डर को retirement plan मत बनाओ. 😭
        </div>


        <!-- =================================================
             02 GENEROSITY
        ================================================== -->

        <section class="value-section generosity-section">

          <div class="value-section-number">
            02
          </div>


          <div class="value-section-heading">

            <span class="value-big-icon">
              ⤴
            </span>

            <div>
              <small>
                KEEP SOME SPACE FOR OTHERS
              </small>

              <h2>
                औदार्य
              </h2>

              <p>
                आपके पास जो अच्छा है,
                उसमें किसी और के लिए थोड़ी जगह रखना।
              </p>
            </div>

          </div>

        </section>


        <p>
          औदार्य को हम अक्सर सिर्फ पैसे से जोड़ देते हैं।
        </p>

        <p>
          किसी को पैसे दिए।
        </p>

        <p>
          Donation किया।
        </p>

        <p>
          Gift खरीदा।
        </p>

        <p>
          बिल्कुल अच्छा है।
        </p>

        <p>
          लेकिन generosity उससे बहुत बड़ी चीज़ है।
        </p>


        <div class="give-grid">

          <div>
            <span>⌛</span>
            <strong>समय</strong>
          </div>

          <div>
            <span>◉</span>
            <strong>Attention</strong>
          </div>

          <div>
            <span>⌘</span>
            <strong>Knowledge</strong>
          </div>

          <div>
            <span>⌂</span>
            <strong>Safety</strong>
          </div>

          <div>
            <span>✦</span>
            <strong>Encouragement</strong>
          </div>

          <div>
            <span>♡</span>
            <strong>Kindness</strong>
          </div>

        </div>


        <p>
          किसी nervous इंसान को safe feel करा सकते हैं।
        </p>

        <p>
          किसी beginner से कह सकते हैं:
        </p>


        <div class="beginner-note">
          “गलती कर सकते हो। कोई बात नहीं।
          Try again.”
        </div>


        <p>
          किसी नए colleague के पास बैठ सकते हैं।
        </p>

        <p>
          परेशान दोस्त की बात बिना तुरंत solution दिए
          सुन सकते हैं।
        </p>

        <p>
          घर जाकर parents के साथ आधा घंटा
          बस बैठ सकते हैं।
        </p>


        <h2>
          कभी coffee shop में बैठकर दुनिया देखना.
        </h2>


        <div class="coffee-scene">

          <div class="coffee-table">

            <div class="coffee-cup">
              <span class="steam-one"></span>
              <span class="steam-two"></span>
            </div>

            <div class="tiny-book"></div>

          </div>


          <div class="coffee-window">

            <span class="person-one"></span>
            <span class="person-two"></span>
            <span class="person-three"></span>

          </div>

        </div>


        <p>
          Phone नीचे रखो।
        </p>

        <p>
          कुछ देर लोगों को आते-जाते देखो।
        </p>

        <p>
          कोई अपने बच्चे के साथ है।
        </p>

        <p>
          कोई अकेला coffee पी रहा है।
        </p>

        <p>
          कोई किसी का इंतज़ार कर रहा है।
        </p>

        <p>
          कोई काम कर रहा है।
        </p>


        <div class="world-note">

          <span>🌍</span>

          <p>
            अचानक याद आता है:
            दुनिया सिर्फ हमारी problems से नहीं बनी है।
          </p>

        </div>


        <p>
          हर table पर एक अलग कहानी चल रही है।
        </p>

        <p>
          Universe को थोड़ा समय देना भी शायद
          generosity का एक रूप है।
        </p>

        <p>
          हर खाली minute को content से भरना
          ज़रूरी नहीं।
        </p>

        <p>
          कभी बस मौजूद रहना भी अच्छा है।
        </p>


        <h2>
          Happiness की एक अजीब property है.
        </h2>


        <div class="giving-math">

          <div class="normal-math">

            <small>MONEY</small>

            <strong>
              ₹100 − ₹50 = ₹50
            </strong>

          </div>


          <div class="weird-math">

            <small>KINDNESS</small>

            <strong>
              ♡ − ♡ = ♡♡
            </strong>

          </div>

        </div>


        <p>
          Respect.
        </p>

        <p>
          Encouragement.
        </p>

        <p>
          Knowledge.
        </p>

        <p>
          Positive energy.
        </p>

        <p>
          Safety.
        </p>

        <p>
          Smile.
        </p>

        <p>
          कुछ चीज़ें देने के बाद कम नहीं होतीं।
        </p>

        <p>
          कई बार बढ़ जाती हैं।
        </p>


        <div class="generosity-question">

          <small>
            MAYBE THIS IS GENEROSITY...
          </small>

          <p>
            जहाँ आप मौजूद हों...
            क्या वहाँ लोग थोड़ा बेहतर महसूस करते हैं?
          </p>


          <div class="better-tags">

            <span>थोड़ा safe.</span>
            <span>थोड़ा seen.</span>
            <span>थोड़ा lighter.</span>

          </div>

        </div>


        <!-- =================================================
             03 COMPASSION
        ================================================== -->

        <section class="value-section compassion-section">

          <div class="value-section-number">
            03
          </div>


          <div class="value-section-heading">

            <span class="value-big-icon">
              ♡
            </span>

            <div>
              <small>
                LET ANOTHER PERSON MATTER
              </small>

              <h2>
                कारुण्य
              </h2>

              <p>
                दया नहीं।
                किसी दूसरे इंसान के अनुभव के लिए जगह बनाना।
              </p>
            </div>

          </div>

        </section>


        <p>
          मेरे लिए कारुण्य का मतलब किसी को कमजोर समझकर
          उस पर pity करना नहीं है।
        </p>

        <p>
          यह “बेचारा” कहना भी नहीं है।
        </p>

        <p>
          कारुण्य में बराबरी रहती है।
        </p>

        <p>
          आप सामने वाले को छोटा नहीं करते।
        </p>


        <div class="compassion-line">

          <span>♡</span>

          <p>
            “यह इंसान भी अपने हिस्से की
            कोई कहानी लेकर चल रहा है।”
          </p>

        </div>


        <!-- DRESS EXAMPLE -->

        <h2>
          एक छोटा example.
        </h2>

        <p>
          मान लो मैं अपने लिए बहुत सारे dresses
          खरीद सकता हूँ।
        </p>

        <p>
          दस खरीद सकता हूँ।
        </p>

        <p>
          बीस भी।
        </p>

        <p>
          लेकिन कोई मेरे बारे में सोचकर एक dress चुने...
        </p>

        <p>
          और बोले:
        </p>


        <div class="gift-card">

          <div class="dress-illustration">

            <span class="dress-top"></span>
            <span class="dress-skirt"></span>

          </div>


          <div>
            <small>
              FOR YOU ♡
            </small>

            <p>
              “मुझे लगा यह तुम्हें अच्छी लगेगी।”
            </p>
          </div>

        </div>


        <p>
          तो खुशी सिर्फ dress की नहीं होती।
        </p>

        <p>
          Dress मैं खुद भी खरीद सकता था।
        </p>

        <p>
          खुशी यह होती है कि:
        </p>


        <div class="remembered-note">
          किसी ने मुझे याद किया. ♡
        </div>


        <p>
          यही फर्क है।
        </p>


        <!-- FOOD -->

        <p>
          मैं अच्छा खाना खुद पका सकता हूँ।
        </p>

        <p>
          Restaurant से order भी कर सकता हूँ।
        </p>

        <p>
          लेकिन कोई मेरे लिए अपने हाथ से कुछ बनाकर कहे:
        </p>


        <div class="food-note">

          <span>🍲</span>

          <p>
            “तुम्हारे लिए बनाया है।”
          </p>

        </div>


        <p>
          तो उसका स्वाद सिर्फ ingredients से नहीं आता।
        </p>

        <p>
          उसमें attention मिला हुआ है।
        </p>

        <p>
          समय मिला हुआ है।
        </p>

        <p>
          Care मिला हुआ है।
        </p>

        <p>
          यही ordinary चीज़ को special बना देता है।
        </p>


        <!-- LISTEN -->

        <h2>
          कारुण्य में सुनना भी आता है.
        </h2>

        <p>
          हम सब चाहते हैं कि लोग हमारी बात सुनें।
        </p>

        <p>
          लेकिन conversation का एक छोटा rule शायद
          यह होना चाहिए:
        </p>


        <div class="listen-first">

          <span class="listen-icon">
            ◉
          </span>

          <p>
            पहले सुनो.<br />
            फिर सुने जाओ.
          </p>

        </div>


        <p>
          अगर हर conversation में हमें सिर्फ अपनी story
          बतानी है...
        </p>

        <p>
          अपनी achievement...
        </p>

        <p>
          अपना struggle...
        </p>

        <p>
          अपनी opinion...
        </p>

        <p>
          तो धीरे-धीरे लोग थक जाते हैं।
        </p>


        <div class="interesting-person">

          <small>
            MAYBE AN INTERESTING PERSON ISN'T SOMEONE WHO
            ALWAYS HAS SOMETHING TO SAY.
          </small>

          <p>
            कई बार interesting इंसान वो होता है जिसके सामने
            आपको लगता है:
          </p>

          <strong>
            “मैं अपनी बात पूरी कर सकता हूँ।”
          </strong>

        </div>


        <h2>
          Give respect. Don't perform respect.
        </h2>

        <p>
          Respect कोई transaction नहीं होना चाहिए:
        </p>


        <div class="transaction">

          मैंने respect दी
          <span>→</span>
          अब तुम मुझे दो

        </div>


        <p>
          शायद real respect इससे simple है।
        </p>


        <div class="respect-rules">

          <div>
            <span>01</span>
            मैं आपकी बात सुनूँगा।
          </div>

          <div>
            <span>02</span>
            आपको बीच में छोटा नहीं करूँगा।
          </div>

          <div>
            <span>03</span>
            Disagreement आपकी dignity कम नहीं करेगा।
          </div>

        </div>


        <p>
          मैं आपसे सहमत नहीं भी हूँ...
        </p>

        <p>
          फिर भी आपको इंसान की तरह treat कर सकता हूँ।
        </p>


        <div class="not-weak">
          Soft होना नहीं।<br />
          Weak होना नहीं।<br />
          <strong>Human रहना.</strong>
        </div>


        <!-- =================================================
             ALL THREE
        ================================================== -->

        <h2>
          तीनों को साथ रखो.
        </h2>

        <p>
          मुझे इन तीनों का combination बहुत सुंदर लगता है।
        </p>


        <div class="three-summary">

          <div class="summary-card confidence-summary">

            <span>◎</span>

            <small>आत्मविश्वास</small>

            <strong>
              “मैं संभाल लूँगा।”
            </strong>

          </div>


          <div class="summary-card generosity-summary">

            <span>⤴</span>

            <small>औदार्य</small>

            <strong>
              “मेरे पास देने के लिए कुछ है।”
            </strong>

          </div>


          <div class="summary-card compassion-summary">

            <span>♡</span>

            <small>कारुण्य</small>

            <strong>
              “तुम्हारी दुनिया भी उतनी ही real है।”
            </strong>

          </div>

        </div>


        <p>
          लेकिन balance important है।
        </p>


        <div class="balance-grid">

          <div>

            <small>
              आत्मविश्वास − कारुण्य
            </small>

            <strong>
              Ego बन सकता है.
            </strong>

          </div>


          <div>

            <small>
              औदार्य − आत्मविश्वास
            </small>

            <strong>
              खुद को खाली कर सकता है.
            </strong>

          </div>


          <div>

            <small>
              कारुण्य − Boundaries
            </small>

            <strong>
              दूसरों का दर्द आपका बोझ बन सकता है.
            </strong>

          </div>

        </div>


        <div class="balance-final">

          <p>
            आत्मविश्वास आपको
            <strong>खड़ा</strong> रखता है।
          </p>

          <p>
            औदार्य आपको
            <strong>खुला</strong> रखता है।
          </p>

          <p>
            कारुण्य आपको
            <strong>इंसान</strong> बनाए रखता है।
          </p>

        </div>


        <!-- =================================================
             NIGHT CHECK
        ================================================== -->

        <div class="night-check">

          <span class="night-moon">
            ☾
          </span>

          <small>
            TONIGHT, ASK YOURSELF...
          </small>


          <div class="night-question">

            <span>01</span>

            <p>
              अगर कल सब बदल जाए,
              क्या मुझे भरोसा है कि
              मैं फिर रास्ता बना लूँगा?
            </p>

          </div>


          <div class="night-question">

            <span>02</span>

            <p>
              आज मेरी वजह से किस इंसान का
              दिन थोड़ा बेहतर हुआ?
            </p>

          </div>


          <div class="night-question">

            <span>03</span>

            <p>
              आज मैंने किसकी बात
              सच में सुनी?
            </p>

          </div>

        </div>


        <p>
          अगर तीनों के जवाब मिल गए...
        </p>

        <p>
          बहुत अच्छा।
        </p>

        <p>
          अगर नहीं मिले...
        </p>

        <p>
          कोई problem नहीं।
        </p>

        <p>
          कल फिर कोशिश करना। ♡
        </p>


        <!-- END -->

        <div class="final-save">

          <small>
            LIFE BACKUP
          </small>


          <code>
            <span>save आत्मविश्वास;</span>
            <span>save औदार्य;</span>
            <span>save कारुण्य;</span>

            <br />

            <span>while (alive) {</span>
            <span>&nbsp;&nbsp;learn();</span>
            <span>&nbsp;&nbsp;give();</span>
            <span>&nbsp;&nbsp;listen();</span>
            <span>&nbsp;&nbsp;love();</span>
            <span>}</span>
          </code>

        </div>


        <p>
          बाकी बहुत कुछ समय के साथ बदल जाएगा।
        </p>

        <p>
          ये तीन चीज़ें शायद आपको हर version में
          पहचानने लायक बनाए रखेंगी।
        </p>


        <div class="story-finish three-finish">

          <span>
            ♡
          </span>

          <p>
            Thoughts जो answers नहीं भी दें...
          </p>

          <strong>
            कभी-कभी life को देखने का angle
            बदल देते हैं.
          </strong>

        </div>


        <div class="next-thought">

          <span>✦</span>

          <div>
            <small>
              NEXT ON LITTLE.LOG
            </small>

            <p>
              एक और छोटा thought जल्द...
            </p>

            <strong>
              stay curious. stay human. ♡
            </strong>
          </div>

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
          save what<br />
          matters ♡
        </span>

      </footer>

    </section>

  </article>
</template>


<style scoped>

/* ==========================================================
   HERO
========================================================== */

.three-hero {
  position: relative;

  min-height: 500px;

  overflow: hidden;

  background:
    radial-gradient(
      circle at 83% 16%,
      #ffeca8 0 9%,
      transparent 23%
    ),
    linear-gradient(
      150deg,
      #d3f1ff,
      #e5ddff 30%,
      #ffdcea 64%,
      #ffe6b8
    );
}

.hero-sun {
  position: absolute;

  top: 48px;
  right: 65px;

  width: 90px;
  height: 90px;

  border-radius: 50%;

  background: rgba(255, 224, 125, .66);
}

.three-spark {
  position: absolute;

  z-index: 4;

  font-size: 24px;
}

.spark-one {
  top: 42px;
  left: 42px;

  color: #7d6aac;
}

.spark-two {
  top: 88px;
  left: 86px;

  color: #e66d9c;
}

.spark-three {
  right: 37px;
  bottom: 34px;

  color: #77a77d;
}


/* ==========================================================
   VALUE ORBITS
========================================================== */

.value-orbit {
  position: absolute;

  z-index: 5;

  width: 145px;
  height: 145px;

  border: 1px solid rgba(82,67,104,.12);
  border-radius: 45px;

  display: flex;
  flex-direction: column;

  align-items: center;
  justify-content: center;

  background: rgba(255,255,255,.75);

  box-shadow:
    0 15px 32px rgba(66,52,91,.1);

  backdrop-filter: blur(13px);
}

.confidence-orbit {
  right: 236px;
  bottom: 49px;

  transform: rotate(-8deg);
}

.generosity-orbit {
  right: 85px;
  bottom: 93px;

  transform: rotate(6deg);
}

.compassion-orbit {
  right: 145px;
  top: 56px;

  transform: rotate(-2deg);
}

.value-icon {
  width: 53px;
  height: 53px;

  margin-bottom: 8px;

  border-radius: 50%;

  display: grid;
  place-items: center;

  color: white;

  background:
    linear-gradient(
      145deg,
      #7362bd,
      #dd6d9e
    );

  box-shadow:
    3px 4px 0 #ddd4ff;

  font-size: 23px;
}

.value-orbit strong {
  color: #4e4857;

  font-family: "Patrick Hand";
  font-size: 16px;
}

.value-orbit small {
  margin-top: 3px;

  color: #918994;

  font-size: 6px;
}


/* ==========================================================
   HERO QUESTION
========================================================== */

.three-question-card {
  position: absolute;

  z-index: 20;

  top: 55px;
  left: 42px;

  width: 340px;

  padding: 23px;

  border: 1px solid rgba(72,57,94,.1);
  border-radius: 19px;

  background: rgba(255,255,255,.87);

  box-shadow:
    0 18px 38px rgba(62,48,91,.11);

  backdrop-filter: blur(13px);

  transform: rotate(-2deg);
}

.three-question-card > small,
.locker-thought small,
.life-reset-card small,
.inner-skills > small,
.generosity-question small,
.interesting-person small,
.night-check > small,
.final-save > small,
.next-thought small {
  color: #8874ab;

  font-family: "DM Mono";
  font-size: 6px;

  letter-spacing: .8px;
}

.three-question-card > p {
  margin: 8px 0 14px;

  color: #504757;

  font-family: "Patrick Hand";
  font-size: 19px;

  line-height: 1.12;
}

.value-options {
  display: grid;

  gap: 7px;
}

.value-options button {
  padding: 9px 11px;

  border: 1px solid #ded7e5;
  border-radius: 10px;

  display: flex;
  align-items: center;

  gap: 8px;

  color: #686071;
  background: white;

  font-size: 8px;

  text-align: left;
}

.value-options button > span {
  width: 22px;
  height: 22px;

  flex: 0 0 auto;

  border-radius: 50%;

  display: grid;
  place-items: center;

  color: #765faf;
  background: #eee9ff;
}

.value-options button.selected {
  border-color: #97ba9b;

  color: #567159;
  background: #ebf6e9;
}

.value-response {
  margin-top: 10px;
  padding: 9px 11px;

  border-radius: 9px;

  color: #725468;
  background: #fff0f5;

  font-family: "Patrick Hand";
  font-size: 13px;
}

.hero-handwriting {
  position: absolute;

  top: 23px;
  right: 27px;

  color: #735c74;

  font-family: "Patrick Hand";
  font-size: 17px;

  line-height: 1.05;

  text-align: right;

  transform: rotate(5deg);
}


/* ==========================================================
   TAG / AUTHOR
========================================================== */

.three-tag {
  color: #9f5774 !important;

  background: #ffe1eb !important;
}

.three-author {
  background:
    linear-gradient(
      145deg,
      #7865be,
      #d76f9d
    );
}


/* ==========================================================
   SAVINGS
========================================================== */

.things-we-save {
  margin: 24px 0;

  display: flex;
  flex-wrap: wrap;

  gap: 7px;
}

.things-we-save span {
  padding: 7px 11px;

  border: 1px solid #e1dbe5;
  border-radius: 50px;

  color: #746d78;
  background: #fffafd;

  font-size: 7px;
}


/* ==========================================================
   LOCKER THOUGHT
========================================================== */

.locker-thought {
  margin: 28px 0;
  padding: 22px;

  border-radius: 14px;

  display: flex;
  align-items: center;

  gap: 14px;

  background:
    linear-gradient(
      135deg,
      #e9e6ff,
      #ffe9f1
    );
}

.locker-thought > span {
  font-size: 30px;
}

.locker-thought p {
  margin: 7px 0 0;

  color: #594f5f;

  font-family: "Patrick Hand";
  font-size: 18px;

  line-height: 1.15;
}

.restart-line {
  width: fit-content;

  margin: 25px auto;
  padding: 11px 18px;

  border-radius: 10px;

  color: #dcd3ff;
  background: #282640;

  box-shadow:
    3px 4px 0 #ddd5ff;

  font-family: "DM Mono";
  font-size: 9px;
}


/* ==========================================================
   THREE MAIN
========================================================== */

.three-main-line {
  margin: 30px 0;

  padding: 19px;

  border: 1px solid #ddd7e4;
  border-radius: 14px;

  display: flex;
  flex-wrap: wrap;

  justify-content: center;
  align-items: center;

  gap: 8px;

  background: #fffafd;
}

.three-main-line > span {
  color: #8a74b7;

  font-family: "DM Mono";
  font-size: 7px;
}

.three-main-line > strong {
  color: #554c5c;

  font-family: "Patrick Hand";
  font-size: 16px;
}

.three-main-line i {
  color: #d6cdd9;
}


/* ==========================================================
   VALUE SECTION HEADERS
========================================================== */

.value-section {
  position: relative;

  margin: 55px 0 29px;
  padding: 30px 25px;

  border-radius: 17px;

  overflow: hidden;
}

.confidence-section {
  background:
    linear-gradient(
      135deg,
      #e4e0ff,
      #f1ecff
    );
}

.generosity-section {
  background:
    linear-gradient(
      135deg,
      #e8f5e6,
      #f3fbef
    );
}

.compassion-section {
  background:
    linear-gradient(
      135deg,
      #ffe4ed,
      #fff0e5
    );
}

.value-section-number {
  position: absolute;

  right: 15px;
  bottom: -22px;

  color: rgba(70,61,90,.06);

  font-family: "DM Mono";
  font-size: 85px;

  font-weight: 700;
}

.value-section-heading {
  position: relative;

  z-index: 2;

  display: flex;
  align-items: center;

  gap: 17px;
}

.value-big-icon {
  width: 60px;
  height: 60px;

  flex: 0 0 auto;

  border-radius: 50%;

  display: grid;
  place-items: center;

  color: white;

  background:
    linear-gradient(
      145deg,
      #7764bd,
      #d8739d
    );

  box-shadow:
    4px 5px 0 rgba(107,88,152,.14);

  font-size: 26px;
}

.generosity-section .value-big-icon {
  background:
    linear-gradient(
      145deg,
      #6e9e75,
      #91bd82
    );
}

.compassion-section .value-big-icon {
  background:
    linear-gradient(
      145deg,
      #df759d,
      #ef9b82
    );
}

.value-section-heading small {
  color: #8e8495;

  font-family: "DM Mono";
  font-size: 6px;
}

.value-section-heading h2 {
  margin: 4px 0 !important;

  font-size: 30px !important;
}

.value-section-heading p {
  margin: 0;

  color: #696170;

  font-family: "Patrick Hand";
  font-size: 16px;
}


/* ==========================================================
   NOT THIS
========================================================== */

.not-this {
  margin: 9px 0;
  padding: 13px 16px;

  border-radius: 11px;

  display: flex;
  align-items: center;

  gap: 10px;

  background: #fff0e7;
}

.not-this > span {
  color: #c16b73;
}

.not-this p {
  margin: 0;

  color: #65575d;

  font-family: "Patrick Hand";
  font-size: 15px;
}


/* ==========================================================
   CONFIDENCE QUOTE
========================================================== */

.confidence-quote {
  margin: 27px 0;
  padding: 24px;

  border-radius: 15px;

  display: flex;

  gap: 12px;

  background:
    linear-gradient(
      135deg,
      #6859ae,
      #8b67b0
    );

  color: white;
}

.confidence-quote > span {
  font-family: Georgia, serif;
  font-size: 44px;

  line-height: .7;

  opacity: .55;
}

.confidence-quote p {
  margin: 0;

  font-family: "Patrick Hand";
  font-size: 20px;

  line-height: 1.15;
}


/* ==========================================================
   SAVE DIFFERENTLY
========================================================== */

.save-differently {
  margin: 28px 0;
  padding: 22px;

  border: 1px solid #ddd7e5;
  border-radius: 15px;

  background: #fffafd;
}

.save-differently > small {
  color: #8c78b2;

  font-family: "DM Mono";
  font-size: 6px;
}

.save-row {
  padding: 14px 0;

  border-bottom: 1px dashed #ddd5df;

  display: grid;

  grid-template-columns: 35px 1fr;

  gap: 9px;
}

.save-row:last-child {
  border: 0;

  padding-bottom: 0;
}

.save-row > span {
  color: #8a72b6;

  font-family: "DM Mono";
  font-size: 7px;
}

.save-row strong {
  color: #514a55;

  font-size: 9px;
}

.save-row p {
  margin: 4px 0 0;

  color: #858089;

  font-size: 7px;
}


/* ==========================================================
   RESET
========================================================== */

.life-reset-card {
  margin: 27px 0;
  padding: 22px;

  border-radius: 14px;

  color: #e7e1fb;
  background: #292740;
}

.life-reset-card p {
  margin: 9px 0;

  font-family: "Patrick Hand";
  font-size: 19px;
}

.life-reset-card small {
  color: #a9a1ba !important;
}

.reset-answer {
  width: fit-content;

  padding: 7px 10px;

  border-radius: 7px;

  color: #545d55;
  background: #dff0dc;

  font-size: 8px;
}


/* ==========================================================
   MONEY
========================================================== */

.money-question {
  margin: 28px 0;
  padding: 22px;

  border-radius: 15px;

  display: grid;

  grid-template-columns: 40px 1fr;

  gap: 10px;

  background: #e8f4e6;
}

.money-question > span {
  width: 35px;
  height: 35px;

  border-radius: 50%;

  display: grid;
  place-items: center;

  color: white;
  background: #77a87a;

  font-size: 18px;
}

.money-question p {
  grid-column: 2;

  margin: 0 0 8px;

  color: #536155;

  font-size: 9px;
}


/* ==========================================================
   HAPPINESS
========================================================== */

.happiness-cloud {
  margin: 25px 0;

  display: flex;
  flex-wrap: wrap;

  justify-content: center;

  gap: 7px;
}

.happiness-cloud span {
  padding: 8px 12px;

  border-radius: 50px;

  color: #675d75;

  background:
    linear-gradient(
      135deg,
      #eee9ff,
      #ffeaf1
    );

  font-family: "Patrick Hand";
  font-size: 13px;
}

.inner-skills {
  margin: 27px 0;
  padding: 22px;

  border-radius: 15px;

  background: #f4f1fa;
}

.inner-skills > div {
  padding: 10px 0;

  border-bottom: 1px dashed #ddd6e2;

  display: flex;

  gap: 10px;

  color: #655d69;

  font-size: 9px;
}

.inner-skills > div:last-child {
  border: 0;
}

.inner-skills div > span {
  color: #826cb3;
}


/* ==========================================================
   SLEEP
========================================================== */

.sleep-note {
  margin: 28px 0;
  padding: 23px;

  border-radius: 15px;

  display: flex;
  align-items: center;

  gap: 14px;

  color: #eee9ff;

  background:
    linear-gradient(
      135deg,
      #292843,
      #504268
    );
}

.sleep-note > span {
  color: #ffdd82;

  font-size: 30px;
}

.sleep-note p {
  margin: 0;

  font-family: "Patrick Hand";
  font-size: 18px;

  line-height: 1.15;
}


/* ==========================================================
   BABY / TRUST
========================================================== */

.baby-code {
  width: fit-content;

  margin: 23px auto;
  padding: 11px 15px;

  border-radius: 9px;

  color: #d6ccff;
  background: #2a2842;

  font-family: "DM Mono";
  font-size: 8px;
}

.adult-note {
  margin: 25px 0;
  padding: 19px;

  border-radius: 13px;

  background: #fff0dd;
}

.adult-note small {
  color: #a07172;

  font-family: "DM Mono";
  font-size: 6px;
}

.adult-note p {
  margin: 7px 0 0;

  color: #67575c;

  font-size: 9px;
}

.trust-yourself {
  margin: 27px 0;
  padding: 24px;

  border-radius: 15px;

  background:
    linear-gradient(
      135deg,
      #e8f4e6,
      #f0efff
    );
}

.trust-yourself p {
  margin: 7px 0;

  color: #58605c;

  font-family: "Patrick Hand";
  font-size: 16px;
}

.trust-yourself strong {
  display: block;

  margin-top: 12px;

  color: #5e4f72;

  font-family: "Patrick Hand";
  font-size: 19px;
}

.gentle-joke {
  margin: 28px 0;
  padding: 18px;

  border-left: 4px solid #e3995f;

  color: #605357;
  background: #fff4e8;

  font-family: "Patrick Hand";
  font-size: 17px;

  line-height: 1.15;
}


/* ==========================================================
   GIVE GRID
========================================================== */

.give-grid {
  margin: 27px 0;

  display: grid;

  grid-template-columns: repeat(3,1fr);

  gap: 8px;
}

.give-grid > div {
  padding: 17px 8px;

  border-radius: 12px;

  background: #eaf5e8;

  text-align: center;
}

.give-grid span {
  display: block;

  margin-bottom: 6px;

  color: #729e74;

  font-size: 21px;
}

.give-grid strong {
  color: #5b685b;

  font-size: 8px;
}

.beginner-note {
  margin: 25px 0;
  padding: 19px;

  border-radius: 13px;

  background: #e9e5ff;

  color: #5e5470;

  font-family: "Patrick Hand";
  font-size: 17px;

  text-align: center;
}


/* ==========================================================
   COFFEE SCENE
========================================================== */

.coffee-scene {
  position: relative;

  height: 210px;

  margin: 27px 0;

  overflow: hidden;

  border-radius: 16px;

  background:
    linear-gradient(
      #d7efff,
      #ffe3ed 65%,
      #f4cfa9
    );
}

.coffee-table {
  position: absolute;

  left: 45px;
  bottom: 28px;

  width: 170px;
  height: 13px;

  border-radius: 10px;

  background: #9e715f;
}

.coffee-cup {
  position: absolute;

  left: 65px;
  bottom: 13px;

  width: 50px;
  height: 47px;

  border: 3px solid #605162;
  border-radius: 4px 4px 15px 15px;

  background: #f3b59a;
}

.coffee-cup::after {
  position: absolute;

  top: 8px;
  right: -18px;

  width: 19px;
  height: 24px;

  border: 5px solid #605162;
  border-left: 0;
  border-radius: 0 50% 50% 0;

  content: "";
}

.steam-one,
.steam-two {
  position: absolute;

  top: -30px;

  width: 2px;
  height: 22px;

  background: rgba(81,69,85,.25);
}

.steam-one {
  left: 15px;

  transform: rotate(8deg);
}

.steam-two {
  right: 15px;

  transform: rotate(-7deg);
}

.tiny-book {
  position: absolute;

  left: 5px;
  bottom: 13px;

  width: 45px;
  height: 9px;

  background: #8b79bb;

  box-shadow:
    0 -8px 0 #ee8eae;
}

.coffee-window {
  position: absolute;

  right: 33px;
  top: 25px;

  width: 200px;
  height: 150px;

  border: 6px solid rgba(255,255,255,.65);
  border-radius: 13px;

  background:
    linear-gradient(
      #cde8ff,
      #f2e0ff
    );
}

.coffee-window > span {
  position: absolute;

  bottom: 18px;

  width: 35px;
  height: 55px;

  border-radius: 18px 18px 4px 4px;

  background: #756c8f;
}

.person-one {
  left: 25px;
}

.person-two {
  left: 80px;

  height: 72px !important;

  background: #c2779a !important;
}

.person-three {
  right: 20px;

  background: #799683 !important;
}


/* ==========================================================
   WORLD
========================================================== */

.world-note {
  margin: 27px 0;
  padding: 21px;

  border-radius: 14px;

  display: flex;
  align-items: center;

  gap: 13px;

  background: #e8f3ff;
}

.world-note > span {
  font-size: 29px;
}

.world-note p {
  margin: 0;

  color: #505e68;

  font-family: "Patrick Hand";
  font-size: 18px;
}


/* ==========================================================
   GIVING MATH
========================================================== */

.giving-math {
  margin: 28px 0;

  display: grid;

  grid-template-columns: 1fr 1fr;

  gap: 10px;
}

.normal-math,
.weird-math {
  padding: 21px;

  border-radius: 14px;
}

.normal-math {
  background: #fff0df;
}

.weird-math {
  background: #e8f4e6;
}

.giving-math small {
  color: #92888f;

  font-family: "DM Mono";
  font-size: 6px;
}

.giving-math strong {
  display: block;

  margin-top: 8px;

  color: #554d55;

  font-family: "DM Mono";
  font-size: 10px;
}

.generosity-question {
  margin: 29px 0;
  padding: 25px;

  border-radius: 15px;

  color: white;

  background:
    linear-gradient(
      135deg,
      #618d6a,
      #769b73
    );

  text-align: center;
}

.generosity-question > small {
  color: rgba(255,255,255,.65);
}

.generosity-question p {
  margin: 9px 0 14px;

  font-family: "Patrick Hand";
  font-size: 19px;
}

.better-tags {
  display: flex;
  flex-wrap: wrap;

  justify-content: center;

  gap: 6px;
}

.better-tags span {
  padding: 6px 9px;

  border-radius: 50px;

  color: #53705b;
  background: rgba(255,255,255,.87);

  font-size: 7px;
}


/* ==========================================================
   COMPASSION
========================================================== */

.compassion-line {
  margin: 28px 0;
  padding: 22px;

  border-radius: 14px;

  display: flex;
  align-items: center;

  gap: 13px;

  background:
    linear-gradient(
      135deg,
      #ffe4ed,
      #fff0e5
    );
}

.compassion-line > span {
  color: #db6f98;

  font-size: 27px;
}

.compassion-line p {
  margin: 0;

  color: #644e5b;

  font-family: "Patrick Hand";
  font-size: 18px;
}


/* ==========================================================
   GIFT / DRESS
========================================================== */

.gift-card {
  margin: 28px 0;
  padding: 21px;

  border-radius: 15px;

  display: flex;
  align-items: center;

  gap: 22px;

  background:
    linear-gradient(
      135deg,
      #f0eaff,
      #ffe9f1
    );
}

.dress-illustration {
  position: relative;

  width: 72px;
  height: 100px;

  flex: 0 0 auto;
}

.dress-top {
  position: absolute;

  top: 4px;
  left: 21px;

  width: 32px;
  height: 37px;

  border-radius: 10px 10px 2px 2px;

  background: #df739e;
}

.dress-top::before,
.dress-top::after {
  position: absolute;

  top: -2px;

  width: 17px;
  height: 32px;

  background: #df739e;

  content: "";
}

.dress-top::before {
  left: -10px;

  transform: rotate(35deg);
}

.dress-top::after {
  right: -10px;

  transform: rotate(-35deg);
}

.dress-skirt {
  position: absolute;

  top: 33px;
  left: 7px;

  width: 60px;
  height: 65px;

  background:
    linear-gradient(
      #e981ab,
      #c96fa2
    );

  clip-path:
    polygon(
      35% 0,
      65% 0,
      100% 100%,
      0 100%
    );
}

.gift-card small {
  color: #97708f;

  font-family: "DM Mono";
  font-size: 6px;
}

.gift-card p {
  margin: 7px 0 0;

  color: #5c4d5c;

  font-family: "Patrick Hand";
  font-size: 18px;
}

.remembered-note {
  width: fit-content;

  margin: 25px auto;
  padding: 15px 22px;

  border-radius: 10px;

  color: #735568;
  background: #ffe7a6;

  box-shadow:
    3px 4px 0 #eee0b5;

  font-family: "Patrick Hand";
  font-size: 18px;

  transform: rotate(-2deg);
}


/* ==========================================================
   FOOD
========================================================== */

.food-note {
  margin: 27px 0;
  padding: 22px;

  border-radius: 14px;

  display: flex;
  align-items: center;

  gap: 14px;

  background: #fff0dd;
}

.food-note > span {
  font-size: 30px;
}

.food-note p {
  margin: 0;

  color: #675255;

  font-family: "Patrick Hand";
  font-size: 19px;
}


/* ==========================================================
   LISTEN
========================================================== */

.listen-first {
  margin: 27px 0;
  padding: 25px;

  border-radius: 15px;

  display: flex;
  align-items: center;
  justify-content: center;

  gap: 15px;

  color: white;

  background:
    linear-gradient(
      135deg,
      #6860ad,
      #9b6ca9
    );
}

.listen-icon {
  font-size: 29px;
}

.listen-first p {
  margin: 0;

  font-family: "Patrick Hand";
  font-size: 22px;

  line-height: 1.08;
}


/* ==========================================================
   INTERESTING PERSON
========================================================== */

.interesting-person {
  margin: 29px 0;
  padding: 24px;

  border: 1px solid #ddd6e3;
  border-radius: 15px;

  background: #fffafd;
}

.interesting-person p {
  margin: 10px 0;

  color: #706875;

  font-size: 9px;
}

.interesting-person strong {
  display: block;

  color: #5d4c60;

  font-family: "Patrick Hand";
  font-size: 20px;

  text-align: center;
}


/* ==========================================================
   RESPECT
========================================================== */

.transaction {
  margin: 25px 0;
  padding: 17px;

  border-radius: 13px;

  display: flex;
  align-items: center;
  justify-content: center;

  gap: 12px;

  color: #715d68;
  background: #fff0e4;

  font-family: "Patrick Hand";
  font-size: 16px;
}

.transaction span {
  color: #b28291;
}

.respect-rules {
  margin: 27px 0;

  border: 1px solid #ddd6e2;
  border-radius: 14px;

  overflow: hidden;
}

.respect-rules > div {
  padding: 15px 17px;

  border-bottom: 1px dashed #ddd5df;

  display: grid;

  grid-template-columns: 34px 1fr;

  gap: 9px;

  color: #5f5964;

  font-size: 9px;
}

.respect-rules > div:last-child {
  border: 0;
}

.respect-rules span {
  color: #9074b5;

  font-family: "DM Mono";
  font-size: 7px;
}

.not-weak {
  margin: 27px 0;
  padding: 22px;

  border-left: 4px solid #df749b;

  color: #64545d;
  background: #fff0f5;

  font-family: "Patrick Hand";
  font-size: 18px;

  line-height: 1.2;
}

.not-weak strong {
  color: #934f70;
}


/* ==========================================================
   THREE SUMMARY
========================================================== */

.three-summary {
  margin: 28px 0;

  display: grid;

  grid-template-columns:
    repeat(3,1fr);

  gap: 9px;
}

.summary-card {
  min-height: 145px;

  padding: 17px;

  border-radius: 14px;

  text-align: center;
}

.confidence-summary {
  background: #e7e3ff;
}

.generosity-summary {
  background: #e7f4e5;
}

.compassion-summary {
  background: #ffe4ed;
}

.summary-card > span {
  display: block;

  margin-bottom: 9px;

  font-size: 25px;
}

.summary-card small,
.summary-card strong {
  display: block;
}

.summary-card small {
  color: #817a87;

  font-family: "DM Mono";
  font-size: 6px;
}

.summary-card strong {
  margin-top: 8px;

  color: #554d58;

  font-family: "Patrick Hand";
  font-size: 15px;

  line-height: 1.1;
}


/* ==========================================================
   BALANCE
========================================================== */

.balance-grid {
  margin: 27px 0;

  display: grid;

  gap: 8px;
}

.balance-grid > div {
  padding: 15px;

  border-radius: 12px;

  background: #f5f1f8;
}

.balance-grid small {
  color: #918894;

  font-family: "DM Mono";
  font-size: 6px;
}

.balance-grid strong {
  display: block;

  margin-top: 5px;

  color: #5f5662;

  font-size: 9px;
}

.balance-final {
  margin: 28px 0;
  padding: 24px;

  border-radius: 15px;

  color: white;

  background:
    linear-gradient(
      135deg,
      #625eab,
      #866aa9 55%,
      #bd719b
    );
}

.balance-final p {
  margin: 9px 0;

  font-family: "Patrick Hand";
  font-size: 18px;
}

.balance-final strong {
  color: #ffe7a8;
}


/* ==========================================================
   NIGHT CHECK
========================================================== */

.night-check {
  position: relative;

  margin: 35px 0;
  padding: 28px;

  border-radius: 17px;

  color: #eee9ff;

  background:
    linear-gradient(
      145deg,
      #282742,
      #4e4167
    );
}

.night-moon {
  position: absolute;

  top: 17px;
  right: 20px;

  color: #ffe08e;

  font-size: 31px;
}

.night-check > small {
  color: #b9afc9;
}

.night-question {
  padding: 16px 0;

  border-bottom: 1px solid rgba(255,255,255,.1);

  display: grid;

  grid-template-columns: 38px 1fr;

  gap: 9px;
}

.night-question:last-child {
  border: 0;
}

.night-question > span {
  color: #d2c3ff;

  font-family: "DM Mono";
  font-size: 7px;
}

.night-question p {
  margin: 0;

  font-family: "Patrick Hand";
  font-size: 16px;

  line-height: 1.15;
}


/* ==========================================================
   FINAL SAVE
========================================================== */

.final-save {
  margin: 32px 0;

  overflow: hidden;

  border-radius: 16px;

  background: #292740;

  box-shadow:
    0 15px 31px rgba(35,29,59,.16);
}

.final-save > small {
  display: block;

  padding: 12px 15px;

  color: #aaa3b9;
  background: #35324d;
}

.final-save code {
  padding: 22px;

  display: flex;
  flex-direction: column;

  color: #d8d0f5;

  font-family: "DM Mono";
  font-size: 9px;

  line-height: 1.7;
}

.final-save code span:nth-child(1) {
  color: #b9a8ff;
}

.final-save code span:nth-child(2) {
  color: #9fd49e;
}

.final-save code span:nth-child(3) {
  color: #f1a4be;
}

.three-finish {
  background:
    linear-gradient(
      135deg,
      #fff8e8,
      #eaf4e8,
      #eeeaff
    );
}


/* ==========================================================
   NEXT THOUGHT
========================================================== */

.next-thought {
  margin-top: 25px;
  padding: 20px;

  border-radius: 14px;

  display: flex;
  align-items: center;

  gap: 13px;

  background: #f4f1fa;
}

.next-thought > span {
  color: #e1a548;

  font-size: 23px;
}

.next-thought p {
  margin: 5px 0;

  color: #706978;

  font-family: "Patrick Hand";
  font-size: 15px;
}

.next-thought strong {
  color: #695471;

  font-size: 9px;
}


/* ==========================================================
   TRANSITION
========================================================== */

.reflection-enter-active,
.reflection-leave-active {
  transition: .25s ease;
}

.reflection-enter-from,
.reflection-leave-to {
  opacity: 0;

  transform: translateY(-5px);
}


/* ==========================================================
   MOBILE
========================================================== */

@media (max-width: 600px) {

  .three-hero {
    min-height: 540px;
  }

  .three-question-card {
    top: 24px;
    left: 16px;
    right: 16px;

    width: auto;

    padding: 18px;
  }

  .three-question-card > p {
    font-size: 16px;
  }

  .value-orbit {
    width: 105px;
    height: 105px;

    border-radius: 30px;
  }

  .value-icon {
    width: 38px;
    height: 38px;

    font-size: 17px;
  }

  .value-orbit strong {
    font-size: 12px;
  }

  .value-orbit small {
    display: none;
  }

  .confidence-orbit {
    left: 15px;
    right: auto;
    bottom: 31px;
  }

  .generosity-orbit {
    left: calc(50% - 52px);
    right: auto;
    bottom: 47px;
  }

  .compassion-orbit {
    top: auto;
    right: 15px;
    bottom: 31px;
  }

  .hero-handwriting {
    display: none;
  }

  .give-grid {
    grid-template-columns:
      repeat(2,1fr);
  }

  .three-summary {
    grid-template-columns: 1fr;
  }

  .summary-card {
    min-height: auto;
  }

  .giving-math {
    grid-template-columns: 1fr;
  }

  .coffee-scene {
    height: 180px;
  }

  .coffee-window {
    right: -25px;

    transform: scale(.8);

    transform-origin: right center;
  }

  .gift-card {
    align-items: flex-start;
  }

  .transaction {
    flex-direction: column;

    gap: 5px;
  }

  .transaction span {
    transform: rotate(90deg);
  }

  .night-check {
    padding: 23px 19px;
  }

  .value-section {
    margin-top: 42px;

    padding: 24px 19px;
  }

  .value-section-heading h2 {
    font-size: 27px !important;
  }

}


/* ==========================================================
   SMALL MOBILE
========================================================== */

@media (max-width: 390px) {

  .value-orbit {
    width: 95px;
    height: 95px;
  }

  .confidence-orbit {
    left: 9px;
  }

  .compassion-orbit {
    right: 9px;
  }

  .generosity-orbit {
    left: calc(50% - 47px);
  }

}
</style>
