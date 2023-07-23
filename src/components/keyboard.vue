<template>
    <img @click="play()" class="key" :id="keyNum" alt="broken image" :src="keyImage"/>
    <audio ref="audioPlayer">
        <source :src="keyAudio" type="audio/mpeg">
        Audio is not supported on this browser.
    </audio>
</template>

<script>
export default {
    name: 'KeyBoard',
    props: {
        keyNum: Number,
        keyAudio: String, //Audio on click
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
        border: 2px solid black;
    }

    img:hover {
        box-shadow: 20px rgba(255, 255, 0, 1);
        border: 1px solid yellow;
    }
</style>