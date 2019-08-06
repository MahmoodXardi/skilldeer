<template>
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
</template>

<script>
  export default {
    name: 'Datepicker',
    data() {
      const today = new Date();
      return {
        dates: [  // initial date 
          today,
          new Date(today.getFullYear(), today.getMonth(), today.getDate() + 2)
        ]
      }
    },
  }
</script>

<style scoped>
/* @import url('https://use.fontawesome.com/releases/v5.2.0/css/all.css');
@import url('https://cdn.materialdesignicons.com/2.5.94/css/materialdesignicons.min.css'); */

</style>