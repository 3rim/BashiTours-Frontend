<template>
    <div class=" container flex flex-col items-center bg-[#9EC8B9] rounded-md">
        <h2 class=" font-bold underline">Next Destinations</h2>
        <table class="w-full">
            <thead class="text-gray-700 text-s font-bold">
                <tr class="">
                    <th>Country</th> <th>Spots</th> <th>Companions</th> <th>Date</th> <th>Action</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(country,index) in mockDestinationData" v-bind:key="index"
                class="text-center" >
                    <td>{{ country.country }}</td>
                    <td>
                        <span v-for="(spot,index) in country.spots" :key="index">
                            {{ spot }},
                        </span>
                    </td>
                    <td>
                        <span v-for="(companions,index) in country.companions" :key="index">
                            {{ companions }},
                        </span>
                    </td>
                    <td>{{ country.date }}</td>
                </tr>
            </tbody>
        </table>
    </div>
    <button
      type="button"
      @click="openModal"
      class="rounded-md bg-black/20 px-4 py-2 text-sm font-medium text-white hover:bg-black/30 focus:outline-none focus-visible:ring-2 focus-visible:ring-white/75"
    >
      Open dialog
    </button>
    <DestinationModal :key="componentKey" :is-open="isOpen" />
    
</template>

<script setup>
import { ref } from 'vue';
import DestinationModal from './DestinationModal.vue'

const isOpen = ref(false)

function openModal() {
  isOpen.value = true
  console.log("openModal")
  forceRerender()
}

const componentKey = ref(0);
//Re-render component if necessary
const forceRerender = () => {
    componentKey.value += 1;
    console.log(componentKey.value)
  };

const mockDestinationData = [
    {country: "Germany",spots:["Hamburg","Berlin"],companions:["Erim","Imon"],date:"12.12.2025"},
    {country: "Germany",spots:["Hamburg","Berlin"],companions:["Erim","Imon"],date:"12.12.2025"},
    {country: "Germany",spots:["Hamburg","Berlin"],companions:["Erim","Imon"],date:"12.12.2025"},
    {country: "Germany",spots:["Hamburg","Berlin"],companions:["Erim","Imon"],date:"12.12.2025"},
    {country: "Germany",spots:["Hamburg","Berlin"],companions:["Erim","Imon"],date:"12.12.2025"},
    {country: "Germany",spots:["Hamburg","Berlin"],companions:["Erim","Imon"],date:"12.12.2025"},
    {country: "Germany",spots:["Hamburg","Berlin"],companions:["Erim","Imon"],date:"12.12.2025"},
    {country: "Germany",spots:["Hamburg","Berlin"],companions:["Erim","Imon"],date:"12.12.2025"}
]

</script>