<template>
  <div v-if="store.loading || store.scanComplete" class="fixed inset-0 z-50 flex items-center justify-center bg-black/50 backdrop-blur-sm">
    <div class="bg-gray-800 rounded-xl shadow-2xl p-8 max-w-sm w-full mx-4 border border-gray-700 transform transition-all">
      
      <!-- Loading State -->
      <div v-if="store.loading" class="text-center">
        <div class="relative w-16 h-16 mx-auto mb-4">
          <div class="absolute inset-0 border-4 border-indigo-500/30 rounded-full"></div>
          <div class="absolute inset-0 border-4 border-indigo-500 rounded-full border-t-transparent animate-spin"></div>
        </div>
        <h3 class="text-xl font-semibold text-white mb-2">Scanning Library</h3>
        <p class="text-gray-400">Reading metadata from files...</p>
      </div>

      <!-- Complete State -->
      <div v-else-if="store.scanComplete" class="text-center">
        <div class="w-16 h-16 mx-auto mb-4 bg-green-500/20 rounded-full flex items-center justify-center">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-green-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7" />
          </svg>
        </div>
        <h3 class="text-xl font-semibold text-white mb-2">Scan Complete</h3>
        <div class="bg-gray-700/50 rounded-lg p-4 mb-6">
          <div class="flex justify-between items-center mb-2">
            <span class="text-gray-400">Tracks Found</span>
            <span class="text-white font-medium">{{ store.scanCount }}</span>
          </div>
          <div class="flex justify-between items-center">
            <span class="text-gray-400">Time Taken</span>
            <span class="text-white font-medium">{{ store.scanDuration }}s</span>
          </div>
        </div>
        <button 
          @click="store.closePopup()"
          class="w-full bg-indigo-600 hover:bg-indigo-700 text-white font-medium py-2 px-4 rounded-lg transition-colors focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2 focus:ring-offset-gray-800"
        >
          Done
        </button>
      </div>

    </div>
  </div>
</template>

<script setup>
import { store } from '../store';
</script>
