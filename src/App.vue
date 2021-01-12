<template>
  <div id="app">
    <Loading-screen v-if="isLoading" />
    <Home />
  </div>
</template>

<script>
import Home from './components/Home.vue';
import LoadingScreen from './components/Loading-screen.vue';

export default {
  name: 'App',
  components: {
    Home,
    LoadingScreen
  },
  data(){
    return {
      isLoading: true
    }
  },
  mounted (){
    setTimeout(() => {
      this.isLoading = false
    }, 3000)
  }
}
</script>

<style>

  :root{
      font-size: 16px;
      font-weight: normal;
      font-family: Arial, Helvetica, sans-serif;
      line-height: 1.6rem;
  }

 *{
      margin: 0;
      padding: 0;
      border: 0;
      font: inherit;
      vertical-align: baseline;
      list-style: none;

      scroll-behavior: smooth;
  }
  
  #app {
    font-family: Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;

    background: #0f0f0f;
    color: #fff;
  }

  body::-webkit-scrollbar {
    width: .7em;
    background: #0f0f0f;
  }

  body::-webkit-scrollbar-track {
    box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  }

  body::-webkit-scrollbar-thumb {
    background-color:  #2b2828;
    outline: 1px solid cyan;
  }
</style>
