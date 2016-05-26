<template>
  <div id="app">
    <a class="button" @click="previous" v-link="{ name: 'page', params: { pageNum: page - 1} }">GO PREVIOUS<span>CURRENT:{{page}}</span></a>
    <list :page="page" :trigger.sync="finish"></list>
    <a class="button" @click="next" v-link="{ name: 'page', params: { pageNum: page + 1} }">GO NEXT<span>CURRENT:{{page}}</span></a>
    <div id="loader" v-show="!finish" :transition="up? 'up-start':'down-start'">
      <span>Loading</span>
    </div>
  </div>
</template>

<script>
import List from './components/List'

export default {
  components: {
    List
  },
  data () {
    return {
      page: parseInt(this.$route.params.pageNum),
      finish: true,
      up: false
    }
  },
  methods: {
    previous () {
      if (this.page === 1) {
        window.alert('已是第一页')
      } else {
        this.page--
        this.up = true
        this.finish = false
      }
    },
    next () {
      this.page++
      this.up = false
      this.finish = false
      document.body.scrollTop = 0
    }
  },
  watch: {
    finish (val, oldVal) {
      if (!oldVal && val && this.up) {
        document.body.scrollTop = document.body.scrollHeight
      }
    }
  }
}
</script>

<style scoped>
  html, body {
    height: 100%;
  }
  .button {
    display: block;
    width: 100%;
    background: #212121;
    color: #fff;
    font-weight: bold;
    text-align: center;
    padding: 1em;
    cursor: pointer;
    text-decoration: none;
  }
  .button span {
    margin-left: 2em;
    font-size: .5rem;
    color: #d6d6d6;
  }
  #loader {
    width: 100%;
    min-height: 3em;
    position: fixed;
    left: 0;
    background: #212121;
    color: #fff;
  }
  #loader span {
    display: block;
    width: 100%;
    text-align: center;
    position: absolute;
    top: 50%;
    margin-top: -0.5em;
  }
  .down-start-transition {
    bottom: 0;
    height: 100%;
  }
  .down-start-enter {
    animation: expand .5s 1 cubic-bezier(0, 1, 0, 1) both;
  }
  .down-start-leave {
    animation: collapse .5s 1 cubic-bezier(0, 1, 0, 1) both;
    top: 0;
    bottom: auto;
  }
  .up-start-transition {
    top: 0;
    height: 100%;
  }
  .up-start-enter {
    animation: expand .5s 1 cubic-bezier(0, 1, 0, 1) both;
  }
  .up-start-leave {
    animation: collapse .5s 1 cubic-bezier(0, 1, 0, 1) both;
    top: auto;
    bottom: 0;
  }
  @keyframes expand {
    0% {
      height: 3em;
      transform: translate3d(0, 0, 0);
    }
    100% {
      height: 100%;
      transform: translate3d(0, 0, 0);
    }
  }
  @keyframes collapse {
    0% {
      height: 100%;
      transform: translate3d(0, 0, 0);
    }
    100% {
      height: 3em;
      transform: translate3d(0, 0, 0);
    }
  }
</style>
