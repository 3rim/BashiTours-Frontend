<script setup>
import DestinationsList from '@/components/DestinationsList.vue';
import Worldmap from '@/components/Worldmap.vue';
import LoadingSpinner from '@/components/LoadingSpinner.vue';
</script>

<template>
  <main class="container">
    <Suspense>
      <Worldmap/>
      <template #fallback>
        <LoadingSpinner :text="'Worldmap Data'"/>
      </template>
    </Suspense>
    <Suspense>
      <DestinationsList/>
      <template #fallback>
        <LoadingSpinner :text="'Destinations'"/>
      </template>
    </Suspense>
    
  </main>
</template>
