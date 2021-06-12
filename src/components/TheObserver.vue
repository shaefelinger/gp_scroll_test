<template>
  <div class="observer"></div>
</template>

<script>
export default {
  name: 'observer',
  data() {
    return {
      observer: null,
    };
  },
  mounted() {
    this.observer = new IntersectionObserver(([entry]) => {
      // only get the first parameter
      if (entry && entry.isIntersecting) {
        this.$emit('intersect');
      }
    });
    this.observer.observe(this.$el);
  },
};
</script>

<style>
.observer {
  height: 1px;
}
</style>
