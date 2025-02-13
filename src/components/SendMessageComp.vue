<template>
    <a-row>
        <a-col :span="21">
            <a-input 
                v-model:value="inputValue"
                placeholder="please input the message"
                @keyup.enter="handleSend"
                ></a-input>
        </a-col>
        <a-col :span="3">
            <a-button 
                type="primary" 
                @click="handleSend" 
                style="width:100%;padding:2px">
                send
            </a-button>
        </a-col>
    </a-row>
</template>

<script setup>
import { ref,defineEmits } from "vue";

const emits = defineEmits(['send']);
const inputValue = ref("");
const handleSend = () => {
    emits("send", inputValue.value);
    inputValue.value = "";
};
</script>

<style>
</style>