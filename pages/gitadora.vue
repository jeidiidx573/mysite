<template>
  <div class="container">
    <div>
      <logo />
      <h1 class="title">
        jeidiidx Lab.
      </h1>
      <navi />
      <div class="cardbox">
       <section class="card" v-for="(item, index) in items" :key="index">
         <img class="card-img" :src='item.img' alt="">
         <div class="card-content">
           <h2 class="card-title">{{ item.title }}</h2>
           <div class="card-topics">
             <div>
               <p class="item-title">artist:</p>
               <p class="item">{{ item.artist }}</p>
             </div>
             <div>
               <p class="item-title">bpm:</p>
               <p class="item">{{ item.bpm }}</p>
             </div>
             <div>
               <p class="item-title">version:</p>
               <p class="item">{{ item.version }}</p>
             </div>
           </div>
         </div>
         <div class="card-link">
           <p>Drum</p>
           <a href="#" class="bas trigger" id="js-trigger" @click="execute">      {{ item.d_bas }}</a>
           <a href="#" class="adv">{{ item.d_adv }}</a>
           <a href="#" class="ext">{{ item.d_ext }}</a>
         </div>
       </section>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Logo from '~/components/Logo.vue'
import Navi from '~/components/Navi.vue'

export default {
  components: {
    Logo,
    Navi
  },
  data () {
    return {
      items: [
        { title: '0時20分のRoulette', artist: '04 Limited Sazabys', bpm: '217', version: 'Matixx', img: 'https://p.eagate.573.jp/game/gfdm/gitadora_exchain/p/eam/playdata/img.html?imgkey=music_skill_gitadora-exchain_MUSIC_INFO&imgid=0&83053065123888274822576331599402', d_bas: '2.85', d_adv: '5.90', d_ext: '7.20' }
      ]
    }
  },
  methods: {
    execute () {
      // 独自イベントclick.triggerを発火
      // bus.$emit('click.trigger');
      this.$store.commit('console', 'hoge')
      console.log(this.$store.state.console)
    },
    getResults () {
      axios.get('https://www.googleapis.com/youtube/v3/search?part=snippet&maxResults=9&q=GITADORA&type=video&key=AIzaSyA25r9qCpM7ZPCw3_D8M7XcocSGFW-m-sk').then((res) => {
        console.log(res.data.items)
        this.items = res.data.items
      }).catch((res) => {
        console.log(res)
      })
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Noto Sans', 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

/* cards */
.cardbox {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin: 0px 50px;
}
.card {
  margin: 30px auto;
  width: 300px;
  background: #fff;
  border-radius: 5px;
  box-shadow: 0 2px 5px #ccc;
}
.card-img {
  border-radius: 5px 5px 0 0;
  max-width: 100%;
  height: auto;
}
.card-content {
  padding: 10px;
}
.card-title {
  font-size: 16px;
  margin-bottom: 10px;
  text-align: center;
  color: #333;
}
.card-topics {
  display: flex;
  flex-direction: column;
  color: #777;
  font-size: 14px;
  line-height: 1.5;
  margin: 0 20px;
  width: 100%;
}
.item-title{
  width: 15%;
  margin-right: 20px;
  display: inline-block;
}
.item{
  display: inline-block;
}

.card-text {
  color: #777;
  font-size: 14px;
  line-height: 1.5;
}
.card-link {
  text-align: center;
  border-top: 1px solid #eee;
  padding: 10px 20px;
  display: flex;
  justify-content: center;
}
.card-link p{
  color: #333;
  padding-bottom: 4px;
  margin: 0 10px;
}
.card-link a{
  text-decoration: none;
  color: #0bd;
  margin: 0 10px;
  display: inline-block;
  padding-bottom: 4px;
  position: relative;
}
.card-link a::after {
  background-color: tomato;
  bottom: 0;
  content: '';
  display: block;
  height: 1px;
  left: 0;
  position: absolute;
  transition: .2s all;
  width: 0;
  left: 50%;
  transform: translateX(-50%);
}
.card-link a:hover::after {
  width: 100%;
}
.card-link a.bas { color: #5297ff; }
.card-link a.bas::after { background-color: #5297ff; }
.card-link a.adv { color: #beaf02; }
.card-link a.adv::after { background-color: #beaf02; }
.card-link a.ext { color: #e10035; }
.card-link a.ext::after { background-color: #e10035; }

.modal {
  position: fixed; top: 0; left: 0;
  width: 100%; height: 100%;
  z-index: 10;
  background: rgba(0, 0, 0, .7);
  transform: translate3d(0, 0, 0);
}
/* 往路のアニメーション全体に対して設定をするためのクラス */
.modal-enter-active {transition: opacity .2s;}
/* 往路の開始状態を設定するためのクラス */
.modal-enter        {opacity: 0;}
/* 往路の終了状態を設定するためのクラス */
.modal-enter-to     {opacity: 1;}
/* 復路のアニメーション全体に対して設定をするためのクラス */
.modal-leave-active {transition: opacity .6s;}
/* 復路の開始状態を設定するためのクラス */
.modal-leave        {opacity: 1;}
/* 復路の終了状態を設定するためのクラス */
.modal-leave-to     {opacity: 0;}

.modal__content {
  position: absolute; top: 50%; left: 50%;
  transform: translate(-50%, -50%);
}
.modal__content > p {
  margin: 0;
  width: 600px;
  vertical-align: middle;
  text-align: center;
  font: bold 12px/100px sans-serif;
  letter-spacing: .1em;
  color: #aaa;
  background: #fff;
}
</style>
