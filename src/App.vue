<template>
    <navTop class="nav"></navTop>
    <div class="background">
      <img :src="imgSrc" alt=""/>
    </div>
    <router-view class="content2" />
</template>

<script>
import navTop from "@/components/common/navTop.vue";
export default {
  components: {
    navTop,
  },
  data() {
    return {
      imgSrc: "/webstatic/background.jpg",
    };
  },
};
</script>

<style scoped>
.background {
  width: 100%;
  height: 98%;
  z-index: -1;
  position: absolute;
}
.background img {
    width: 100%;
    height: 100%;
}

.content2 {
  position: absolute;
  top: 10%;
  bottom: 5%;
  left: 0;
  right: 0;
  z-index: 1;
  height: 100%; /* 设置 .content2 的高度为 90% */
}

.nav {
  -webkit-backdrop-filter: blur(10px);
  backdrop-filter: blur(10px);
  width: 100%;
  height: 10%;
  z-index: 1;
  position: absolute;
}
</style>
