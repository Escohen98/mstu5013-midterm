<template>
    <img class="key" v-bind:id="{keyNum}" v-bind:href="{keyImage}"/>
    <audio>
        <source v-bind:src="{keyAudio}">
    </audio>
</template>

<script>
export default {
    name: 'key',
    data() {
        return {
            keyNum: Number,
            keyImage: String, //Default image
            keyHoverImage: String, //Image on hover
            keyAudio: String, //Audio on click
            keyRef: String //Ref to play the audio
        };
    }
}
</script>

<style scoped>
    .key {
        background-color: white; /*Default key */
        border: 2px solid black;
    }

    .key:hover {
        box-shadow: 4px rgba(255, 255, 0, .1);
    }
</style>