
<template>
  <div>
    <div class="mt-30">
    <h1 class="title is-3 ">Discover local classes <br> Learn new skills </h1>
    
    </div>

    <!-- Datepicker -->
    <div class="container">
      <div class="row ">
        <div class="columns">
          <div class="column is-6 is-offset-3 mt-30">
            <b-field label="Filter by date">
              <b-datepicker
                  placeholder="Click to select..."
                  v-model="dates"
                  range>
              </b-datepicker>
            </b-field>
          </div>
        </div>
      </div>
    </div>
    <br>
    <!-- Search button to grab data api -->
    <b-button type="is-primary" @click.prevent="getClasses">Search</b-button>
  


<keep-alive>
<section class="section">
<div class="container">
<div class="columns is-multiline is-centered ">    
  
  <div class="column is-4" v-for="course in classes" :key="course.id">  
  <div class="card">
    <div class="card-image">
      <figure class="image is-4by3">
        <img :src="course.photo" alt="Course image">
      </figure>
    </div>
  <div class="card-content">
    <b-taglist>
      <b-tag type="is-warning">{{course.start | moment('h:mm A')}} </b-tag>
    </b-taglist>
    
    <p class="title is-4"> {{course.title}} </p>   
    
    <b-message type="is-success">
      <p class="subtitle is-6"> Start date :  {{course.start | moment("Do, MMMM  YYYY")}} </p>
    </b-message>

    <div class="content">
      <b-tooltip label="Get more information" position="is-right" type="is-dark">
      <router-link 
          :to="'/course/'+ course.id"
          class="button is-primary">
          Show details
      </router-link>
      </b-tooltip>

        <br>
  
        </div>
      </div>
    </div>
  </div>
 </div>
</div>
</section>
</keep-alive>
  </div>
</template>

<script>
  import axios from 'axios';
  import Datepicker from '../components/Datepicker';

  export default {
    name: 'About',
    components: {
      Datepicker,
    },
    data() {
      const today = new Date();
      return {
        dates: [  // initial date 
          today,
          new Date(today.getFullYear(), today.getMonth(), today.getDate() + 2)
        ],
        classes:[],
        
      }
    },
    computed: {
      start() {   // date format yyyy-mm-dd
      return this.dates[0].getFullYear()+'-'+(this.dates[0].getMonth()+1)+'-'+this.dates[0].getDate();
      },
      end() {
      return this.dates[1].getFullYear()+'-'+(this.dates[1].getMonth()+1)+'-'+this.dates[1].getDate();
      },
      
    },
    methods: {
      getClasses(){
        const path = `https://skilldeer.com/calendar/list?start=${this.start}&end=${this.end}`;

         axios.get(path).then((response)=> {
          this.classes = response.data;
          //console.log(this.classes);
          })
         .catch((error)=> {
            console.log('There is something wrong : '+ error);
          });
         
      }
   
    }}
</script>

<style scoped>
@import url('https://use.fontawesome.com/releases/v5.2.0/css/all.css');
@import url('https://cdn.materialdesignicons.com/2.5.94/css/materialdesignicons.min.css');

.mt-30 { 
  margin-top: 30px;
}
</style>
