<template>
    <a-row>
        <a-col span="20" style="padding:5px" :offset="2">
            <a-flex justify="flex-end">
                <div class="messageCard">{{ props.message }}</div>
            </a-flex>
        </a-col> 
        <a-col span="2">
            <img src="/src/assets/avatar_me.jpg" width="100%"  style="padding:3px" alt="avatar"/>
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
    background: rgb(154, 224, 154);
    border-radius: 10px;
    line-height: 34px;
    font-size:12px;
    padding-left:8px;
    padding-right: 8px;
}
</style>
