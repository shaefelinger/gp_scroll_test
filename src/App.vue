<template>
  <div id="app">
    <!-- <ShowComments :episodes="items" ref="test" /> -->
    <div
      class="container"
      ref="containerRef"
      :style="{ transition: `linear ${speed}s` }"
    >
      <div v-for="(item, index) in items" v-bind="item" :key="index">
        <h1>{{ item.name }}</h1>
        <h2>{{ item.id }}</h2>
        <p>{{ item.body }}</p>
        <p>speed: {{ speed }}</p>
      </div>
    </div>
    <TheObserver @intersect="onIntersect" />
  </div>
</template>

<script>
// import ShowComments from './components/ShowComments.vue';
import TheObserver from './components/TheObserver.vue';
export default {
  name: 'App',
  components: {
    TheObserver,
    // ShowComments,
  },
  data() {
    return {
      timerId: null,
      items: [],
      episodeCount: 0,
      speed: 10,
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
    // resetArray() {
    //   this.items = [].concat(this.episodes);
    // },
    handleScroll() {
      console.log('scroll');
    },
    onIntersect() {
      console.log('intersect');
      this.items = this.items.concat(this.episodes);
      // for (let i = 0; i < 3; i++) {
      //   this.items = this.items.concat(this.episodes);
      // }
      const innerHeight = this.$refs.containerRef.offsetHeight;
      this.$refs.containerRef.style.marginTop = `-${innerHeight}px`;
      // this.items = this.items.slice(1);
    },
    // loadAutoscroll() {
    //   this.items = this.items.concat(this.episodes);
    //   // for (let i = 0; i < 1; i++) {
    //   //   this.items = this.items.concat(this.episodes);
    //   // }
    //   // console.log(this.episodes);
    //   // if (this.items.length > 10) {
    //   //   this.items = this.episodes;
    //   // }

    //   console.log(this.$refs.containerRef.offsetHeight);

    //   // const innerHeight = this.$refs.containerRef.offsetHeight;
    //   // this.$refs.containerRef.style.marginTop = `-${innerHeight}px`;

    //   // console.log(this.episodeCount);
    //   // this.episodeCount++;
    //   // if (this.episodeCount > 2) {
    //   //   this.items = [...this.episodes];
    //   //   this.episodeCount = 0;
    //   // }
    // },
    // pageScroll() {
    // console.log(this.$refs.containerRef.offsetHeight);
    // let scroll = window.devicePixelRatio;
    // window.scrollBy(0, 3);
    // console.log(window.scrollY);
    // },
  },
  mounted() {
    this.items = [].concat(this.episodes);
    // const innerHeight = this.$refs.containerRef.offsetHeight;
    this.$refs.containerRef.style.marginTop = `-100px`;
    // this.resetArray();
  },

  created() {
    window.addEventListener('scroll', this.handleScroll);
  },
  destroyed() {
    window.removeEventListener('scroll', this.handleScroll);
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
