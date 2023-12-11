<script setup>
import DestinationsList from '@/components/DestinationsList.vue';
import Worldmap from '@/components/Worldmap.vue';

</script>

<template>
  <main class="">
    <Suspense>
      <Worldmap/>
    </Suspense>
    <!-- TODO: DestinationsList , add suspense later -->
    <DestinationsList/>
    
  </main>
</template>
