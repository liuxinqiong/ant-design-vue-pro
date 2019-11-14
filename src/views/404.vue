<template>
  <div style="text-align: center">
    <IconFont type="icon-icon-test" style="font-size: 100px"></IconFont>
    <img :src="logo" alt />
  </div>
</template>

<script>
import logo from "@/assets/logo.png";
export default {
  data() {
    return {
      logo
    };
  }
};
</script>

<style></style>
