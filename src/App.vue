<template>
  <div class="board">
    <ul>
      <li v-for="num in numKeys" :key="num">
        <keyboard keyNum="getKeyNum(num)" keyAudio="https://www.myinstants.com/media/sounds/spongebob-fail.mp3" :keyImage="keyImage" />
      </li>
    </ul>
  </div>
</template>

<script>
import keyboard from './components/keyboard.vue'

export default {
  name: 'App',
  data() {
    return {
      numKeys: 10,
      keyImage: "https://images6.fanpop.com/image/photos/33200000/Spongebob-spongebob-squarepants-33210738-2284-2140.jpg"
    };
  },
  components: {
    keyboard
  },
  methods: {
    getKeyNum(num) {
      return `key${num}`
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.board {
  align-self: center;
  align-items: center;
  justify-content: center;
  display: flex;
  width: 80%;
  height: auto;
}

ul {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  list-style-type: none;
}

li > img {
  width: 5em;
  height: auto;
}
</style>
