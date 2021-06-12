<template>
  <div class="comments">
    <h1>{{ name }}</h1>
    <h2>{{ id }}</h2>
    <p>{{ body }}</p>
  </div>
</template>

<script>
export default {
  name: 'ShowComments',
  props: {
    postId: Number,
    id: Number,
    name: String,
    email: String,
    body: String,
  },
};
</script>

<style></style>
