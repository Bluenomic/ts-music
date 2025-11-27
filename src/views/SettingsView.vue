<template>
  <div class="p-6 max-w-2xl mx-auto">
    <h1 class="text-2xl font-bold text-white mb-6">Settings</h1>
    
    <div class="bg-gray-800 rounded-lg p-6 shadow-lg">
      <h2 class="text-xl font-semibold text-white mb-4">Performance</h2>
      
      <div class="space-y-4">
        <ToggleInt 
          v-model="store.useParallelism" 
          label="Use Parallel Processing (Faster)" 
        />
        
        <p class="text-sm text-gray-400 mt-2">
          When enabled, the application will use multiple CPU threads to scan and parse music files. 
          Disable this if you experience system instability or high CPU usage during scans.
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { store } from '../store';
import ToggleInt from '../components/settings/ToggleInt.vue';
</script>