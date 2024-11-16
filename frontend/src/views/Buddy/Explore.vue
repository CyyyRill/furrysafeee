<template>


        <div class="flex flex-col p-4 lg:p-[3rem] lg:flex-row h-[calc(100vh-64px)] lg:h-screen ">
            
            <!-- Map Area -->
            <div class=" flex-1 relative">
                <div class="w-full h-full bg-white flex items-center justify-center">
                    <displayMap class=" rounded-2xl"
                        :shelterlat="stores.length > 0 ? stores[0].latitude : 0" 
                        :shelterlng="stores.length > 0 ? stores[0].longitude : 0" 
                        containerHeight="100%" 
                        containerWidth="100%" 
                        @location-changed="handleLocationChange" />
                </div>
                <!-- Store Details Popup -->
                <!-- <div
            class="absolute bottom-0 left-0 right-0 lg:top-1/2 lg:left-1/2 lg:bottom-auto lg:right-auto lg:transform lg:-translate-x-1/2 lg:-translate-y-1/2 bg-white rounded-t-lg lg:rounded-lg p-4 shadow-lg w-full lg:w-80">
            <div class="flex items-center mb-4">
              <img src="/placeholder.svg?height=40&width=40" alt="Adidas" class="w-10 h-10 rounded-full" />
              <div class="ml-3">
                <div class="font-medium">dolens</div>
                <div class="text-sm text-black">0.5 mi • Open 'til 6pm</div>
              </div>
            </div>
            <div class="font-medium mb-2">naa sa davao dapit </div>
            <p class="text-black text-sm mb-4">asfjaljkfhakehaweuily hfjkasdhflkahfklahdklf
              fjklahjklhefklfhwaelkfwauefeioyoiy</p>
            <button class="w-full bg-gray-800 text-white rounded-md py-2 hover:bg-gray-700 transition-colors">More
              Details</button>
          </div> -->
            </div>
        </div>
</template>

<script>
import displayMap from '@/components/buddy_Map.vue'

export default {
    name: 'ExploreView',
    // Your existing component logic
}
</script>

<script setup>
import { ref } from 'vue'

const sidebarOpen = ref(false)

const toggleSidebar = () => {
    sidebarOpen.value = !sidebarOpen.value
}

const stores = ref([
    {
        id: 1,
        name: 'Dolens',
        logo: '/placeholder.svg?height=32&width=32',
        distance: '0.5 mi'
    },
    {
        id: 2,
        name: 'imong mama',
        logo: '/placeholder.svg?height=32&width=32',
        distance: '0.7 mi'
    },
])
</script>