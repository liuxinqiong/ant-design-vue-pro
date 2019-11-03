<template>
  <div>
    <a-layout
      :class="[`nav-theme-${navTheme}`, `nav-layout-${navLayout}`]"
      id="components-layout-demo-side"
      style="min-height: 100vh"
    >
      <a-layout-sider
        v-if="navLayout === 'left'"
        :theme="navTheme"
        collapsible
        v-model="collapsed"
        :trigger="null"
      >
        <div class="logo">Ant Design Vue Pro</div>
        <SiderMenu></SiderMenu>
      </a-layout-sider>
      <a-layout>
        <a-layout-header style="background: #fff; padding: 0">
          <a-icon
            class="trigger"
            :type="collapsed ? 'menu-unfold' : 'menu-fold'"
            @click="collapsed = !collapsed"
          ></a-icon>
          <Header></Header>
        </a-layout-header>
        <a-layout-content style="margin: 0 16px">
          <router-view></router-view>
        </a-layout-content>
        <a-layout-footer style="text-align: center">
          <Footer></Footer>
        </a-layout-footer>
      </a-layout>
    </a-layout>
    <SettingDrawer></SettingDrawer>
  </div>
</template>

<script>
import Header from "./Header";
import Footer from "./Footer";
import SiderMenu from "./SiderMenu";
import SettingDrawer from "../components/SettingDrawer";
export default {
  components: {
    Header,
    Footer,
    SiderMenu,
    SettingDrawer
  },
  data() {
    return {
      collapsed: false
    };
  },
  computed: {
    navTheme() {
      return this.$route.query.navTheme || "dark";
    },
    navLayout() {
      return this.$route.query.navLayout || "left";
    }
  }
};
</script>

<style lang="less" scoped>
.trigger {
  padding: 0 20px;
  line-height: 64px;
  font-size: 20px;

  &:hover {
    background-color: #eee;
  }
}

.logo {
  line-height: 64px;
  text-align: center;
}

.nav-theme-dark .logo {
  color: #ffffff;
}
</style>
