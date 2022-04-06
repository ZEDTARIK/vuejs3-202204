<template lang="">

  <!-- Component For Add New Post-->
  <div class="row" v-if="showForm">
    <div class="col-md-9 mx-auto">
      <AddPost @addPost="OnAddPost($event)" />
    </div>
  </div>

  <div class="row">
    <div class="col-md-12">
      <button type="button" @click="displayForm()" class="btn btn-sm"
        :class="{'btn-success' : !showForm, 'btn-dark': showForm }">
        {{ showForm ? 'Close' : 'New'}}
      </button>
    </div>
  </div>

  <!-- Component For List Post-->
  <div class="row">
    <div class="col-md-3" v-for="post in Posts" :key="post.id">
        <ListPost :post="post" @deletePost="onDelete($event)" />
    </div>
  </div>


   <teleport to="#alert" v-if="PostDeleted">
          <div class="alert alert-danger">
            <strong>Post Deleted !!</strong>
        </div>
    </teleport>

</template>
<script>
  import ListPost from "./ListPost.vue";
  import AddPost from "./AddPost.vue";
  export default {
    components: {
      ListPost,
      AddPost,
    },
    data() {
      return {
        PostDeleted: false,
        showForm: false,
        Posts: [
          {
            id: 1,
            title: "Learn VueJS",
            tags: ['Front End'],
            category: 'Framework JS',
            image:
              "https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:705/https://www.filepicker.io/api/file/k7Fltx5ITbu9LI6VtgTS",
          },
          {
            id: 2,
            title: "Learn Angular",
            tags: [],
            category: 'Framework JS',
            image:
              "https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:705/https://www.filepicker.io/api/file/nrOHB2iQTIiGe7hHX9O0",
          },
          {
            id: 3,
            title: "Learn Laravel",
            tags: [],
            category: 'Framework PHP',
            image:
              "https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:705/https://www.filepicker.io/api/file/aL2OXWSpTguVo0azLaPb",
          },
          {
            id: 4,
            title: "Learn NodeJs",
            tags: [],
            category: '',
            image:
              "https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:705/https://www.filepicker.io/api/file/yMO0mZjvTm2pwyeOQUpT",
          },
        ],
      };
    },
    methods: {
      onDelete(id) {
        this.Posts = this.Posts.filter(c => c.id != id);
        this.PostDeleted = true;
        setTimeout(() => {
          this.PostDeleted = false;
        }, 3000);
        
      },
      OnAddPost(post) {
        this.Posts = [post, ...this.Posts];
        this.showForm = !this.showForm;
      },
      displayForm() {
        this.showForm = !this.showForm;
      }
    },
  };
</script>
<style>

</style>