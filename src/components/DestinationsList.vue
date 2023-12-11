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
</template>

<script setup>

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