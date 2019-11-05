<template>
  <div id="app">
  <Header/>
  <b-container class="bv-example-row">
  <b-row>
    <b-col sm="6" offset="3">
      <QuestionBox :next="next" :currentQuestion="questions[index]" />
    </b-col>
 
  
  </b-row>
</b-container>
  
  </div>
</template>

<script>
import Header from './components/Header'
import QuestionBox from './components/QuestionBox'

export default {
  name: 'app',
 
  components: {
    Header,QuestionBox
  },
  data(){
return{
  questions:[],
  index:0
}
  },
  methods:{
    next:function(){
this.index++
    }
  },
  mounted:function(){
     fetch("https://opentdb.com/api.php?amount=10&category=27&type=multiple")
  .then((resp) => resp.json()) // Transform the data into json
  .then((data) =>{
    // Create and append the li's to the ul
   console.log(data.results)
   this.questions=data.results;
    })
  }
  
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
