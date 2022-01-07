<template>
  <section>
      <div class="hero-container">
          <div class="hero-text">
              <h1>Make your links shorter</h1>
              <p>Build your brand's recognition and get detailed insights by having your links shorter.</p>
          </div>
          <div class="hero-asset">
              <img src="../assets/illustration-working.svg" alt="illustration-working-svg">
          </div>
      </div>
  </section>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
section{
    width: 100%;
    min-height: 80vh;
    .hero-container{
        width: 90%;
        margin: 0 auto;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 30px;
        .hero-text{
            width: 100%;
            h1{
                font-size: 60px;
                color: hsl(255, 11%, 22%);
            }
            p{
                color:  hsl(257, 7%, 63%);
                width: 70%;
            }
        }
        .hero-asset{
            width: 90%;
            img{
                width: 100%;
            }
        }
    }
}


@media (max-width:950px){
    section{
        .hero-container{
            .hero-text{
                h1{
                    font-size: 45px;
                }
            }
        }
    }
}
@media (max-width:750px){
    section{
        min-height: 100vh;
        .hero-container{
            flex-direction: column;
            .hero-text{
                order: 2;
                text-align: center;
                p{
                    width: 100%;
                    padding-top: 10px;
                    font-size: 18px;
                }
            }
            .hero-asset{
                order: 1;
                padding-top: 20px;
                display: flex;
                align-items: center;
                justify-content: center;
                img{
                    width: 100%;
                }
            }
        }
    }
}

@media (max-width:500px){
    section{
        min-height: 75vh;
    }
}


</style>