<template>
  <div id="app">
    <my-user @input:user="user = $event" />
    <hr>
    <pre>{{ user }}</pre>
  </div>
</template>

<script>
import MyUser from './components/renderless/MyUser.vue';

export default {
  name: 'app',

  components: {
    MyUser
  },

  data: () => ({
    user: {
      firstName: '',
      lastName: ''
    }
  })
};
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;

  max-width: 60%;
  margin: 60px auto auto;

  hr {
    width: 100%;
    height: 2px;

    margin: 40px auto;
    border: none;
    border-radius: 1px;

    background: #efefef;
  }
}
</style>
