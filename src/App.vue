<template>
  <div id="app">
<!--    <div class="card"
         v-for="(item, index) in items"
         :key="index"
    >
      <h2>
        {{ item.title }}
      </h2>
      <img
          :src="item.url"
          alt="img"
      >
    </div>-->
    <div class="new-post-block">
      <form>
        <label for="title">title</label>
        <input id="title" type="text" v-model="formTitle">
        <label for="body">body</label>
        <input id="body" type="text" v-model="formBody">
        <div class="button" @click="postPost">post</div>
      </form>
      <div
        v-if="mes === 201"
        class="message"
      >
          Успешно!
      </div>
      <div class="data">
          <div class="title">
              {{ this.title }}
          </div>
          <div class="body">
              {{ this.body }}
          </div>
      </div>
    </div>
  </div>
</template>

<script>

import axios from "axios";

export default {
  name: 'App',
  data () {
    return {
      items: [],
      formTitle: '',
      formBody: '',
      mes: '',
      title: '',
      body: ''
    }
  },
    methods: {
      postPost () {
        axios.post('https://jsonplaceholder.typicode.com/posts', {
          title: this.formTitle,
          body: this.formBody,
        })
        .then(response => {
            this.mes = response.status
            this.body = response.data.body
            this.title = response.data.title
        })
      }
    },

  /*created() {
    axios.get('https://jsonplaceholder.typicode.com/photos?_limit=10')
    .then(response => {
      this.items = response.data
      console.log(this.items)
    })

  }*/
}
</script>

<style>
#app {
  display: flex;
  flex-wrap: wrap;
}

/*h2  {
  text-align: center;
}
.card {
  box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.58);
  width: 300px;
  height: 300px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin: 10px;
}
img {
  max-width: 300px;
  max-height: 100px;
  margin-top: 10px;
}*/

form {
    display: flex;
    align-items: flex-start;
    flex-direction: column;
}
.button {
    margin-top: 10px;
}
.button {
    background: peachpuff;
    padding: 5px 10px;
    border-radius: 2px;
    cursor: pointer;
}
</style>
