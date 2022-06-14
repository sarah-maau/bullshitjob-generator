<template>
  <header class="header">
    <div
      class="header__inner"
      :style="'border-color:' + textColor + ';'"
      >
        <h1
        :style="'color:' + textColor + ';'"
        class="header__title"> Bullshit Job Titles Generator</h1>
      </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderComponent',
  props: ['textColor'],
};

</script>

<style lang="scss">
    .header {
      font-size: .8rem;
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      text-align: left;
      padding: 2rem .5rem 0 .5rem;
      z-index: 2;
      .header__inner {
        display: flex;
        padding-top: 0.3em;
        border-top: 2px solid;
        justify-content: space-between;
      }
    }

</style>
