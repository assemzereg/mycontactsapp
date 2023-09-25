<template>
<div class="home-container" >
<div class="search-container">

  <div v-if="isFetching">
    <p>
      Loading... {{isFetching}}
      </p>


  </div>
  <div v-if="!isFetching">

  <span class="number-of-contacts">{{ numberOfContacts }} Contact(s)</span>
  </div>
  <div class="input-cont">

 <v-text-field
  variant="outlined"
  label="Search..."
  prepend-inner-icon="mdi-magnify"
  color="#007bff"
  clearable 
  hide-details="true"
  v-model="searchQuery"
  ></v-text-field>
  </div>
</div>
<div  v-if="!isFetching && data && JSON.parse(data).results" class="content-container" >

  <card-vue v-for="contact in JSON.parse(data).results" :key="contact.id.value" :contact="contact" />
     



</div>
</div>

</template>

<script lang="ts">
import { defineComponent, ref  } from 'vue';
import { useFetch } from '@vueuse/core';

import _ from 'lodash'
// Components
import CardVue from '../components/CardContact.vue';



export default defineComponent({
  name: 'HomeView',

  components: {
    CardVue,
  },

  setup() {
    const { data, error, isFetching } =  useFetch('https://randomuser.me/api/?results=100')
    const numberOfContacts = 100;
    const searchQuery = ref<string>('');
    

 
   
    return {
      data,
      error,
      isFetching,
      searchQuery,
      numberOfContacts,
    };
  },

});
</script>


<style scoped>
.home-container{
  width: 86%;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 25px;
  margin: 20px auto;
}
.search-container{
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.content-container{
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}
.number-of-contacts{
  font-size: 2.125rem!important;
    line-height: 2.5rem;
    letter-spacing: .0073529412em!important;
}
.input-cont{
  width: 50%;
}
</style>