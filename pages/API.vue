<template>
       <b-container class="api">
              <Card 
              v-for="(string,i) of info"
              :key="i"
              :info="string"
              
               />
               
       </b-container>
  
</template>



<script>
//import components
import Card from "../../restaurant/components/Card.vue"
import axios from 'axios'


export default {
  components: {
    Card
  },
   data() {
    return {
      loading: true,
      info:null,
      errored: false
    }
  },
  methods: {
    //need to make (maybe recursive function?) here that will make an api call when get to bottom of screen, and then put that function in mounted
    getInitialDogs() {
     axios
     //api call
      .get('https://dog.ceo/api/breeds/image/random/99')
      .then(response => {
        //assign response to message
        this.info = response.data.message
        
      })
    .catch(error => {
 
      console.log(error)
      this.errored = true
    })
    .finally(() => this.loading = false)
  }
  ,
    getNextDog() {
      window.onscroll = () => {
        //need to add recusive functionality to this?
        //https://www.digitalocean.com/community/tutorials/vuejs-implementing-infinite-scroll
        let bottomOfWindow = document.documentElement.scrollTop + window.innerHeight === document.documentElement.offsetHeight;
        if (bottomOfWindow) {
          axios
      .get('https://dog.ceo/api/breeds/image/random/99')
      .then(response => {
        this.info = response.data.message
        
      })
    .catch(error => {
 
      console.log(error)
      this.errored = true
    })
    .finally(() => this.loading = false)
        }
      }
    }
    },
  beforeMount(){
    this.getInitialDogs();
    
  },
   mounted () {
  this.getNextDog();
  }
  }








</script>

<style lang="scss">
@import './css/_settings.responsive.scss';

.api {
    display: flex;
    justify-content: space-around;
    align-items: center;
    flex-wrap: wrap;
    @include media-query('mobile'){
        flex-direction: column;
         justify-content: space-between;
         align-items: center;
    }
}
  

</style>