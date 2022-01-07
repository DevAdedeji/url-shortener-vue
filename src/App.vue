<template>
  <Header />
  <Hero />
  <LinkInputContainer />
  <Footer />
</template>

<script>
import Header  from '../src/components/Header.vue'
import Hero  from '../src/components/Hero.vue'
import LinkInputContainer  from '../src/components/LinkInputContainer.vue'
import Footer  from '../src/components/Footer.vue'

export default {
  name: 'App',
  components: {Header, Hero,LinkInputContainer, Footer}
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Lexend+Deca&family=Poppins:wght@500&family=Public+Sans:wght@300&display=swap');
*, body{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}
</style>
