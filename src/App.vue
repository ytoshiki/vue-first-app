<template>
  <div>
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoDetail :video="video" />
    <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';
import axios from 'axios';
const API_KEY = 'AIzaSyDHzuNcP66UVsbSH4VWs5pUCHFY_uciN0M';

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return {
      videos: [],
      video: null
    };
  },
  computed: {},
  methods: {
    async onTermChange(searchTerm) {
      const response = await axios.get(`https://www.googleapis.com/youtube/v3/search`, {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      });

      const { items } = response.data;
      if (items.length > 0) {
        this.videos = items;
      }
    },

    onVideoSelect(video) {
      this.video = video;
    }
  }
};
</script>
