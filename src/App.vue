<template>
  <div id="app">
    <ShowComments :episodes="items" ref="test" />
    <TheObserver @intersect="loadAutoscroll" />
  </div>
</template>

<script>
import ShowComments from './components/ShowComments.vue';
import TheObserver from './components/TheObserver.vue';
export default {
  name: 'App',
  components: {
    TheObserver,
    ShowComments,
  },
  data() {
    return {
      timerId: null,
      items: [],
      episodeCount: 0,
      episodes: [
        {
          id: 1,
          name: 'id labore ex et quam laborum',
          body: 'laudantium enim quasi est quidem magnam voluptate ipsam eos\ntempora quo necessitatibus\ndolor quam autem quasi\nreiciendis et nam sapiente accusantium',
        },
        {
          id: 2,
          name: 'quo vero reiciendis velit similique earum',
          body: 'est natus enim nihil est dolore omnis voluptatem numquam\net omnis occaecati quod ullam at\nvoluptatem error expedita pariatur\nnihil sint nostrum voluptatem reiciendis et',
        },
        {
          id: 3,
          name: 'odio adipisci rerum aut animi',
          body: 'quia molestiae reprehenderit quasi aspernatur\naut expedita occaecati aliquam eveniet laudantium\nomnis quibusdam delectus saepe quia accusamus maiores nam est\ncum et ducimus et vero voluptates excepturi deleniti ratione',
        },
      ],
      page: 1,
    };
  },
  methods: {
    loadAutoscroll() {
      for (let i = 0; i < 10; i++) {
        this.items = this.items.concat(this.episodes);
      }
      console.log(this.items);
      // console.log(this.episodeCount);
      // this.episodeCount++;
      // if (this.episodeCount > 2) {
      //   this.items = [...this.episodes];
      //   this.episodeCount = 0;
      // }
    },
    pageScroll() {
      // window.scrollBy({
      //   top: 300,
      //   behavior: 'smooth',
      // });
      // let scroll = window.devicePixelRatio;

      window.scrollBy(0, 2);
      // console.log(window.scrollY);
    },
  },
  mounted() {
    this.timerId = setInterval(() => this.pageScroll(), 22);
  },
  destroyed() {
    clearInterval(this.timerId);
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  margin-top: 60px;
  background: black;
}
</style>
