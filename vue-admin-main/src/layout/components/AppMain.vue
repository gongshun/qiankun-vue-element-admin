<template>
  <section class="app-main">
    <transition>
      <router-view :key="key" />
    </transition>
    <div id="appContainer"></div>
  </section>
</template>

<script>
import { start } from 'qiankun';

export default {
  name: 'AppMain',
  computed: {
    key() {
      return this.$route.path
    }
  },
  mounted() {
    if(!window.isQiankunStart){
      window.isQiankunStart = true;
      start();
    }
  },
}
</script>

<style scoped>
.app-main {
  /*50 = navbar  */
  min-height: calc(100vh - 50px);
  width: 100%;
  position: relative;
  overflow: hidden;
}
.fixed-header+.app-main {
  padding-top: 50px;
}
</style>

<style lang="scss">
// fix css style bug in open el-dialog
.el-popup-parent--hidden {
  .fixed-header {
    padding-right: 15px;
  }
}
</style>
