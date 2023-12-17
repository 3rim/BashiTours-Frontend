<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <!-- Container for simplemaps worldmap -->
    <div class="flex flex-col mt-4">
        <div class="bg-[#092635] p-0.5 rounded-md shadow-2xl ">
            <div class="bg-[#092635] " id="map"></div>
        </div>
        
        <div class="flex justify-center">
            <button
            @click="openModal"
            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded ">
              Button
            </button>
        </div>
    <CountryModal :key="componentKey" :is-open="showCountryModal" :country="country"/>
    </div>

</template>

<script setup>
import { ref, onMounted, } from 'vue';
import CountryModal from './CountryModal.vue';

const showCountryModal = ref(false)
const componentKey = ref(0)
const visitedCountriesDummy = ["DE","AL","US"]
const country = ref("");

const loadVisitedCountries = async () =>{
    //Late API-Call
    
    await new Promise(resolve => setTimeout(resolve,300))
    //Test Mock-loading
    visitedCountriesDummy.forEach(element => {
        console.log(element)
        simplemaps_worldmap.mapdata.state_specific[element].color='#9EC8B9';
        simplemaps_worldmap.mapdata.state_specific[element].description='visited';
        
    });
    //simplemaps_worldmap.load();
}
await loadVisitedCountries();

onMounted (() =>{
    simplemaps_worldmap.load();
})

const openModal = () => {
    showCountryModal.value = true
    forceRenderer()
}
//Re-render component if necessary
const forceRenderer = () => {
    componentKey.value +=1
}

simplemaps_worldmap.hooks.click_state = function(id){
     var description = simplemaps_worldmap.mapdata.state_specific[id].description;
     country.value = simplemaps_worldmap.mapdata.state_specific[id].name;
     if(description === "visited"){
        openModal();
     }
        
   }

const test = () => {
  console.log("change color ")
  //simplemaps_worldmap.mapdata.main_settings.state_color = 'red';
  simplemaps_worldmap.mapdata.state_specific['DE'].color='#9EC8B9';
  console.log(simplemaps_worldmap.mapdata.state_specific['DE'].visited)
  simplemaps_worldmap.mapdata.state_specific['DE'].color='#9EC8B9';

  simplemaps_worldmap.refresh();
}

</script>
