<template>
  <div>
    <h1>
      <span>
        <img alt="Vue logo" src="../../assets/logo.png">
      </span>ue
      <span class="logo-inverted">
        <img alt="Vue logo" src="../../assets/logo.png">
      </span>pp
    </h1>
  </div>
</template>

<script>
export default {
  name: "AppHeader"
};
</script>

<style scoped>
h1 {
  /* background-color: #3a5169; */
  color: white;
  text-align: center;
}
img {
  height: 25px;
  width: 20px;
}
.logo-inverted img {
  transform: rotate(180deg);
}
</style>

