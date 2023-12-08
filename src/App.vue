<template>
  <div>
    <form @submit.prevent>
      <input
          v-bind:value="title"
          @input="titleHandler"
          class="input"
          type="text"
          placeholder="Title: ">
      <input
          v-bind:value="desc"
          @input="desc=$event.target.value"
          class="input"
          type="text"
          placeholder="Desc: ">
      <button class="btn-post" @click="addPost">Add post</button>
    </form>
    <div class="posts" v-for="post in posts">
      <div class="post">
        <div><strong class="title">Title: </strong>{{post.title}}</div>
        <div><strong class="desc">Description: </strong>{{post.desc}}</div>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [
          {id:1, title: "JavaScript", desc: "about JS"},
          {id:2, title: "TypeScript", desc: "about TS"},
          {id:3, title: "Node.js", desc: "about Node.js"},
      ],
      title: '',
      desc: ''
    }
  },
  methods: {
    addPost(){
      const newPost = {
        id: new Date(),
        title: this.title,
        desc: this.desc
      }
      this.posts.push(newPost)
      this.title = ''
      this.desc = ''
    },
    titleHandler(e){
      this.title = e.target.value
    },
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.input {
  width: 100%;
  padding: 5px;
  margin-top: 5px;
  border: 1px solid teal;
}

.btn-post{
  margin-top: 5px;
  padding: 5px;
  background: #ffffff;
  border: 2px solid teal;
  border-radius: 5px;
  color: teal;
}

.title, .desc {
  font-weight: bold;
}

.post{
  padding: 15px;
  border: 1px solid teal;
  margin-top: 15px;
}

</style>
