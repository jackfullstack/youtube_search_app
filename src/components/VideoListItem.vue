<template>
    <li class="list-group-item media" @click="onVideoSelect">
        <img :src="thumbnailURL" />
        <div class="media-body">
            {{ video.snippet.title }}
        </div>
        
    </li>
</template>

<script>
    export default {
        name: 'VideoListItem',
        props: {
            video: Object
            },
        computed: {
            thumbnailURL() {
                return this.video.snippet.thumbnails.default.url 
            }
        },
        methods: { //vue specific event
            onVideoSelect() {
              this.$emit('videoSelect', this.video) //referencing prop - this video is passed as video to listener  
            }
        }
    }
</script>

<style scoped>
    li {
        display: flex;
        cursor: pointer;
    }

    li:hover {
        background-color: #eee;
    }

    img {
        margin-right: 1rem;
    }
</style>