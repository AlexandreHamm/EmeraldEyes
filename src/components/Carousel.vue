<script>
import { ref, onMounted } from "@vue/runtime-core";
export default {
    data() {
        return {
        // fc: {},
        members: {}
        }
    },
    async mounted(){
        const response = await fetch('https://xivapi.com/freecompany/9233364398528010620?data=FCM')
        const data = await response.json()
        // this.fc = data.FreeCompany
        this.members = data.FreeCompanyMembers
        // date = new Date(this.fc.Formed * 1000).toLocaleDateString('fr', { year: 'numeric', month: 'long', day: 'numeric' })

        let test = this.members.length

        const timer = ms => new Promise(res => setTimeout(res, ms))

        document.querySelector('.carousel').addEventListener('DOMNodeInserted', async function slide(){
        if(document.querySelectorAll('.profil').length == test)
        for(let i = 0; i < document.querySelectorAll('.profil').length; i++){
            document.querySelector('.carousel').style.opacity = '0'
            setTimeout(() => {
            document.querySelector('.carousel').style.transform = 'translateX(calc((((40vw - 5rem) / 2) * '+ i +') * -1))'
            document.querySelector('.carousel').style.opacity = '1'
            }, 400)
            await timer(5000);
            if(i == (document.querySelectorAll('.profil').length - 1))
            slide();
        }
        });
    }
}
</script>

<template>
    <div class="container">
        <div class="carousel">
            <div class="profil" v-for="member in members" :key="member">
                <a class="pp" href="https://fr.finalfantasyxiv.com/lodestone/character/{{ member.ID }}/" target="_blank">
                    <img class="avatar" :src='member.Avatar' alt="">
                </a>

                <div class="temp">
                    <h3> {{ member.Name }} </h3>
                    <div>
                        <img :src='member.RankIcon' alt="">
                        <span>{{ member.Rank }}</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>

    .container{
        position: fixed;
        right: 0;
        bottom: 0;
        width: calc((40vw - 3rem) / 2);
        /* height: calc((40vw - 5rem) / 2); */
        padding: 2rem;
        background: #fff;
        overflow: hidden;
    }

  .carousel{
    width: auto;
    height: 100%;
    display: flex;
    opacity: 0;
    transition: opacity .4s ease-in-out;
  }

  .carousel > .profil{
    min-width: calc((40vw - 5rem) / 2);
    height: 100%;
    display: flex;
    justify-content: space-around;
    align-items: flex-start;
  }

  .carousel > .profil > div{
    width: 50%;
  }

  .carousel > .profil > .pp{
    display: flex;
    justify-content: center;
    filter: brightness(60%) sepia(1) hue-rotate(121deg) saturate(1000%);
  }

  .carousel > .profil > .temp{
    text-align: center;
    padding: 1rem 0;
    /* color: #fff; */
  }

  .carousel > .profil > .temp > h3{
    font-size: 2rem;
    /* transform: translateX(-12.5%); */
    font-family: 'Gobold';
    text-transform: uppercase;
    letter-spacing: .5px;
  }

  .carousel > .profil > .temp > div{
    display: flex;
    margin: .5rem;
  }

  .carousel > .profil > .temp > div > span{
    margin: auto 1rem;
  }

  .avatar{
    border-radius: 50%;
    /* border: .7rem solid #fff; */
    /* box-shadow: 0 0 2rem #181818; */
    /* filter: contrast(1.2) brightness(1.8); */
    transform: scale(1.1);
  }

</style>