 <!-- 
    Just your average soundboard with some additional features
    Includes 2 soundboards with 10 buttons each.
    Utilizes all of the features I've used in my past assignments
    This includes components, methods, data, for loops, if statements
    Hover commands, and more
  -->
<template>
  <h1>My sick sound board that's awesome.</h1>
  <div class="board">
    <ul id="list1">
      <!-- v-for creates the image / sound buttons -->
      <li v-for="num in numKeys" :key="num" :style="getTransitionStyle(num)">
        <h2 v-if="loadedKeys.includes(num)">{{num}}</h2>
        <!-- v-if renders the keyboard element when loadedKeys array is populated with num
        Let's me have a dynamic load-->
        <keyboard v-if="loadedKeys.includes(num)" :keyNum="getKeyNum(num)" :keySounds="windowsSounds[num-1]" :keyImage="keyImages[0]" />
      </li>
    </ul>
    <ul id="list2">
      <li v-for="num in numKeys" :key="num*10" :style="getTransitionStyle(num)">
        <h2 v-if="loadedKeys.includes(num)">{{num+10}}</h2>
        <!-- v-if renders the keyboard element when loadedKeys array is populated with num
        Let's me have a dynamic load-->
        <keyboard v-if="loadedKeys.includes(num)" :keyNum="getKeyNum(num+10)" :keySounds="randomSounds[num-1]" :keyImage="randomHovers[num-1]" />
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
      keyboards: 2,
      transitionDelay: 200, // For keyboard animation
      keyImages: [
      "https://picfiles.alphacoders.com/462/462435.jpg", //Windows
      "https://www.flayrah.com/sites/default/files/u/dronon/mystery-box.jpg", //Random -> Not useful, but sad because hovering doesn't work, so leaving it here.
      ],
      //Hovers for the random sound buttons
      //Was supposed to be for when the user hovered over the mystery buttons, 
      //But I couldn't get it to work
      randomHovers: [
        "https://i.ytimg.com/vi/QexVOkb68rM/maxresdefault.jpg", //Baby
        "http://clubhardhead.com/wp-content/uploads/2012/04/Crazy-Cat.jpg", //Cat
        "https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fi.pinimg.com%2F736x%2F62%2Fc0%2Ffc%2F62c0fcc9f0fdcfd1755e7d4068f83bf9.jpg&f=1&nofb=1&ipt=ecc8036c8e172a1d78c562bf87d203b6cf4d31b8dcb0a5482e72cc00250dddac&ipo=images", //Taco bell meme
        "https://i.imgflip.com/2/70ziqx.jpg", //Grilled cheese Obama
        "https://www.cartoonbucket.com/wp-content/uploads/2015/08/Funny-Image-Of-Spongebob.jpg", //Spongebob
        "https://cdn.patchcdn.com/users/22253747/2013/12/T600x450/bd7f63329b0c2793146375e9dd861e04.jpg", //Knocking
        "https://kkfi.org/wp-content/uploads/Screen-Shot-2021-01-19-at-9.10.21-PM.png", //Idk, but it goes to the 9 + 10 one
        "https://images5.fanpop.com/image/polls/1073000/1073421_1342083688012_full.jpg?v=1342083796", //Alvin and the chipmunks for 9 + 10
        "https://runt-of-the-web.com/wordpress/wp-content/uploads/2017/05/who.png", //Mind and body
        "https://i.redd.it/b6mermd7gkc21.jpg" //U got that
        
      ],
      //Sounds for the random sound buttons
      randomSounds: [
        "https://www.myinstants.com/media/sounds/asdasd_xyorzJ8.mp3", //Baby Cry
        "https://www.myinstants.com/media/sounds/discord-kitten.mp3", //Weird cat dude sound
        "https://www.myinstants.com/media/sounds/taco-bell-bong-sfx.mp3", //Taco bell bong
        "https://www.myinstants.com/media/sounds/grilled-cheese-obama-sandwich.mp3", //Grilled cheese Obama
        "https://www.myinstants.com/media/sounds/spongebob-fail.mp3", //Spongebob
        "https://www.myinstants.com/media/sounds/crazy-realistic-knocking-sound-trim.mp3", //Super real knocking
        "https://www.myinstants.com/media/sounds/whats-9-plus-10_i5prvd4.mp3", //9 + 10 = 21
        "https://www.myinstants.com/media/sounds/funny-sound-that-will-make-you-to-laugh_1.mp3", // Na Na Na
        "https://www.myinstants.com/media/sounds/when-the-q-lands_1.mp3", //Mind and body
        "https://www.myinstants.com/media/sounds/u-got-that-mp3-fix.mp3" //U got that

      ],

      //Windows sounds for the first sound board
      //I created the others first even though this one is on top. Oops.
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
      ],
      loadedKeys: [], // Array to keep track of loaded keyboard elements
    };
  },
  components: {
    keyboard
  },
  methods: {
    // Method to load the keyboard elements one at a time with a delay
    loadKeyboardElements() {
      this.loadedKeys = []; // Clear the loadedKeys array
      let index = 0;
      const loadNextKey = () => {
        if (index < this.numKeys) {
          this.loadedKeys.push(index + 1); // Load the next key
          index++;
          setTimeout(loadNextKey, this.transitionDelay); // Delay between each key loading
        }
      };
      loadNextKey();
    },
    //Gets the number of the key
    getKeyNum(num) {
      return `key${num}`
    },
    // Computed property to calculate the transition duration for each element
    getTransitionStyle() {
      return (index) => ({
        animationDelay: `${this.transitionDelay * index}ms`,
      });
    },
  },
  created() {
    this.loadKeyboardElements(); // Start loading the keyboard elements
  },
  /* Leaving this here because I am sad and depressed it doesn't work :'(
  //Returns the image from randomHovers based on the index
  switchImages(index) {
    try {
      var image = randomHovers[index];
      randomHovering[index] ? randomHovers[index] : keyImages[1]; 
      return image;
    } catch (error) { //In the event the index does not exist
      return "https://thumbs.dreamstime.com/b/scream-shocked-scared-man-5443860.jpg";
    }
  },
  */
};
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
  flex-direction: column;
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
  max-width: 100%;
  max-height: 10em;
  aspect-ratio: 1 / 1;
}

.list2 > img {
  padding-left: 10px
}

/* CSS animation for the keyboard elements */
.keyboard-transition-enter-active,
.keyboard-transition-leave-active {
  transition: all 0.5s ease;
}

.keyboard-transition-enter {
  transform: scale(0); /* Start with scale 0 */
}

.keyboard-transition-leave-to {
  transform: scale(0); /* End with scale 0 */
}

.keyboard-transition-move {
  transition: transform 0.5s ease; /* Apply the same animation when reordering elements */
}
</style>
