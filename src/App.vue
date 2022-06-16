<template>
<!--  <img alt="Vue logo" src="./assets/logo.png">-->
<!--  <HelloWorld msg="Welcome to Your Vue.js App"/>-->
  <h1>title of the book: {{ book.title}}</h1>

  <div v-if="showBooks">
    <p class="bg-amber-800">{{book.author}} - {{book.age}}</p>
  </div>

  <button v-on:click="book.age++">increment age</button>
  <button v-on:click="book.age--">decrement age</button>
  <button @click="book.author ='mkakariaanerson'">change author</button>

  <button class="bg-red-700 py-3 px-6 rounded-lg block" @click="changeTitle('this is new title anderson')">change title</button>

  <button @click="toggleShowBooks" class="bg-blue-500 py-3 px-6 rounded-lg flex">
    <span v-if="showBooks">hide books</span>
<!--    <span v-if="!showBooks">show books</span>
instead use v-else
-->
    <span v-else>show books</span>
  </button>
<!--v show-->
  <div v-show="showBooks" class="text-white w-1/2 mx-auto p-3 bg-purple-500">currently show books</div>

<!-- mouse events -->
  <div class="box" @mouseover="handleEvent"></div>
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>


</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data(){
    return{
      showBooks:true,
      book : {
        title : "code with vue",
        author: "anderson",
        age: 45
      }
    }
  },
  methods:{
    changeTitle(title){
      this.book.title= title
    },
    toggleShowBooks(){
      this.showBooks = !this.showBooks
    }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
