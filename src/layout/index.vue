<template>
  <div :class="classObj" class="app-wrapper">
    <sidebar :isCollapse="!isSiderbarOpen" class="sidebar-container" />
    <div class="main-container">
      <div>
        <navbar :isActive="isSiderbarOpen" @toggleSideBar="toggleSideBar" />
      </div>
      <app-main />
    </div>
  </div>
</template>

<script>
import { Navbar, Sidebar, AppMain } from "./components";

export default {
  name: "Layout",
  components: {
    Navbar,
    Sidebar,
    AppMain
  },
  data() {
    return {
      isSiderbarOpen: true
    };
  },
  methods: {
    toggleSideBar() {
      this.isSiderbarOpen = !this.isSiderbarOpen;
    }
  },
  computed: {
    classObj() {
      return {
        hideSidebar: !this.isSiderbarOpen,
        openSidebar: this.isSiderbarOpen,
        withoutAnimation: false
      };
    }
  }
};
</script>

<style lang="scss" scoped>
@import "~@/styles/mixin.scss";
@import "~@/styles/variables.scss";

.app-wrapper {
  @include clearfix;
  position: relative;
  height: 100%;
  width: 100%;
}
</style>
