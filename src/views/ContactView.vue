<template>
  <div class="contact-container">
    <v-btn prepend-icon="mdi-arrow-left" variant="text" @click="back">
      Go back to contact list 
    </v-btn>
  <div>
  </div>
  <v-card
    class="card-cont"
    v-if="!isFetching && data && JSON.parse(data).results"
  >
    <v-img
      :src="JSON.parse(data).results[0].picture.medium"
      class="image"
    ></v-img>
    <div class="details">

    <h1 class="name">{{JSON.parse(data).results[0].name.first}} {{JSON.parse(data).results[0].name.last}}</h1>
    <div class="info">
       <v-icon
      size="large"
      icon="mdi-phone"
    ></v-icon>
    <div class="contain-info">
      <span class="info-title">phone</span>
      <span class="info-value">{{JSON.parse(data).results[0].phone}}</span>
    </div>
    </div>
    <div class="info">
       <v-icon
      size="large"
      icon="mdi-cake"
    ></v-icon>
    <div class="contain-info">
      <span class="info-title">Birth Date</span>
      <span class="info-value">{{JSON.parse(data).results[0].dob.date}}</span>
    </div>
    </div>
    <div class="info">
       <v-icon
      size="large"
      icon="mdi-card-account-details"
    ></v-icon>
    <div class="contain-info">
      <span class="info-title">Social Number</span>
      <span class="info-value">{{JSON.parse(data).results[0].id.value}}</span>
    </div>
    </div>
    <div class="info">
       <v-icon
      size="large"
      icon="mdi-earth"
    ></v-icon>
    <div class="contain-info">
      <span class="info-title">Country</span>
      <span class="info-value">{{JSON.parse(data).results[0].location.country}}</span>
    </div>
    </div>
    
    
    </div>
  </v-card>
  </div>
</template>

<script lang='ts'>
import { defineComponent } from 'vue';
import { useFetch } from '@vueuse/core';
import { useRoute } from 'vue-router'

export default defineComponent({
  name:'ContactView',
  methods:{
    back(){
      this.$router.push('/')
    }
  },
  data(){
    return{
      contact:{
      
            "gender": "male",
            "name": {
                "title": "Mr",
                "first": "Ievlampiy",
                "last": "Paholyuk"
            },
            "location": {
                "street": {
                    "number": 5145,
                    "name": "Bazhana"
                },
                "city": "Chigirin",
                "state": "Ivano-Frankivska",
                "country": "Ukraine",
                "postcode": 22900,
                "coordinates": {
                    "latitude": "77.4054",
                    "longitude": "-66.4842"
                },
                "timezone": {
                    "offset": "+3:00",
                    "description": "Baghdad, Riyadh, Moscow, St. Petersburg"
                }
            },
            "email": "ievlampiy.paholyuk@example.com",
            "login": {
                "uuid": "5a880f52-c5b2-45a4-bc1b-e52f9e0820cb",
                "username": "bigpeacock917",
                "password": "scorpion",
                "salt": "WtQjxOro",
                "md5": "1549cf0d585a7d505a0dd03e20ad68c3",
                "sha1": "6a985af75d6dddc0c1560bd3b0e886aeaf5cff8e",
                "sha256": "d012cf7485b5d12b9d196a5f09db47b2d63bf049891123748d2aca8e981492d0"
            },
            "dob": {
                "date": "1964-10-09T06:17:51.081Z",
                "age": 58
            },
            "registered": {
                "date": "2004-11-14T02:19:08.815Z",
                "age": 18
            },
            "phone": "(097) Y05-1077",
            "cell": "(066) W42-1139",
            "id": {
                "name": "PPS",
                "value": "1416560T"
            },
            "picture": {
                "large": "https://randomuser.me/api/portraits/men/98.jpg",
                "medium": "https://randomuser.me/api/portraits/med/men/98.jpg",
                "thumbnail": "https://randomuser.me/api/portraits/thumb/men/98.jpg"
            },
            "nat": "UA"
        }
    }
  },
  setup() {
    const route = useRoute()
    const { data, error, isFetching } =  useFetch('https://randomuser.me/api/?id.value='+route.params.id)
    const numberOfContacts = 100;
  
   
    return {
      data,
      error,
      isFetching,
      numberOfContacts,
    };
  },
})
</script>

<style scoped>
.contact-container{
  width: 45%;
  margin: 15px auto;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 10px;
}
.card-cont{
  width: 100%;
  display: flex;
  align-items: center;
  box-sizing: border-box;
  padding: 15px 10px;
}
.image{
  width: 128px;
  height: 128px;
  object-fit: cover;
}
.details{
  width: 65%;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 15px;
}
.name{
  font-size: 28px;
  font-weight: 500;
}
.info{
  display: flex;
  align-items: center;
  gap: 20px;
  margin-left: 20px;
}
.contain-info{
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  
}
.info-title{
  color: rgba(0,0,0,.6);
  font-size: .875rem;
}
.info-value{
  font-size: 1rem;
  color: rgba(0,0,0,.87);
}
</style>
