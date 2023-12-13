<script setup>
import DestinationsList from '@/components/DestinationsList.vue';
import Worldmap from '@/components/Worldmap.vue';

</script>

<template>
  <main class="container">
    <Suspense>
      <Worldmap/>
      <template #fallback>
            Loading...
      </template>
    </Suspense>
    <!-- TODO: DestinationsList , add suspense later -->
    <DestinationsList/>
    
  </main>
</template>
