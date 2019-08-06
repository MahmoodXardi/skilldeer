<template>
  <div>
      <div class="container">
      <div class="columns is-centered">
      <div class="column is-9">
            <div class="content is-medium">
          <h3 class="title is-3"></h3>
              <div class="box">                
                <h4 id="const" class="title is-3">{{course.title}}</h4>                      
                <article class="message is-primary has-background-primary">                
                  <div class="message-body has-text-white ">
                    Instructor: {{course.provider_name}}  <br>
                    Location: {{course.location}} 
                  </div>
                </article>
                

               <div class="columns is-multiline is-centered">    
                  <div class="column is-2">  
                    <b-taglist attached>
                      <b-tag type="is-dark">Age</b-tag>
                      <b-tag type="is-primary"> {{course.age.min}} - {{course.age.max}}</b-tag>
                    </b-taglist>
                  </div>   

                  <div class="column is-4">  
                    <b-taglist attached>
                      <b-tag type="is-dark">Price</b-tag>
                      <b-tag type="is-primary"> 
                        {{course.packages[0].currency}} {{course.packages[0].price}} 
                      </b-tag>
                    </b-taglist> 
                  </div>   

                  <div class="column is-2">  
                    <b-taglist attached>
                      <b-tag type="is-dark">Gender</b-tag>
                      <b-tag type="is-primary"> 
                        {{course.gender  ? course.gender : 'Any'}}  
                      </b-tag>
                    </b-taglist> 
                  </div>


                  <div class="column is-2">  
                    <b-taglist attached>
                      <b-tag type="is-dark">Rating</b-tag>
                      <b-tag type="is-primary"> 
                        {{course.rating.stars}} stars
                      </b-tag>
                    </b-taglist> 
                  </div>
               </div>
               <br>
               <p class="has-text-primary">
                  {{course.description_short}}
                </p>
                <h5 class="is-pulled-left">Available Schedule</h5> <br> 
    
                <div v-for="(booking, index) in course.bookings" :key="index" >
                  <div class="control is-centered">
                  <b-taglist attached>
                    <b-tag type="is-dark">{{booking.description}}</b-tag> <br> <br>
                    <b-tag type="is-info">{{booking.title}}</b-tag>
                  </b-taglist>
                  </div>     
                </div>                
            </div>


        <div class="is-pulled-right">  
          <a :href="course.url" target="_blank">
          <b-button type="is-warning">Go to Course</b-button></a>
          <router-link 
            to="/explore"
            class="button is-danger"
            style="margin-left:10px;">
            Back
            </router-link>
          </div>
      </div>
      </div>
      </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios';

  export default {
    name: 'ClassDetails',
    data() {
      return {
        id: this.$route.params.id,
        course: {},
        
      }
    },
    created () {
      const path = `https://skilldeer.com/course/quick-view?id=${this.id}`;

         axios.get(path).then((response)=> {
          this.course = response.data;
          console.log(response.data);
          })
         .catch((error)=> {
            console.log('There is something wrong : '+ error);
          });
    },
    
  }
</script>

<style scoped>

/* @import url('https://use.fontawesome.com/releases/v5.2.0/css/all.css'); */

</style>
