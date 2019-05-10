<template>
  <div class="container">
    <search-bar @termChange="onTermChange"></search-bar>
    <div class="row">
      <video-detail :video="selectedVideo" class="mb-5 col-md-8"></video-detail>
      <video-list :videos="videos" @videoSelect="onVideoSelect" class="col-md-4"></video-list>
    </div>
  </div>
</template>
<script>
import axios from "axios";
import SearchBar from "@/components/SearchBar.vue";
import VideoList from "@/components/VideoList.vue";
import VideoDetail from "@/components/VideoDetail.vue";
import API from "../config.js";

export default {
  name: "App",
  data() {
    return {
      videos: [
        {
          kind: "youtube#searchResult",
          etag: '"XpPGQXPnxQJhLgs6enD_n8JR4Qk/2UvwZQlPa5YuoN-BFVtvjcLiAfA"',
          id: {
            kind: "youtube#video",
            videoId: "aQqAUXKn7t4"
          },
          snippet: {
            publishedAt: "2018-11-19T18:17:01.000Z",
            channelId: "UC3gNmTGu-TTbFPpfSs5kNkg",
            title: "Shrek (2001) - Kill the Ogre Scene (3/10) | Movieclips",
            description:
              "Shrek - Kill the Ogre: Shrek (Mike Myers) and Donkey (Eddie Murphy) accidentally find themselves in the middle of a trial by combat. BUY THE MOVIE: ...",
            thumbnails: {
              default: {
                url: "https://i.ytimg.com/vi/aQqAUXKn7t4/default.jpg",
                width: 120,
                height: 90
              },
              medium: {
                url: "https://i.ytimg.com/vi/aQqAUXKn7t4/mqdefault.jpg",
                width: 320,
                height: 180
              },
              high: {
                url: "https://i.ytimg.com/vi/aQqAUXKn7t4/hqdefault.jpg",
                width: 480,
                height: 360
              }
            },
            channelTitle: "Movieclips",
            liveBroadcastContent: "none"
          }
        },
        {
          kind: "youtube#searchResult",
          etag: '"XpPGQXPnxQJhLgs6enD_n8JR4Qk/PIng430yL_7HuxXvYM1fpX4qRiQ"',
          id: {
            kind: "youtube#video",
            videoId: "8SeCMLddf3w"
          },
          snippet: {
            publishedAt: "2018-05-12T06:38:17.000Z",
            channelId: "UCYI1VzfvGaiyhfv3l-uaGtg",
            title:
              "Shrek movie | Best Scenes And Funny Moments | Top Animated Movies",
            description:
              "This Chanel is about Funny songs, Funny videos for kids to learn colors, learn colors with minions, Surprise eggs, 3D,Lollipops, Kinder, Surprise, Toys, Eggs, ...",
            thumbnails: {
              default: {
                url: "https://i.ytimg.com/vi/8SeCMLddf3w/default.jpg",
                width: 120,
                height: 90
              },
              medium: {
                url: "https://i.ytimg.com/vi/8SeCMLddf3w/mqdefault.jpg",
                width: 320,
                height: 180
              },
              high: {
                url: "https://i.ytimg.com/vi/8SeCMLddf3w/hqdefault.jpg",
                width: 480,
                height: 360
              }
            },
            channelTitle: "Kids Channel",
            liveBroadcastContent: "none"
          }
        },
        {
          kind: "youtube#searchResult",
          etag: '"XpPGQXPnxQJhLgs6enD_n8JR4Qk/0cjLhyJjvSiohwHuDrkaI6Vu-cQ"',
          id: {
            kind: "youtube#video",
            videoId: "pM70TROZQsI"
          },
          snippet: {
            publishedAt: "2018-11-30T00:58:28.000Z",
            channelId: "UCNFAQk2EvarfCfYzHjml7fg",
            title: "Shrek Retold",
            description:
              "We got over 200 people to remake Shrek. This is it. collaborators ▷ https://tinyurl.com/ydf6zquf download ▷ https://tinyurl.com/y67ktkzt patreon ...",
            thumbnails: {
              default: {
                url: "https://i.ytimg.com/vi/pM70TROZQsI/default.jpg",
                width: 120,
                height: 90
              },
              medium: {
                url: "https://i.ytimg.com/vi/pM70TROZQsI/mqdefault.jpg",
                width: 320,
                height: 180
              },
              high: {
                url: "https://i.ytimg.com/vi/pM70TROZQsI/hqdefault.jpg",
                width: 480,
                height: 360
              }
            },
            channelTitle: "3GI",
            liveBroadcastContent: "none"
          }
        },
        {
          kind: "youtube#searchResult",
          etag: '"XpPGQXPnxQJhLgs6enD_n8JR4Qk/HNa2oI-1jPHNpNzFgNRUIhRHVaY"',
          id: {
            kind: "youtube#video",
            videoId: "Uo2SNtFofWI"
          },
          snippet: {
            publishedAt: "2011-12-03T04:47:52.000Z",
            channelId: "UCYtsOmQw2GDZftoKKCy6u3g",
            title: "Shrek - All Stars",
            description: "Smash Mouth - All Stars.",
            thumbnails: {
              default: {
                url: "https://i.ytimg.com/vi/Uo2SNtFofWI/default.jpg",
                width: 120,
                height: 90
              },
              medium: {
                url: "https://i.ytimg.com/vi/Uo2SNtFofWI/mqdefault.jpg",
                width: 320,
                height: 180
              },
              high: {
                url: "https://i.ytimg.com/vi/Uo2SNtFofWI/hqdefault.jpg",
                width: 480,
                height: 360
              }
            },
            channelTitle: "Fangki Borres",
            liveBroadcastContent: "none"
          }
        },
        {
          kind: "youtube#searchResult",
          etag: '"XpPGQXPnxQJhLgs6enD_n8JR4Qk/HatHKzT9vhhnj1XAv9emaZLryvs"',
          id: {
            kind: "youtube#video",
            videoId: "em9lziI07M4"
          },
          snippet: {
            publishedAt: "2018-11-19T18:16:56.000Z",
            channelId: "UC3gNmTGu-TTbFPpfSs5kNkg",
            title:
              "Shrek (2001) - An All-Star Ogre Opening Scene (1/10) | Movieclips",
            description:
              "Shrek - An All-Star Ogre Opening: Shrek (Mike Myers) enjoys a day of solitude just like any other before a group of villagers decide to change that. BUY THE ...",
            thumbnails: {
              default: {
                url: "https://i.ytimg.com/vi/em9lziI07M4/default.jpg",
                width: 120,
                height: 90
              },
              medium: {
                url: "https://i.ytimg.com/vi/em9lziI07M4/mqdefault.jpg",
                width: 320,
                height: 180
              },
              high: {
                url: "https://i.ytimg.com/vi/em9lziI07M4/hqdefault.jpg",
                width: 480,
                height: 360
              }
            },
            channelTitle: "Movieclips",
            liveBroadcastContent: "none"
          }
        }
      ],
      selectedVideo: null
    };
  },
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get(`${API.url}`, {
          params: {
            key: API.key,
            type: "video",
            part: "snippet",
            q: searchTerm
          }
        })
        .then(response => (this.videos = response.data.items))
        .catch(error => console.log(error));
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    }
  }
};
</script>
<style scoped>
.container {
  text-align: center;
  margin-top: 20px;
}
</style>
