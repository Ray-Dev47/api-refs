<template>
  <div>
    <h2>Hello</h2>
    <div v-if="jokes">
        <p @click="newJokes">{{jokes}}</p>
      <button @click="newJokes">Click to get random jokes</button>
    </div>
    <div v-else>
        <p>Loading jokes.....</p>
    </div>
      

  </div>
</template>

<script>
export default {
    data(){
  return {
       jokes: null  
  }
},
methods:{
    getJokes(){
        let jokeUrl = 'https://api.chucknorris.io/jokes/random';
        fetch(jokeUrl)
        .then(response => response.json())
        .then((response) => {
           this.jokes = response.value
          //  console.log(response)
        })
        .catch(err => console.log(err.message))
    },
    newJokes(){
      this.getJokes()
      
    }
},
   mounted(){
       this.getJokes()
   }

};

</script>

<style>
</style>