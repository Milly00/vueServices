<template>
   <div class="post-container">
      <div class="post-card">
         <h3>{{ postId.title }}</h3>
         <p>{{ postId.body }}</p>
      </div>
      <router-link class="link" :to="{name: 'PostList'}">Volver</router-link>
   </div>

</template>
<script setup>
import PostService from "@/services/PostService";
import { onMounted } from "vue";
import { useRoute } from "vue-router";

const service = new PostService();
let postId = service.getPost();

onMounted(() => {
   const route = useRoute();
   postId.value = service.fetchById(route.params.id);
   console.log(postId);
});
</script>

<style lang="scss">
.post-container {
   width: 100%;
   display: flex;
   justify-content: center;
   align-items: center;
   flex-direction: column;
}

.post-card {
   padding: 25px;
   width: 350px;
   border-radius: 15px;
   border: 1px solid #ccc;
}

.link {
   margin-top: 25px;
   color: $primaryColor;
   text-decoration: none;
}

.link:hover {
   text-decoration: underline;
}
</style>