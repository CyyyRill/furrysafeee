<template>
    <div class="font-semibold border-t text-sm rounded-b-lg">
        <button v-if="!showRescueCancelButtons && !showSuccessMessage && !showConfirmDialog" type="button"
            class="flex justify-center py-4 font-semibold w-full text-red-600 bg-slate-50 hover:bg-red-500 hover:text-white rounded-b-lg"
            @click="showRescueCancelButtons = true; confirmAction()">
            Take Action
        </button>

        <div v-else-if="showRescueCancelButtons || props.operation == 'ongoing'" class="flex justify-between font-semibold text-gray-600 rounded-b-lg">
            <button type="button" class="bg-green-100 py-4 w-full hover:bg-green-500 hover:text-white rounded-bl-lg"
            @click="handleAction('Rescued')">
            <h1 class="font-bold text-sm flex gap-3">{{ report.post_type }}</h1>
            </button>
        </div>

        </div>

</template>

<script setup>

import axios from 'axios';


const props = defineProps({
    postId: {
        type: Number,
        required: true
    },
    operation:{
        type: String,
        required: false
    }
});

const emit = defineEmits(['statusUpdated']);

const selectedAction = ref('');

const handleAction = (action) => {
    selectedAction.value = action;
};

</script>