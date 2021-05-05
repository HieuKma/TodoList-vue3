<template>
  <div id="app">
    <Header />
    <Todos />
  </div>
</template>

<script>
import Header from './components/Header'
import Todos from './components/Todos'

export default {
  name: 'App',
  components: { Header, Todos }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
}
bpdy {
display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  width: 400px;
  margin: 0 auto;
}
</style>
