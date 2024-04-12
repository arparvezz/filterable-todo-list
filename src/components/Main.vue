<script setup>
import { reactive, ref } from 'vue';
const taskList = reactive([
  {
    title: "Drink More Water",
    condition: true
  },
  {
    title: "Take A Break!",
    condition: false
  },
  {
    title: "Go for a walk.",
    condition: false
  }
])

let popupOpen = ref(true)
</script>
<template>
  <div class="container mx-auto grid place-items-center">

    <div class="p-4 rounded border border-slate-500 mt-20">

      <!-- Task Input Box -->
      <div class="space-x-1 my-2">
        <input class="px-2 py-2 rounded focus:outline-none" type="text" name="newTask" id="newTask"
          placeholder="Drink Water...">
        <button class="px-3 py-2 rounded bg-green-300 text-green-800">Add New Task</button>
      </div>

      <!-- Task List Section -->
      <div class="space-y-2 my-2">

        <div v-for="(task, index) in taskList" :key="index"
          class="p-2 rounded bg-white flex justify-between items-center">
          <!-- Single message section -->
          <div class="flex items-center space-x-1">
            <input type="checkbox" name="condition" :id="index" v-model="task.condition">
            <label :for="index">{{ task.title }}</label>
          </div>
          <!-- Single - edit / delete section -->
          <div class="space-x-2 flex items-center">
            <button @click="popupOpen.value == !popupOpen.value"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24" color="#0000FF"
                fill="none">
                <path
                  d="M16.2141 4.98239L17.6158 3.58063C18.39 2.80646 19.6452 2.80646 20.4194 3.58063C21.1935 4.3548 21.1935 5.60998 20.4194 6.38415L19.0176 7.78591M16.2141 4.98239L10.9802 10.2163C9.93493 11.2616 9.41226 11.7842 9.05637 12.4211C8.70047 13.058 8.3424 14.5619 8 16C9.43809 15.6576 10.942 15.2995 11.5789 14.9436C12.2158 14.5877 12.7384 14.0651 13.7837 13.0198L19.0176 7.78591M16.2141 4.98239L19.0176 7.78591"
                  stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
                <path
                  d="M21 12C21 16.2426 21 18.364 19.682 19.682C18.364 21 16.2426 21 12 21C7.75736 21 5.63604 21 4.31802 19.682C3 18.364 3 16.2426 3 12C3 7.75736 3 5.63604 4.31802 4.31802C5.63604 3 7.75736 3 12 3"
                  stroke="currentColor" stroke-width="1.5" stroke-linecap="round" />
              </svg></button>
            <button><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24" color="#FF0000"
                fill="none">
                <path
                  d="M19.5 5.5L18.8803 15.5251C18.7219 18.0864 18.6428 19.3671 18.0008 20.2879C17.6833 20.7431 17.2747 21.1273 16.8007 21.416C15.8421 22 14.559 22 11.9927 22C9.42312 22 8.1383 22 7.17905 21.4149C6.7048 21.1257 6.296 20.7408 5.97868 20.2848C5.33688 19.3626 5.25945 18.0801 5.10461 15.5152L4.5 5.5"
                  stroke="currentColor" stroke-width="1.5" stroke-linecap="round" />
                <path
                  d="M3 5.5H21M16.0557 5.5L15.3731 4.09173C14.9196 3.15626 14.6928 2.68852 14.3017 2.39681C14.215 2.3321 14.1231 2.27454 14.027 2.2247C13.5939 2 13.0741 2 12.0345 2C10.9688 2 10.436 2 9.99568 2.23412C9.8981 2.28601 9.80498 2.3459 9.71729 2.41317C9.32164 2.7167 9.10063 3.20155 8.65861 4.17126L8.05292 5.5"
                  stroke="currentColor" stroke-width="1.5" stroke-linecap="round" />
                <path d="M9.5 16.5L9.5 10.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" />
                <path d="M14.5 16.5L14.5 10.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" />
              </svg></button>
          </div>
        </div>
      </div>

      <!-- Task Filter Section -->
      <div class="bg-white p-2 rounded ">
        <h3>Filter Tasks</h3>
        <div class="flex items-center space-x-2">
          <div class="flex items-center space-x-1">
            <input type="radio" name="filter-type" id="done">
            <label for="done">Done</label>
          </div>
          <div class="flex items-center space-x-1">
            <input type="radio" name="filter-type" id="processing">
            <label for="processing">Processing</label>
          </div>
          <div class="flex items-center space-x-1">
            <input type="radio" name="filter-type" id="willdo">
            <label for="willdo">Will do</label>
          </div>
        </div>
      </div>

    </div>

    <!-- Pop Up Section -->
    <Transition>
    <div v-show="popupOpen.value" class="p-2 rounded border border-slate-300 space-y-1">
      <input class="px-2 py-2 rounded focus:outline-none" type="text" name="editTask" id="editTask"><br>
      <div class="space-x-1">
        <button class="px-3 py-2 rounded bg-green-300 text-green-800">Add New Task</button>
        <button class="px-3 py-2 rounded bg-red-300 text-red-800">Cancel</button>
      </div>
    </div>
  </Transition>

  </div>




</template>
<style>
/* we will explain what these classes do next! */
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}</style>
