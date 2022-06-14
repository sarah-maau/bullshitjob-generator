<template v-if="this.jobTitle">
    <h1 v-html="this.jobTitle"></h1>
  <button @click="this.getJobTitle()">click</button>

</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      jobTitle: undefined,
    };
  },
  created() {
    this.getJobTitle();
  },
  methods: {
    getJobTitle() {
      this.jobTitle = undefined;
      this.axios.get('https://bullshit-job-title-generator.herokuapp.com/api/bullshit').then((response) => {
        this.jobTitle = response.data;
      });
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
