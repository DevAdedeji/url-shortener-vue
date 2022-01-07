<template>
  <footer>
    <div>
        <img src="../assets/logo.svg" alt="Shortly">
        <p>Made by Tewogbade Adedeji</p>
    </div>
  </footer>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
footer{
  width: 100%;
  background-color: hsl(260, 8%, 14%);
  padding:20px 0;
    div{
      width: 90%;
      margin: 0 auto;
      display: flex;
      align-items: center;
      justify-content: space-between;
        p{
            color: #fff;
            text-align: center;
        }
    }
}

@media (max-width:550px){
  footer{
    div{
      flex-direction: column;
      gap: 20px;
    }
  }
}
</style>