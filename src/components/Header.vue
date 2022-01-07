<template>
  <header>
    <div class="logo">
      <img src="../assets/logo.svg" alt="Shortly">
    </div>
  </header>

</template>

<script>

export default {

}
</script>


<style lang="scss" scoped>
header{
    width: 100%;
    height: 10vh;
    .logo{
      width: 90%;
      margin: 0 auto;
      padding: 15px 0;
    }
}

@media (max-width:750px){
  header{
    height: 15vh;
  }
}
  
</style>
