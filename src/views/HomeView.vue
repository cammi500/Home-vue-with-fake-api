<template>
  <div class="container">
    <h1>Home</h1>

    <button class="btn btn-danger my-5" @click="getData()">click</button>
    <h1 v-if="loadingStatus">Loading....</h1>
    <div v-else>
      <h1>data have</h1>
    </div>

    <table class="table table-striped">
      <thead>
        <tr>
          <th scope="col">ID</th>
          <th scope="col">Category</th>
          <th scope="col">Des</th>
          <th scope="col">Image</th>
        </tr>
      </thead>
      <tbody>
        <tr v-if="posts.length ==0">
          <th scope="row" colspan="4" >There i no data</th>
        </tr>
        <tr v-else v-for="(p,index) in posts" :key="index">
          <th scope="row">{{ p.id }}</th>
          <td>{{p.category}}</td>
          <td>{{p.price}}</td>
          <td>
            <img :src="p.image" width="100" height="100"/>
          </td>
        </tr>
       
      </tbody>
    </table>
  </div>
</template>

<script>
  export default {
    name:"HomeView",
    data() {
      return {
        loadingStatus : false,
        posts: [],
      }
    },
    methods : {
      getData(){
        this.loadingStatus = true;
      fetch('https://fakestoreapi.com/products')
            .then(res=>res.json())
            .then((json) =>{
              this.posts = json;
              this.loadingStatus = false;
            });
    }
    }
  }
</script>
