<template>
  <div class="home" ref="home">
    <h1>Home</h1>
    <PostList v-if="showPosts" :posts="posts" />
    <button @click="showPosts = !showPosts">toggle posts</button>
    <button @click="posts.pop()">delete a post</button>
  </div>
</template>

<script>
import PostList from "@/components/PostList.vue";
import { ref } from "vue";

export default {
  components: { PostList },
  name: "Home",
  setup() {
    const posts = ref([
      {
        title: "welcome to the blog",
        body:
          "Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium perspiciatis, id rerum magni qui suscipit voluptate nemo laborum enim amet accusamus animi architecto sapiente quaerat optio! Reiciendis amet, provident qui eligendi, inventore aliquam nesciunt esse, dolorem quis beatae error labore. Error id odit inventore sunt placeat, nostrum facilis! Odit nemo omnis odio corporis ea, tempore non voluptatem suscipit adipisci alias labore esse, impedit nobis vero saepe ut hic facilis error. Itaque, suscipit illum perferendis nisi incidunt quaerat repellat ipsa, quidem fugiat provident nulla. Autem est reprehenderit soluta inventore ipsa dolorum ipsam obcaecati, consequatur tempora nisi laudantium cupiditate a doloremque eum.",
        id: 1,
      },
      {
        title: "top 5 CSS tips",
        body: "lorem ipsum",
        id: 2,
      },
    ]);

    const showPosts = ref(true);

    return {
      posts,
      showPosts,
    };
  },
};
</script>
