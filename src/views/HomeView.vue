<template>
  <div>
    <h1>Home</h1>

    <button class="btn btn-danger my-5" @click="getData()">click</button>
    <h1 v-if="loadingStatus">Loading....</h1>
    <div v-else>
      <h1>data have</h1>
    </div>

  </div>
</template>

<script>
  export default {
    name:"HomeView",
    data() {
      return {
        loadingStatus : false,
      }
    },
    methods : {
      getData(){
        this.loadingStatus = true;
      fetch('https://fakestoreapi.com/products')
            .then(res=>res.json())
            .then(json=>{console.log(json)
            this.loadingStatus = false;
            });
    }
    }
  }
</script>
