<template>
  <header class="header">
    <h1><span class="t">T</span><span class="o">o</span><span class="d">d</span><span class="o">o</span><span class="d">L</span><span class="i">i</span><span class="s">s</span><span class="t">t</span></h1>
    <div>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header"
}
</script>

<style scoped>
  .header {
    background: #333;
    color: #fff;
    text-align: center;
    padding: 10px;
  }

  .header h1 {
    -webkit-text-stroke: 1px white;
  }

  .t {
    color: yellow;
  }

  .o {
    color: limegreen;
  }

  .d {
    color: blue;
  }

  .i {
    color: red;
  }

  .s {
    color: orange;
  }

  .header a {
    color: #fff;
    padding-right: 5px;
    text-decoration: none;
  }

  .header a.router-link-exact-active {
    color: #42b983;
  }
</style>