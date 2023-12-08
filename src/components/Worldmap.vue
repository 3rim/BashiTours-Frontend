<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <div>
        <div id="map"></div>
        <button @click="test" class=" bg-red-100 rounded-sm">click</button>
    </div>
</template>

<script setup>
import { onMounted } from 'vue';

onMounted (() =>{
    simplemaps_worldmap.load();
})

const test = () => {
  console.log("das")
  simplemaps_worldmap.mapdata.main_settings.state_color = 'red';
  simplemaps_worldmap_mapdata.state_specific['DE'].color='blue';
  simplemaps_worldmap.refresh();
}
</script>
