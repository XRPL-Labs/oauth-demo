<template>
  <img alt="Vue logo" class="logo" src="./assets/XUMM-oauth-challenge.png" />
  <Front />
</template>

<script>
import Front from './components/Front.vue'

export default {
  name: 'App',
  components: {
    Front
  }
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
div.container {
  max-width: 300px;
  margin: 0 auto;
}
img.logo {
  max-width: 200px;
  padding-bottom: 1.5rem;
  margin-bottom: 0.5rem;
  border-bottom: 2px solid #e0e0e0;
}
button {
  padding: 0.8rem 1rem;
  width: calc(100% - 2rem);
  position: relative;
  margin: 1rem;
  background: rgb(223, 223, 223);
  border: 2px solid transparent;
  border-radius: 0.7rem;
  font-weight: bold;
  font-size: 1.1rem;
  transition: all 0.15s;
}
button:hover {
  background: #3052ff;
  border: 2px solid #8398ff;
  color: #fff;
  cursor: pointer;
  transform: scale(0.98);
}
hr {
  margin-top: 1rem;
  margin-bottom: 1rem;
}
code {
  background: #d9dfff;
  padding: 0.25rem 1rem;
  border-radius: 0.25rem;
}
small {
  display: block;
  color: #3052ff;
  font-weight: 800;
  font-size: 1.1rem;
}
h3 {
  margin: 0.5rem;
}
</style>
