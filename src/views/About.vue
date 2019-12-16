<template>
  <div class="about">
    <img alt="gif" src="../assets/1410967177-dragonballzgif-0.gif" />
    <About msg="Fucking page" mmm="123"/>
  </div>
</template>

<script>
// @ is an alias to /src
import About from "@/components/About.vue";
export default {
  name: "about",
  components: {
    About
  }
};
</script>
