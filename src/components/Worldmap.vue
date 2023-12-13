<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <!-- Container for simplemaps worldmap -->
    <div class="flex flex-col mt-4">
        <div class="bg-[#092635] p-0.5 rounded-md shadow-2xl ">
            <div class="bg-[#092635] " id="map"></div>
        </div>
        
        <div class="flex justify-center">
            <button
            @click="test"
            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded ">
              Button
            </button>
        </div>
        
    </div>
</template>

<script setup>
import { onMounted } from 'vue';

onMounted (() =>{
    simplemaps_worldmap.load();
})

const test = () => {
  console.log("change color ")
  //simplemaps_worldmap.mapdata.main_settings.state_color = 'red';
  simplemaps_worldmap.mapdata.state_specific['DE'].color='#9EC8B9';
  simplemaps_worldmap.refresh();
}
</script>
