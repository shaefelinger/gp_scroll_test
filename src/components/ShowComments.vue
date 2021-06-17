<template>
  <div>
    <div
      class="comments"
      v-for="(item, index) in episodes"
      v-bind="item"
      :key="index"
    >
      <h1>{{ item.name }}</h1>
      <h2>{{ item.id }}</h2>
      <p>{{ item.body }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ShowComments',
  props: {
    episodes: Array,
  },
};
</script>

<style></style>
