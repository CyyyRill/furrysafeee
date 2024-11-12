<template>
    <div class="min-h-screen bg-white text-black">
        <!-- Mobile Header -->
        <header class="lg:hidden bg-white border p-4 flex items-center justify-between">
            <button class="text-gray-400 hover:text-white text-2xl">&larr;</button>
            <div class="flex items-center">
                <span class=" font-semibold">Furrysafe</span>
            </div>
            <button @click="toggleSidebar" class="text-gray-400 hover:text-white text-2xl">&#9776;</button>
        </header>

        <div class="flex flex-col lg:flex-row h-[calc(100vh-64px)] lg:h-screen">
            <!-- Sidebar -->
            <div :class="['w-full lg:w-80   p-4 overflow-y-auto', { 'hidden lg:block': !sidebarOpen }]">
                <!-- Search Bar -->
                <div class="relative mb-6">
                    <input type="text" placeholder="Search..."
                        class="w-full bg-white border-2 rounded-md py-2 pl-4 pr-10 focus:outline-none focus:ring-1 focus:ring-gray-700" />
                    <span class="absolute right-3 top-2.5 text-gray-500">&#128269;</span>
                </div>

                <!-- Filters -->
                <div class="flex flex-wrap items-center gap-2 mb-6">
                    <div class="text-sm text-gray-400 w-full lg:w-auto mb-2 lg:mb-0">Show me:</div>
                    <button class=" bg-white border-2  px-3 py-1.5 rounded-md text-sm flex items-center">Open Now <span
                            class="ml-1">&#9662;</span></button>
                    <button class=" bg-white border-2 px-3 py-1.5 rounded-md text-sm">Nearest</button>
                    <button class=" bg-white border-2  px-3 py-1.5 rounded-md text-sm flex items-center"><span
                            class="mr-1">&#9881;</span>Filters</button>
                </div>

                <!-- Store List -->
                <div class="space-y-4">
                    <div v-for="store in stores" :key="store.id" class="flex items-center justify-between group">
                        <div class="flex items-center">
                            <img :src="store.logo" :alt="store.name" class="w-8 h-8 rounded-full" />
                            <div class="ml-3">
                                <div class="font-medium">{{ store.name }}</div>
                                <div class="text-sm text-gray-400">{{ store.distance }} • Open 'til 6pm</div>
                            </div>
                        </div>
                        <button
                            class="text-gray-500 opacity-100 lg:opacity-0 lg:group-hover:opacity-100 transition-opacity">&#8942;</button>
                    </div>
                </div>
            </div>

            <!-- Map Area -->
            <div class=" flex-1 relative">
                <div class="w-full h-full bg-white flex items-center justify-center">


                    <iframe class="absolute rounded-[3rem]  border-4 border-black p-2 top-0 left-0 w-full h-full"
                        src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d12080.73732861526!2d-74.0059418!3d40.7127847!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zM40zMDA2JzEwLjAiTiA3NMKwMjUnMzcuNyJX!5e0!3m2!1sen!2sus!4v1648482801994!5m2!1sen!2sus"
                        frameborder="0" style="border:0;" allowfullscreen="" aria-hidden="false" tabindex="0">
                    </iframe>
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
    </div>
</template>

<script>
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