<template>
  <div class="container">
    <HeaderComp></HeaderComp>
    <!--消息展示-->
    <div v-for="(item, index) in messageList" :key="index">
      <LeftMessageCompVue
        v-if="item.position == 'left'"
        :message="item.message"
      ></LeftMessageCompVue>
      <RightMessageCompVue
        v-if="item.position == 'right'"
        :message="item.message"
      ></RightMessageCompVue>
    </div>
    <!--发送消息-->
    <SendMessageCompVue
      style="position: absolute; bottom: 0px; width: 100%"
      @send="handleSend"
    ></SendMessageCompVue>
  </div>
</template>

<script setup>
import { message } from "ant-design-vue";
import { ref } from "vue";
import HeaderComp from "./components/HeaderComp.vue";
import LeftMessageCompVue from "./components/LeftMessageComp.vue";
import RightMessageCompVue from "./components/RightMessageComp.vue";
import SendMessageCompVue from "./components/SendMessageComp.vue";
import axios from "axios";

const messageList = ref([
  {
    position: "left",
    message: "Hihihi~",
  },
]);

const handleSend = async (value) => {
  messageList.value.push({
    position: "right",
    message: value,
  });
  //模拟回复
  // setTimeout(() => {
  //   messageList.value.push({
  //     position: "left",
  //     message: "服务器繁忙，请稍后再试。",
  //   });
  // }, 500);
  //向百度云发送请求
  const messages = messageList.value.map((item) => {
    return {
      role: item.position == "left" ? "assistant" : "user",
      content: item.message,
    };
  });

  const res = await axios.request({
    url: "https://aip.baidubce.com/rpc/2.0/ai_custom/v1/wenxinworkshop/chat/ernie-speed-128k?access_token=24.d369be7d5bcbee45f73cbb8072039690.2592000.1742034786.282335-117493444",
    method: "POST",
    data: {
      messages,
      system: "你是一只猫,说话搞怪抽象.",
    },
  });
  // console.log(res);

  messageList.value.push({
    position: "left",
    message: res.data.result,
  });
};
</script>

<style scoped>
.container {
  width: 50%;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  background: rgb(228, 227, 227);
  height: 100%;
}
</style>
