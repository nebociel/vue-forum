<template>
  <div class="page-home">
    <h1>Vue Forum</h1>
    <div v-for="thread in threads" :key="thread.id" class="thread">
      <h2 class="thread-title">{{ thread.title }}</h2>
      <div v-for="post in posts" :key="post.id" class="post">
        <div class="post-author">{{ userById(post.userId).name }}:</div>
        <div class="post-content">{{ postById(post.id).text }}</div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue';
import sourceData from '@/data.json';

const threads = reactive(sourceData.threads);
const posts = reactive(sourceData.posts);
const users = reactive(sourceData.users);

const postById = (id) => posts.find((post) => post.id === id);
const userById = (id) => users.find((user) => user.id === id);
</script>

<style scoped>
.page-home {
  display: flex;
  padding: 20px;
  background-color: #f9f9f9;
  flex-direction: column;
}

.page-home h1 {
  font-size: 32px;
  margin-bottom: 20px;
  text-align: center;
  letter-spacing: 1rem;
  text-transform: uppercase;
}

h2 {
  font-size: 20px;
  margin-bottom: 10px;
}

.thread {
  margin-bottom: 20px;
  padding: 10px;
  background-color: #fff;
  border-radius: 5px;
}

.thread-title {
  font-size: 18px;
  margin-bottom: 10px;
}

.post {
  margin-top: 10px;
  padding: 10px;
  background-color: #f9f9f9;
  border-radius: 5px;
}

.post-content {
  margin-bottom: 10px;
  text-align: justify;
}

.post-author {
  font-size: 14px;
  color: #666;
  margin-bottom: 5px;
  font-style: italic;
}
</style>
