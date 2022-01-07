<template>
  <section>
    <div class="input-link-container">
        <div class="con">
            <input type="text" placeholder="Shorten a link here" ref="input">
            <button @click="shorten" ref="shorten">Shorten it!</button>
        </div>
        <p ref="error"></p>
    </div>
    <div v-show="links">
        <div class="link" v-for="link in links" :key="link.id">
            <p id="link">{{link.link}}</p>
            <div class="imp">
                <p id="shortenedlink">{{link.shortenedLink}}</p>
                <button @click="copy(link.id)" ref="copy" :class="[link.copy ? 'copied': '']">{{link.copy? 'Copied' : 'Copy'}}</button>
            </div>
        </div>
    </div>
  </section>
</template>

<script>
import axios from 'axios'

export default {
    data(){
        return{
            CurrentLink: '',
            links: [],
        }
    },
    methods:{
        getRandomID(){
            const num = Math.floor(Math.random() * (101))
            return num;
        },
        shorten(){
            let link = "https://api.shrtco.de/v2/shorten?url="
            if(this.$refs.input.value){
                this.$refs.shorten.textContent = "Loading....."
                link = link + this.$refs.input.value
                this.CurrentLink = this.$refs.input.value
                axios.get(link)
                .then(res => {
                    let result = {
                        id: this.getRandomID(),
                        copy: false,
                        link: `${this.CurrentLink}`, 
                        shortenedLink: `${res.data.result.full_short_link}`}
                    this.links.push(result)
                    this.$refs.input.value = ""
                    this.$refs.shorten.textContent = "Shorten it!"  
                }
                )
                .catch(err => {this.$refs.error.textContent = "Invalid link";
                this.$refs.input.value = "";}
                )
            }else{
                this.$refs.error.textContent = "Please add a link"
            }
        },
        copy(id){
            let clink = this.links.filter(link =>
                {if(link.id == id){
                    return link
                }}
            )
           navigator.clipboard.writeText(clink[0].shortenedLink);
           clink[0].copy = true;
        }
    }
}
</script>

<style lang="scss" scoped>
.copied{
    background-color: hsl(257, 27%, 26%) !important;
}
section{
    width: 100%;
    background-color: hsl(0, 0%, 75%);
    padding: 20px;
    min-height:30vh;
    .input-link-container{
        width: 90%;
        padding: 30px 0;
        margin: 0 auto;
        background: hsl(257, 27%, 26%);
        border-radius: 10px;
        .con{
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            input{
                width: 60%;
                height: 40px;
                border: none;
                outline: none;
                padding-left: 20px;
                border-radius: 5px;
            }
            input:focus{
                border: 1px solid hsl(0, 87%, 67%);
            }
            input::placeholder{
                color: hsl(0, 87%, 67%);
            }
            button{
                width: 15%;
                height: 40px;
                border: none;
                outline: none;
                border-radius: 5px;
                background-color: hsl(180, 66%, 49%);
                color: #fff;
                cursor: pointer;
            }
            button:hover{
                text-decoration: underline;
            }
        }
        p{
            width: 75%;
            margin: 0 auto;
            color: hsl(0, 87%, 67%);
            padding-top: 10px;
            font-style: italic;
        }
    }
    .link{
        width: 90%;
        margin: 20px auto;
        border-radius: 10px;
        padding: 20px;
        background-color: #fff;
        display: flex;
        align-items: center;
        justify-content: space-between;
        .imp{
            display: flex;
            align-items: center;
            gap: 20px;
            #shortenedlink{
                color: hsl(180, 66%, 49%);
            }
            button{
                border: none;
                outline: none;
                border-radius: 5px;
                padding: 10px;
                background-color: hsl(180, 66%, 49%);
                color: #fff;
                cursor: pointer;
            }
        }
    }
}
@media (max-width:750px){
    section{
        background-color: #fff;
        padding: 20px 0;
        margin: 0;
        .input-link-container{
            .con{
                flex-direction: column;
                input, button, p{
                    width:90%;
                    margin: 0 auto;
                }
            }
        }
        .link{
            background-color: #fff;
            flex-direction: column;
            gap: 20px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.15);
            #link{
                width:100%;
                border-bottom:1px solid #333;
                padding:10px 0;
            }
            .imp{
                width:100%;
                flex-direction: column;
                align-items: center;
                justify-content: center;
                #shortenedlink{
                    width:100%;
                }
                button{
                    width:100%;
                    margin:0 auto;
                }
            }
        }
    }
}
</style>