<template>
  <div>
    <!-- <h2>Hello</h2>
    <div v-if="jokes">
        <p @click="newJokes">{{jokes}}</p>
      <button @click="newJokes">Click to get random jokes</button>
    </div>
    <div v-else>
        <p>Loading jokes.....</p>
    </div> -->


     <ul v-for="post in meowFacts" :key="post.id">
      <li>{{post.body}}</li>
     </ul>
      

  </div>
</template>

<script>
import axios from 'axios'

export default {
    data(){
  return {
      //  jokes: null  
      meowFacts: null
  }
},
methods:{
    // getJokes(){
    //     let jokeUrl = 'https://api.chucknorris.io/jokes/random';
    //     fetch(jokeUrl)
    //     .then(response => response.json())
    //     .then((response) => {
    //        this.jokes = response.value
    //       //  console.log(response)
    //     })
    //     .catch(err => console.log(err.message))
    // },
    // newJokes(){
    //   this.getJokes()
      
    // }
    
    // *********** Axios method *********************
    async fetchMeowFactRes(){
         await axios.get('https://jsonplaceholder.typicode.com/posts') 
         .then(response => this.meowFacts = response.data)
            // this.results = response.data
            //  this.meowFacts = response
            .catch((err) => console.log(err.message))
       
        
         
         
        
        
    }


},
   mounted(){
  this.fetchMeowFactRes()
}
}
</script>

<style>
</style>