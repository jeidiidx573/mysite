<template>
  <div id="js-modal">
    <!-- イベント修飾子.selfにより、.modal要素自身がクリックされた時のみイベントを発生させる -->
    <transition name="modal">
    <div class="modal" v-show="opened" @click.self="close">
      <div class="modal__close" @click="close">×</div>
      <div class="modal__content">
        <p>Click here and check nothing happens</p>
      </div>
    </div>
    </transition>
  </div>
</template>

<script>

export default {
  components: {
    Logo,
    Navi
  }
}
</script>

<style>
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
