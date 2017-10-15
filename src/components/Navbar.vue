<template>
  <header>
    <img id="logo" src="../assets/logo.png" alt="Sort Tube Logo" >
  </header>
</template>

<script>
export default {
  name: 'navbar'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  header {
    position: fixed;
    width: 100%;
    top: 0;
    height: 55px;
    border-bottom: 2px red solid;
    text-align: center;
  }
  #logo {
    width: 30px;
    position: absolute;
    transform: translateY(50%);
    left: 10px;
  }
</style>
