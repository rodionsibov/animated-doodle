<template>
  <div v-if="error">{{ error }}</div>
  <div v-if="post" class="post">
    <h3>{{ post.title }}</h3>
    <p class="pre">
      {{ post.body }}
    </p>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  props: ["id"],
  setup(props) {
    const post = ref(null);
    const error = ref(null);

    const load = async () => {
      try {
        let data = await fetch("http://localhost:3000/posts/" + props.id);
        if (!data.ok) {
          throw Error("that post does not exist");
        }
        post.value = await data.json();
      } catch (err) {
        error.value = err.message;
        console.log(error.value);
      }
    };
    load();

    return {
      post,
      error,
    };
  },
};
</script>

<style>
.post {
  max-width: 800px;
  margin: 0 auto;
}

.post p {
  color: #444;
  line-height: 1.5em;
  margin-top: 40px;
}

.pre {
  white-space: pre-wrap;
}
</style>