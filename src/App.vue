<template>
  <div id="app">
    <div
      class="container"
      ref="containerRef"
      :style="{ transition: `linear ${speed}s` }"
    >
      <div v-for="(item, index) in items" v-bind="item" :key="index">
        <h1>{{ item.id }}</h1>
        <h2>{{ item.name }}</h2>
        <br><br>
      </div>
    </div>

    <TheObserver @intersect="onIntersect" />
  </div>
</template>

<script>
import TheObserver from './components/TheObserver.vue';
export default {
  components: {
    TheObserver,
  },
  data() {
    return {
      items: [],
      speed: 10,
      episodes: [
        {
          id: 1,
          name: 'id labore ex et quam laborum',
        },
        {
          id: 2,
          name: 'quo vero reiciendis velit similique earum',
        },
        {
          id: 3,
          name: 'odio adipisci rerum aut animi',
        },
      ],
      page: 1,
    };
  },
  methods: {
    onIntersect() {
      console.log('intersect');
      this.items = this.items.concat(this.episodes);
      // for (let i = 0; i < 10; i++) {
      //   this.items = this.items.concat(this.episodes);
      // }
      const innerHeight = this.$refs.containerRef.offsetHeight;
      this.$refs.containerRef.style.marginTop = `-${innerHeight}px`;
    },
     handleScroll() {
      // do something when scrolling??
      console.log('scroll');
    },
  },
  mounted() {
    this.items = [].concat(this.episodes);
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
  background: black;
}
</style>
