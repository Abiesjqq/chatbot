<template>
    <a-row>
        <a-col span="2">
            <img src="/src/assets/avatar.jpg" width="100%"  style="padding:3px" alt="avatar"/>
        </a-col>
        <a-col span="20" style="padding:5px">
            <div class="messageCard">{{ props.message }}</div>
        </a-col> 
    </a-row>
</template>

<script setup>
const props=defineProps(['message']);
</script>

<style scoped>
.messageCard {
    width:fit-content;
    height:100%;
    background: white;
    border-radius: 10px;
    line-height: 34px;
    font-size:12px;
    padding-left:8px;
    padding-right: 8px;
}
</style>
