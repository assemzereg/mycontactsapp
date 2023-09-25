<template>
  <v-card
    class="mx-auto v-card-class"
    max-width="272"
    @click="redirect(contact.id.value)"
  >
    <v-img
      :src="contact.picture.large"
      height="204px"
      cover
    ></v-img>
    <div class="v-card-content">
<v-card-title>
      {{contact.name.first}} {{contact.name.last}}
    </v-card-title>

    <v-card-subtitle>
     <v-icon
      size="large"
      icon="mdi-email"
    ></v-icon> {{contact.email}}
    </v-card-subtitle>
    </div>
    

   
  </v-card>
</template>


<script lang="ts">
import { defineComponent } from 'vue';
import {Contact} from './Contact'
// Components

export default defineComponent({
  name: 'VirticalCardView',
  props:{
    contact:{}  as Contact | any
  },

  components: {
  },
  data(){
    return{
      numberOfContacts: 100,
     
    }
  },
  methods:{
    redirect(path: string){
        this.$router.push('/contact/'+path)
    }
  }


});
</script>

<style scoped>
.v-card-content{
    box-sizing: border-box;
    padding: 10px 5px;
}
.v-card-class:hover{
    box-shadow:  0px 2px 8px 0 rgba(0, 0, 0, 0.2), 0 2px 20px 0 rgba(0, 0, 0, 0.19)!important;
    cursor: pointer;
}
</style>