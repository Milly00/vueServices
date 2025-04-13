<script lang="ts" setup>
import PostService from "@/services/PostService";
import { onMounted } from "vue";
const service = new PostService();
const posts = service.getPosts();
onMounted(async () => {
  await service.fetchAll();
});
</script>
<template>
  <div v-for="post in posts" :key="post.id">
    <h3>{{ post.title }}</h3>
  </div>
</template>
<style scoped lang="scss">
h3 {
  color: $red;
}
.post-list {
  width: 95vw;
  height: 75px;
  padding: 20px;
}
</style>
