<template>
  <div class="home">
    <div>
      <router-link :class="[$style.start]" to="/questions"
        >ゲームを始める</router-link
      >
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import foodList from '@/components/foodList.vue'

export default {
  name: "HomeView",
  components: {},
};
</script>

<style module>
.start {
  background-color: #fff;
  width: 200px;
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border-radius: 5px;
  font-size: 20px;
  font-weight: bold;
  cursor: pointer;
  text-decoration: none;
}
</style>
