<template>
  <div id="app">
    Hello
    <ShowComments v-for="item in items" v-bind="item" :key="item.id" />
    <TheObserver @intersect="Intersected" />
  </div>
</template>

<script>
import ShowComments from './components/ShowComments.vue';
import TheObserver from './components/TheObserver.vue';
export default {
  name: 'App',
  components: { TheObserver, ShowComments },
  data() {
    return {
      items: [],
      page: 1,
    };
  },
  methods: {
    async Intersected() {
      console.log('insersect');
      const res = await fetch(
        `https://jsonplaceholder.typicode.com/comments?_page=${this.page}`
      );
      const items = await res.json();
      this.items = [...this.items, ...items];
      this.page++;
      console.log(this.page);
    },
    pageScroll() {
      window.scrollBy(0, 1);
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
