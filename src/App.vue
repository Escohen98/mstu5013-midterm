<template>
  <h1>My sick sound board that's awesome.</h1>
  <div class="board">
    <ul>
      <li v-for="num in numKeys" :key="num">
        <h2>{{num}}</h2>
        <keyboard :keyNum="getKeyNum(num)" :keySounds="windowsSounds[num-1]" :keyImage="keyImage" />
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
      keyImage: "https://images6.fanpop.com/image/photos/33200000/Spongebob-spongebob-squarepants-33210738-2284-2140.jpg",
      keyHovers: [
        "https://i.ytimg.com/vi/QexVOkb68rM/maxresdefault.jpg", //Baby
        "http://clubhardhead.com/wp-content/uploads/2012/04/Crazy-Cat.jpg", //Cat
        "https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fi.pinimg.com%2F736x%2F62%2Fc0%2Ffc%2F62c0fcc9f0fdcfd1755e7d4068f83bf9.jpg&f=1&nofb=1&ipt=ecc8036c8e172a1d78c562bf87d203b6cf4d31b8dcb0a5482e72cc00250dddac&ipo=images", //Taco bell meme
        "https://www.myinstants.com/media/sounds/spongebob-fail.mp3", //Spongebob

        
      ],
      keySounds: [
        "https://www.myinstants.com/media/sounds/asdasd_xyorzJ8.mp3", //Baby Cry
        "https://www.myinstants.com/media/sounds/discord-kitten.mp3", //Weird cat dude sound
        "https://www.myinstants.com/media/sounds/taco-bell-bong-sfx.mp3", //Taco bell bong

      ],
      windowsSounds: [
        "https://www.myinstants.com/media/sounds/error_CDOxCYm.mp3", //old error sound
        "https://www.myinstants.com/media/sounds/preview_4.mp3", //Shutdown sound
        "https://www.myinstants.com/media/sounds/windows-10-error-sound.mp3", //newer error sound
        "https://www.myinstants.com/media/sounds/connect.mp3", //USB connect
        "https://www.myinstants.com/media/sounds/win31.mp3", //Windows 3.1 tada startup
        "https://www.myinstants.com/media/sounds/windowsding.mp3", //Ding
        "https://www.myinstants.com/media/sounds/windows-7-startup.mp3", //Windows 7 startup
        "https://www.myinstants.com/media/sounds/erro-win-7_3OFHeWK.mp3", //Windows 7 error
        "https://www.myinstants.com/media/sounds/windows-10-hardware-remove-disconnect.mp3", //USB disconnect
        "https://www.myinstants.com/media/sounds/blue-screen-of-death.mp3", //Blue screen of death
      ]
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
