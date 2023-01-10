<template>
  <div>
    <h2>Hello</h2>
    <div v-for="joke in jokes" :key="joke.id">
     

    </div>
      <p @click="newJokes">{{jokes}}</p>
      <button @click="newJokes">Click to get random jokes</button>

  </div>
</template>

<script>
export default {
    data(){
  return {
       jokes: []    
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
        .catch(err => console.log())
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