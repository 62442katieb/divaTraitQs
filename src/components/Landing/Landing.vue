<!--<template>-->
<!--<div class="landingPage mt-3 pt-3 text-left">-->
<!--<section class="smooth-scroller" style="padding-top: 0">-->
<!--<section style="height: 30vw; min-height: 15rem;-->
<!--background: linear-gradient(#5A478F, #47337D)">-->
<!--<div style="-->
<!--height: 30vw;-->
<!--min-height: 15rem;-->
<!--background-image: url(/static/images/about%20the%20study.svg);-->
<!--background-position: center;-->
<!--background-size: contain;-->
<!--background-repeat: no-repeat">-->
<!--</div>-->
<!--</section>-->
<!--<br>-->
<!--<section>-->
<!--<div class="container">-->
<!--<vue-markdown v-if="content"> {{content}} </vue-markdown>-->
<!--<Loader v-else/>-->
<!--<p style="margin-top: 2rem">-->
<!--<router-link class="join-button" to="/study/intro">Join</router-link>-->
<!--</p>-->
<!--</div>-->
<!--</section>-->
<!--</section>-->
<!--</div>-->
<!--</template>-->

<!--<style>-->
<!--.landingPage img {-->
<!--max-width: 250px;-->
<!--}-->
<!--</style>-->

<!--<script>-->
<!--import axios from 'axios';-->
<!--import VueMarkdown from 'vue-markdown';-->
<!--import Loader from '../Loader';-->

<!--export default {-->
<!--props: {-->
<!--contentSrc: {-->
<!--type: String,-->
<!--},-->
<!--},-->
<!--components: {-->
<!--VueMarkdown,-->
<!--Loader,-->
<!--},-->
<!--data() {-->
<!--return {-->
<!--content: null,-->
<!--};-->
<!--},-->
<!--mounted() {-->
<!--axios.get(this.contentSrc).then((resp) => {-->
<!--this.content = resp.data;-->
<!--});-->
<!--},-->
<!--};-->
<!--</script>-->

<template>
  <div class="docked-layout">
    <section class="smooth-scroller" style="padding-top: 0">
      <section style="height: 30vw; min-height: 15rem; background: linear-gradient(#ffffff, #f4f5f6)">
        <div style="
          height: 30vw;
          min-height: 15rem;
          background-image: url(/static/images/undraw_detailed_examination_joef.svg);
          background-position: center;
          background-size: contain;
          background-repeat: no-repeat">
        </div>
      </section>
      <br>
      <section>
        <div class="container-fluid">
          <h2>Welcome to DIVA Study</h2>
          <p align='justify'>The purpose of the DIVA, or Dense Investigation of Variability of
            Affect, Study is to gain a better understanding of how brain activity
            and emotion vary within individuals and how health and lifestyle
            factors impact this variability. We are asking you to participate
            because you are an adult female between the ages of 18 and 30 years
            old. In this study, you may be asked to complete one or more weekly
            two-hour MRI scans, along with other external tasks, for a total of
            no more than 13 sessions. In addition to MRI scanning and
            task/questionnaire completion, you will be asked to wear an activity
            tracker and submit saliva and speech data samples twice a week
            throughout the duration of the 13-week study.</p>
        </div>
      </section>

      <section>
        <div class="image container">
          <div class="image">
            <BridgeImage style="margin-bottom: -6px" src="/static/images/undraw_Mobile_app_p3ts.svg"/>
          </div>
          <div class="text" style="padding-top: 1rem">
            <h3>Mobile Questionnaires</h3>
            <p align='justify'>Twice a week, you will be prompted by a notification
              on your phone to complete several surveys and answer questions
              online. Questionnaires include information about your mental, emotional,
              and physical states, which may vary from week to week. You do not
              have to answer any questions that make you feel uncomfortable. You
              will be prompted to answer ompleting the surveys will take about 20
              minutes and will be done on your phone.</p>
          </div>
        </div>
      </section>

      <section>
        <div class="image container">
          <div class="image">
            <BridgeImage style="padding-top: 1.5rem" src="/static/images/undraw_activity_tracker_1l9o.svg"/>
          </div>
          <div class="text">
            <h3>Affective Variability in Life</h3>
            <p>In addition to answering questions about your mental, emotional, and
              physical states, you will be asked to wear a fitness tracker throughout
              the coures of the study to monitor your heart rate, activity, and sleep.
              This information will help us understand what aspects of life affect
              your mood.
            </p>
          </div>
        </div>
      </section>

      <section>
        <div class="image container">
          <div class="image">
            <BridgeImage style="padding-bottom: 1rem" src="/static/images/undraw_inspection_9phc.svg"/>
          </div>
          <div class="text">
            <h3>Get started!</h3>
            <p>In just a minute you can decide whether or not you'd like to
              participate. Let's go!
            </p>

            <p style="margin-top: 2rem">
              <router-link class="join-button" to="/study/intro">Join</router-link>
            </p>
            <!--<div class="container">-->
            <!--<vue-markdown v-if="content"> {{content}} </vue-markdown>-->
            <!--<Loader v-else/>-->
            <!--</div>-->
          </div>
        </div>
      </section>
    </section>
  </div>
</template>

<script>

import axios from 'axios';
import VueMarkdown from 'vue-markdown';
import Loader from '../Loader';

export default {
  name: 'Landing',
  props: {
    contentSrc: {
      type: String,
    },
  },
  components: {
    VueMarkdown,
    Loader,
  },
  data() {
    return {
      content: null,
    };
  },
  mounted() {
    axios.get(this.contentSrc).then((resp) => {
      this.content = resp.data;
    });
  },
};
</script>

<style scoped>
  h1 {
    font-size: 1.2rem;
    margin: 0;
    padding: 0;
    color: #;
  }
  h2 {
    color: #254588;
    text-align: center;
    margin: 1rem 0 .5rem 0;
  }
  h3 {
    color: #254588;
    margin: 0;
    margin-bottom: .25rem;
  }
  p {
    line-height: 1.5;
    color: #1A1C29;
    margin: 0;
    margin-bottom: 1rem;
  }
  blockquote {
    margin-left: 1rem;
    margin-right: 0;
    font-size: .8rem;
  }
  button {
    border: none;
  }

  section:nth-child(odd) {
    width: 100%;
    background-color: rgba(238, 238, 238, 0.3);
  }
  .container {
    max-width: 30rem;
    margin: 0 auto;
    padding: 1.5rem;
  }
  .image.container {
    max-width: 60rem;
    padding: 1rem 1rem 0 1rem;
    display: flex;
    align-items: center;
  }
  .image.container .image {
    align-self: flex-end;
  }
  .image.container .image img {
    width: 15rem;
  }
  .image.container .text {
    margin-left: 2rem;
  }
  .image.container .text h2 {
    color: #254588;
  }
  .image.container .text h3 {
    color: #245588;
  }
  .image.container .text p {
    font-size: .9rem;
  }
  img {
    width: 100%;
  }
  .join-button {
    background-color: #eafc40;
    color: #1A1C29!important;
    border-radius: 100px;
    border: none;
    display: inline-block;
    margin: .2rem 0;
    padding: .4rem 1.6rem;
    text-decoration: none;
    font-weight: bold;
  }
  .grayscale {
    opacity: .4;
  }

  /* Layout of general HTML content */
  ol, ul {
    margin: 0;
    margin-bottom: 1rem;
    padding: 0 0 0 1.3rem;
  }
  table {
    width: 100%;
  }
  td {
    vertical-align: top;
  }
  li {
    margin-top: .75rem;
    margin-bottom: .75rem;
  }
  /* Consent as displayed in a viewer that can be maximized to view. */
  .maximized {
    position: absolute;
    top: 0px;
    left: 0px;
    right: 0px;
    bottom: 0px;
    z-index: 2;
    background-color: white;
    overflow: hidden;
    -webkit-overflow-scrolling: touch;
  }
  .min-max-control {
    bottom: 0;
    cursor: pointer;
    position: absolute;
    right: 0;
    width: 2rem;
    height: 2rem;
    z-index: 1;
    border-radius: 2px;
  }
  .opener {
    background: transparent url(/static/images/Maximize.svg) center center no-repeat;
    background-size: contain;
  }
  .closer {
    background: transparent url(/static/images/Minimize.svg) center center no-repeat;
    background-size: contain;
  }

  nav.basic {
    color: white;
    background-color: rgba(0,0,0,.1);
    display: flex;
    overflow: hidden;
    justify-content: space-between;
    align-items: center;
    padding-left: 1rem;
    padding-right: 1rem;
  }
  nav.basic > div {
    height: 2.2rem;
    line-height: 2.2rem;
    padding: .25rem 0rem;
  }
  nav.basic a {
    background-color: white;
    padding: .4rem 1rem;
    border-radius: 1rem;
    font-size: .7rem;
  }

  /* DOCKED LAYOUT (header annd footer at top and bottom of viewport,
  center elements each scroll) */
  .docked-layout {
    display: flex;
    flex-direction: column;
    height: 100%;
    box-sizing: border-box;
  }
  .docked-layout > section {
    flex: 1;
    overflow-y: auto;
    position: relative;
  }
  .docked-layout > section.smooth-scroller {
    -webkit-overflow-scrolling: touch;
  }

  @media screen and (max-width: 50em) {
    .image.container {
      flex-direction: column;
      padding-top: 1rem;
    }
    .image.container .image {
      margin: 0 auto;
    }
    .image.container .text {
      margin: 1rem;
    }
  }
  @media screen and (min-width: 40em) {
    html, body {
      font-size: 20px;
    }
  }
</style>
