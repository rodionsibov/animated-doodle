<template>
  <div class="post">
    <router-link :to="{ name: 'Details', params: { id: post.id } }">
      <h3>{{ post.title }}</h3>
    </router-link>
    <p>{{ snippet }}</p>
    <span v-for="tag in post.tags" :key="tag" class="tag"> #{{ tag }}</span>
  </div>
</template>

<script>
import { computed } from "vue";
export default {
  props: ["post"],
  setup(props) {
    const snippet = computed(() => {
      return props.post.body.substring(0, 100) + "...";
    });

    return {
      snippet,
    };
  },
};
</script>

<style>
.tag {
    background: crimson;
    border-radius: 8px;
    padding: 4px 6px;
    margin: 0 4px;
    color: white;
    font-size: 14px;
    font-weight: bold;
}
</style>