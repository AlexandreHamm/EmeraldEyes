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

    let membersLength = this.members.length

    const timer = ms => new Promise(res => setTimeout(res, ms))

    document.querySelector('.marquee').addEventListener('DOMNodeInserted', async function slide(){
      // if(document.querySelectorAll('.profil').length == membersLength)
      // for(let i = 0; i < document.querySelectorAll('.profil').length; i++){
      //     document.querySelector('.marquee').style.opacity = '0'
      //     setTimeout(() => {
      //     document.querySelector('.marquee').style.transform = 'translateX(calc((((40vw - 5rem) / 2) * '+ i +') * -1))'
      //     document.querySelector('.marquee').style.opacity = '1'
      //     }, 400)
      //     await timer(5000);
      //     if(i == (document.querySelectorAll('.profil').length - 1))
      //     slide();
      // }
      if(document.querySelectorAll('.profil').length == membersLength)
      document.querySelector('.marquee').animate([
          {transform: 'translateX(25vw)'},
          {transform: 'translateX(calc(-'+ membersLength + ' * ((27.5vw - 5rem) / 2) - 50vw))'}
      ],
      {
          duration: 60000,
          // delay: 500,
          iterations: Infinity
      });
    });
  }
}
</script>

<template>
  <div class="container">
    <div class="marquee">
      <div class="profil" v-for="member in members" :key="member">
        <a class="pp" :href="'https://fr.finalfantasyxiv.com/lodestone/character/' + member.ID + '/'" target="_blank">
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
  position: absolute;
  left: 50%;
  bottom: 2rem;
  transform: translateX(-50%);
  width: 50%;
  height: 6rem;
  padding: .5rem;
  /* background: #fff; */
  overflow: hidden;
}

.marquee{
  width: auto;
  height: 100%;
  display: flex;
  transform: translateX(25vw);
  /* opacity: 0;
  transition: opacity .4s ease-in-out; */
  /* animation: marquee 10s linear infinite; */
}

.marquee > .profil{
  min-width: 60%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: flex-start;
}

.marquee > .profil > div{
  width: 50%;
}

.marquee > .profil > .pp{
  display: flex;
  justify-content: center;
  filter: brightness(60%) sepia(1) hue-rotate(121deg) saturate(1000%);
}

.marquee > .profil > .temp{
  width: 100%;
  margin: .5rem;
  /* text-align: center; */
  /* padding: 1rem 0; */
  color: #fff;
}

.marquee > .profil > .temp > h3{
  font-size: 1.7rem;
  /* transform: translateX(-12.5%); */
  /* font-family: var(--gobold); */
  text-transform: uppercase;
  letter-spacing: .5px;
}

.marquee > .profil > .temp > div{
  display: flex;
  margin: .5rem;
  text-align: center;
}

.marquee > .profil > .temp > div > span{
  margin: auto 1rem;
}

.avatar{
  border-radius: 50%;
  height: 5rem;
  /* border: .7rem solid #fff; */
  /* box-shadow: 0 0 2rem #181818; */
  /* filter: contrast(1.2) brightness(1.8); */
  /* transform: scale(1.1); */
}


.container:before, .container:after {
  position: absolute;
  top: 0;
  width: 10rem;
  height: 100%;
  content: "";
  z-index: 10;
}
.container:before {
  left: 0rem;
  background: linear-gradient(to right, #181818 0%, #181818 50%,transparent 100%);
}
.container:after {
  right: -1rem;
  background: linear-gradient(to left, #181818 0%, #181818 50%,transparent 100%);
}
</style>