<template>
  <div id="app" class="container-fluid">
    <header>
      <nav class="navbar navbar-light bg-dark">
        <div class="container-fluid brand-div">
           <span class="navbar-brand">{{ appTitle }}</span>
        </div>
      </nav>
    </header>
    <main>
      <div>
          <h1 class="title mx-auto py-4 mt-5 h1">{{ appTitle }}</h1>
          <SearchBar @termChange="onTermChange"></SearchBar>
      </div>
      <div>
          <VideoDetail :video="selectedVideo" class="mt-5"/>
          <VideoList :videos="videos" @videoSelect="onVideoSelect" class="mt-5"></VideoList>
      </div>
    </main>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail";


const API_KEY = 'AIzaSyBK3hXN8_-3EO6NlKCROaDjON-V5Q5Bm6w';

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return {
      appTitle: 'YouTube Search',
      videos: [],
      selectedVideo: null
    };
  },
  methods: {
    onVideoSelect(video) {
      this.selectedVideo = video;  
    },
    onTermChange(searchTerm) {
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      }).then(response => {this.videos = response.data.items});
    }
  }
}
</script>

<style scoped>
  .container-fluid {
    padding: 0%
  }
  .container-fluid.brand-div {
    padding-left: 1rem;
  }
  h1 {
    max-width: 400px;
    text-align: center;
  }

  .navbar-brand {
    color: white;
  }

  .navbar-brand:hover {
    color: white;
    cursor: pointer;
  }

</style>
