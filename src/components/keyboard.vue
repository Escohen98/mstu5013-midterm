<template>
    <!-- Key instance for the keyboard
Handles each individual button. 
Do bear in mind that this was originally supposed to be a piano until I realized 
the sound response time was too slow -->
    <img @click="play()" class="key" :id="keyNum" alt="broken image" :src="keyImage"/>
    <audio ref="audioPlayer">
        <source :src="keySounds" type="audio/mpeg">
        Audio is not supported on this browser.
    </audio>
</template>

<script>
export default {
    name: 'KeyBoard',
    props: {
        keyNum: Number,
        keySounds: String, //Audio on click
        keyImage: String, //Default image
       //keyHoverImage: String, //Image on hover
    },
    data() {
        return {
        };
    },
    methods: {
        //Plays the audio
        //Taken from https://thewebdev.info/2021/01/21/add-an-audio-player-with-vue-3-and-javascript/
        play() {
            this.$refs.audioPlayer.play();
        }
    }
}
</script>

<style scoped>
    .key {
        background-color: white; /*Default key */
        border: 2px inset rgb(125, 125, 125);
        margin-right: 5px;
        border-radius: 50%;
    }

    img {
        /* I couldn't get the dang aspect ratio to work */
        max-width: 100%;
        height: 5em;
      
    }

    img:hover {
        box-shadow: 20px rgba(255, 255, 0, 0.5);
        border: 1px solid yellow;
    }
</style>