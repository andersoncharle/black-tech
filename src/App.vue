<template>
<!--  <img alt="Vue logo" src="./assets/logo.png">-->
<!--  <HelloWorld msg="Welcome to Your Vue.js App"/>-->
  <h1>title of the book: {{ book.title}}</h1>
<!--attribtue binding-->
  <a :href="url" class="text-white">this is link</a>
  <div v-if="showBooks">
    <p class="bg-amber-800">{{book.author}} - {{book.age}}</p>
  </div>

  <button v-on:click="book.age++">increment age</button>
  <button v-on:click="book.age--">decrement age</button>
  <button @click="book.author ='mkakariaanerson'">change author</button>

  <button class="bg-red-700 py-3 px-6 rounded-lg block" @click="changeTitle('this is new title anderson')">change title</button>

  <button @click="toggleShowBooks" class="bg-blue-500 py-3 px-6 rounded-lg flex">
<!--    <span v-if="!showBooks">show books</span>
instead use v-else
-->
    <span v-if="showBooks">hide books</span>
    <span v-else>show books</span>
  </button>
<!--v show-->
  <div v-show="showBooks" class="text-white w-1/2 mx-auto p-3 bg-purple-500">currently show books</div>

<!-- mouse events -->
  <div class="box" @mouseover="handleEvent($event,5)">mouseover event</div>
  <div class="box" v-on:mouseleave="handleLeaveEvent">mouseleave event</div>
  <div class="box" v-on:dblclick="handleDoubleClickEvent">double click event</div>
  <div class="box" @mousemove="handleMousemoveEvent">mouse move events: {{ x }} : {{ y }}</div>

  <div v-if="showBooks">hide books
      <ul class="text-white text-justify">
    <li v-for="book in books" :key="book" class="p-3 divide-y-2 divide-amber-700">
    <h1>{{book.title}}</h1>
      <p>{{book.author}}</p>
      <p>{{book.age}}</p>
    </li>
  </ul>
    </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data(){
    return{
      url: "https://www.youtube.com/",
      showBooks:true,
      book : {
        title : "code with vue",
        author: "anderson",
        age: 45
      },
      books: [
        {title: "name of wind",author:"mkakari",age:20},
        {title: "land of the wind",author:"rose",age:34},
        {title: "merlin",author:"asha",age:19},
        {title: "tailwind css",author:"john",age:25},
      ],
      x: 0,
      y:0
    }
  },
  methods:{
    changeTitle(title){
      this.book.title= title
    },
    toggleShowBooks(){
      this.showBooks = !this.showBooks
    },
    handleEvent(e,data){
      console.log("mouse over events")
      console.log(e,e.type)
     if (data){
       console.log(data)
     }
    },
    handleLeaveEvent(){
      alert("mouse leave event")
    },
    handleDoubleClickEvent(){
      alert("handle Double Click Event")
    },
    handleMousemoveEvent(e){
      this.x = e.offsetX
      this.y = e.offsetY
      console.log(e)
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
