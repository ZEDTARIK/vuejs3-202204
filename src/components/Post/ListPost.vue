<template lang="">
  <div class="card mt-2">
    <img class="card-img-top" :src="post.image" :alt="post.title">
    <div class="card-body">
      <h4 class="card-title text-center"> {{ post.title }} </h4>
      <p class="card-text text-justify">
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Ratione, consequatur!
      </p>

      <div class="my-2 text-center">
        <button class="btn btn-success btn-sm" type="button">
          {{ post.category ? post.category: 'No Category' }}
        </button>
      </div>
    </div>

    <div class="card-footer" >
      <span class="badge badge-warning ml-2" v-for="(tag,index) in post.tags" :key="index">
        {{ tag }}
      </span>
    </div>

    <div class="card-footer text-right">
      <button @click="DeletePost(post.id)" type="button" class="btn btn-sm btn-danger">Delete</button>
    </div>
  </div>


</template>
<script>
  export default {
    props: ["post"],
    data() {
      return {

      };
    },
    methods: {
      DeletePost(id) {
        this.$emit("deletePost", id);
      },
    },
  };
</script>
<style scoped>
  h4 {
    color: green;
  }
</style>