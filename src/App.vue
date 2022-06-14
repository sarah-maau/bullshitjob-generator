<template v-if="this.jobTitle">
  <HeaderComponent :textColor="this.textColor"/>
  <main class="main">
    <div class="container">
      <h2
        class="title"
        v-html="this.jobTitle"
        :style="'color:' + this.textColor + ';'"
        >
      </h2>
      <div class="icon">
 <RefreshIcon
        class="icon__refresh"
          :style="'color:' + this.textColor + ';'"
          @click="this.getJobTitle(); this.changeColor()"
        />

      </div>
    </div>
  </main>
</template>

<script>
import { RefreshIcon } from '@iconicicons/vue3';
import HeaderComponent from './components/Header.vue';

export default {
  name: 'App',
  components: { HeaderComponent, RefreshIcon },
  data() {
    return {
      jobTitle: undefined,
      textColor: `#${Math.floor(Math.random() * 16777215).toString(16)}`,
    };
  },
  created() {
    document.body.style.background = `#${Math.floor(Math.random() * 16777215).toString(16)}`;
    this.getJobTitle();
  },
  methods: {
    getJobTitle() {
      this.jobTitle = undefined;
      this.axios.get('https://bullshit-job-title-generator.herokuapp.com/api/bullshit').then((response) => {
        this.jobTitle = response.data;
      });
    },
    changeColor() {
      const randomTextColor = Math.floor(Math.random() * 16777215).toString(16);
      const randomBackgroundColor = Math.floor(Math.random() * 16777215).toString(16);
      document.body.style.background = `#${randomBackgroundColor}`;
      this.textColor = `#${randomTextColor}`;
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: 'Bebas Neue', cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 60px;
}

.main {
  display: flex;
  align-items: center;
  padding: 5rem auto;
  z-index: 1;
  position: relative;
  margin: .5rem auto;
  .container {
    width: 100%;
    display: block;
    padding: auto .7rem;
    .title {
      display: block;
      width: 100%;
      line-height: .95;
      font-size: 10rem;
    }
    .icon {
      position:fixed;
      bottom: 0;
      width: 100%;
        .icon__refresh {
          float: right;
          width: 10rem;
          height: 10rem;
          cursor: pointer;
        }
    }

  }
}
</style>
