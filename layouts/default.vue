<template>
  <div>
    <Header></Header>
    <Nuxt />
    <Footer></Footer>
  </div>
</template>

<script>
import Header from '../components/App/Header.vue'
import Footer from '../components/App/Footer.vue'
import Menu from '../components/App/Menu.vue'
export default {
  components: {
    Header,
    Footer,
    Menu
  },
  data() {
    return {
    };
  },

  methods: {
  },
} 
</script>
<style>
.body-app {
  display: flex;
  width: 100%;
  padding: 0 5%;
  background-color: #f0f0f0;
}

.menu-app {
  width: 20%;
  min-height: 500px;
}

.main-app {
  width: 80%;
  min-height: 500px;
}
</style>
