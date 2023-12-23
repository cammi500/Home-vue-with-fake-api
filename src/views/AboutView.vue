<template>
  <div class="container">
    <div class="row">
      <div class="col-4">
        <div class="row">
          <div class="col-2 offset-1">Title</div>
          <div class="col">
            <input type="text" class="form-control" placeholder="enter title" name="" id="" v-model="title">
          </div>
        </div>
        <div class="row mt-4">
          <div class="col-2 offset-1">Author</div>
          <div class="col">
            <input type="text" class="form-control" placeholder="enter author"  v-model="author">
          </div>
        </div>
        <div class="row mt-4">
          <div class="col-2 offset-1">Message</div>
          <div class="col">
            <textarea class="form-control" placeholder="enter massage" cols="30" rows="10" v-model="description"></textarea>
          </div>
        </div>

        <button class="btn bg-dark text-white mt-4 col-5" @click="saveInfo()">Save</button>
        <div class="col">
          <div v-for="(list,index) in lists" :key="index" class="my-3 shadow-sm">
          <div class="card" style="">
            <div class="card-body">
              <h5 class="card-title">{{ list.title }}</h5>
              <p class="card-text">{{list.description}}</p>
              <p class="card-text">{{list.author}}</p>
            </div>
          </div>
      </div>
    </div>
  </div>
</div>
</div>
  <!-- <div class="container">
    
      <div class="">
        <div class="row">
          <div class="col-4">
            <div class="row">
                <div class="col-2">title</div>
                <div class="col">
                  <input type="text" class="form-control" placeholder="enter title">
                </div>
            </div>
            <div class="col-2">title</div>
                <div class="col">
                  <input type="text" class="form-control" placeholder="enter title">
                </div>
          </div>
          <div class="col-8">
            <div class="" v-for="(list,index) in lists" :key="index"></div>
            <div class="card" style="">
              <div class="card-body">
                <div class="card-title">{{list.title}}</div>
                <p class="card-text">{{list.description}}</p>
                <p class="card-text">{{list.author}}</p>
              </div>
            </div>
          </div>
          </div>
        </div>
      </div> -->
    
</template>
<script>
import axios from "axios";
  export default {
    name : "AboutView",
    data() {
      return {
        lists :[],
        title : "",
        author : "",
        description : "",
      }
    },
    methods :{
      saveInfo() {
        let myData = {
          id : "1000",
          title : this.title,
          author : this.author,
          description : this.description,
        };
        console.log(myData);
      },
    },
    mounted(){
      axios.get("http://localhost:3000/posts")
      .then((response) => {
        this.lists = response.data;
          // console.log(response.data);
      });
    }
  }
</script>


