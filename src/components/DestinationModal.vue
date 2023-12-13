<template>
  <TransitionRoot appear :show="showModal" as="template">
    <Dialog as="div" @close="closeModal" class="relative z-10">
      <TransitionChild
        as="template"
        enter="duration-300 ease-out"
        enter-from="opacity-0"
        enter-to="opacity-100"
        leave="duration-200 ease-in"
        leave-from="opacity-100"
        leave-to="opacity-0"
      >
        <div class="fixed inset-0 bg-black/25" />
      </TransitionChild>

      <div class="fixed inset-0 overflow-y-auto">
        <div
          class="flex min-h-full items-center justify-center p-4 text-center"
        >
          <TransitionChild
            as="template"
            enter="duration-300 ease-out"
            enter-from="opacity-0 scale-95"
            enter-to="opacity-100 scale-100"
            leave="duration-200 ease-in"
            leave-from="opacity-100 scale-100"
            leave-to="opacity-0 scale-95"
          >
            <DialogPanel
              class="w-full max-w-xl transform overflow-hidden rounded-2xl bg-white p-6 text-left align-middle shadow-xl transition-all"
            >
              <DialogTitle
                as="h3"
                class="text-lg font-medium leading-6 text-gray-900"
              >
                Add new Destination
              </DialogTitle>
              <div class="mt-2">
                <form >
                  <!--Country-->
                  <div class="flex flex-wrap">
                    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
                      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="country">Country</label>
                      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border  rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" type="text" id="country" placeholder="Country" v-model="country" required>
                    </div>
                    <!--Date -->
                    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
                      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="date">Date</label>
                      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border  rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" type="text" id="date" placeholder="Date" v-model="date">
                    </div>
                    <!-- Spots -->
                    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
                     <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="spots">Spots</label>
                      <div class="flex flex-row">
                        <input  v-on:keyup.enter="addSpot" class="appearance-none block w-full bg-gray-200 text-gray-700 border  rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" type="text" placeholder="Spots" name="" id="spots" v-model="tempSpots">
                        <button @click="addSpot"
                        type="button"
                        class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-3 px-2 mb-3 rounded-r-md">Add</button>
                      </div>
                      <div v-for="(element,index) in spots" :key="index"
                      class="text-xs font-semibold inline-block py-1 px-2  rounded-full text-sky-600 bg-sky-200  last:mr-0 mr-1 hover:cursor-pointer">
                        <span @click="removeSpot(element)">{{ element }}</span>
                      </div>
                    </div>
                    <!--Companions-->
                    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
                      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="companions">Companions</label>
                      <div class="flex flex-row">
                        <input v-on:keyup.enter="addCompanion" class="appearance-none block w-full bg-gray-200 text-gray-700 border rounded-l-md py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" type="text" placeholder="companions" name="" id="companions" v-model="tempCompanions">
                        <button type="button" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-3 px-2 mb-3 rounded-r-md" @click="addCompanion">Add</button>
                      </div>
                      <div v-for="(element,index) in companions" :key="index"
                      class="text-xs font-semibold inline-block py-1 px-2  rounded-full text-sky-600 bg-sky-200  last:mr-0 mr-1 hover:cursor-pointer">
                        <span @click="removeCompanion(element)">{{ element }}</span>
                      </div>
                    </div>
                  </div>
                </form>
                 <!--Submit-->
                 <div class="mt-4">
                   <button
                      class="inline-flex justify-center rounded-md border border-transparent bg-blue-100 px-4 py-2 text-sm font-medium text-blue-900 hover:bg-blue-200 focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-500 focus-visible:ring-offset-2"
                      @click="submitForm"
                    >
                    Submit!
                    </button>
                 </div>
              </div>
            </DialogPanel>
          </TransitionChild>
        </div>
      </div>
    </Dialog>
  </TransitionRoot>
</template>

<script setup>
import {TransitionRoot,TransitionChild,Dialog,DialogPanel,DialogTitle,} from '@headlessui/vue';
import { ref } from 'vue';

const props = defineProps(['isOpen']);
const country = ref("");
const date = ref("");
const tempSpots = ref("");
const spots = ref([]);
const companions = ref([]);
const tempCompanions = ref("");

const showModal = ref(props.isOpen)

function closeModal() {
    showModal.value = false
}

const submitForm = () =>{
  console.log("subitForm")
  closeModal()
}

const addSpot = () => {
  console.log("add spot")
  if(tempSpots.value){
    if(!spots.value.includes(tempSpots.value)){
      console.log(tempSpots.value)
      spots.value.push(tempSpots.value)
    }
    tempSpots.value ="";
  }
}
const addCompanion = () => {
  if(tempCompanions.value){
    if(!companions.value.includes(tempCompanions.value)){
      console.log(tempCompanions.value)
      companions.value.push(tempCompanions.value)
    }
    tempCompanions.value ="";
  }
}

const removeCompanion = (element) => {
  companions.value = companions.value.filter ((e) =>{
    return element !== e;
  })
}

const removeSpot = (element) => {
  spots.value = spots.value.filter ((e) =>{
    return element !== e;
  })
}
</script>
