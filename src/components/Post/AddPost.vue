<template lang="">
    <div class="card my-3">
        <div class="card-body">
            <h4 class="card-title text-center">Add New Post</h4>

            <div class="form-group row">
                <label for="title" class="col-sm-2 col-form-label">Title</label>
                <div class="col-sm-10">
                    <input v-model="title" type="text" class="form-control" id="title" placeholder="Title">
                </div>
            </div>

            <div class="form-group row">
                <label for="image" class="col-sm-2 col-form-label">Url Image</label>
                <div class="col-sm-10">
                    <input v-model="image" type="text" class="form-control" id="image" placeholder="Url Image">
                </div>
            </div>

            <div class="form-group row">
                <label for="category" class="col-sm-2 col-form-label">Category</label>
                    <div class="col-sm-10">
                        <select class="form-control" v-model="category" id="category" >
                            <option v-for="cat in categories" :key="cat.id" :value="cat.id">{{cat.name}}</option>
                        </select>
                     </div>
            </div>

            <div class="form-group row">
                <label for="tag" class="col-sm-2 col-form-label">Tags</label>
                    <div class="col-sm-10">
                         <div class="form-check" v-for="(tag, index) in MyTags" :key="index">
                           <label class="form-check-label">
                             <input v-model="tags" type="checkbox" class="form-check-input" :value="tag">
                             {{ tag }}
                           </label>
                         </div>
                     </div>
            </div>

        </div>
        <div class="card-footer text-right">
            <button class="btn btn-sm btn-success" type="button" @click="onSubmit()">Save Post</button>
        </div>
    </div>


</template>
<script>
export default {
  data() {
    return {
      title: "",
      image: "",
      category: "",
      categories: [
        { id: 1, name: "Framework JS" },
        { id: 2, name: "Framework PHP" },
        { id: 3, name: "Java" },
        { id: 4, name: "Others ..." },
      ],
      MyTags: ["Front End", "Back End", "Mobile", "others.."],
      tags: [],
    };
  },
  methods: {
    onSubmit() {
      let title = this.title;
      let image = this.image;

      if (title === "" || image === "") {
        return;
      }
      const post = {
        title,
        image,
        category: this.categories.find((cat) => cat.id == this.category).name,
        tags : this.tags
      };

      this.$emit("addPost", post);
    },
  },
};
</script>
<style>
</style>