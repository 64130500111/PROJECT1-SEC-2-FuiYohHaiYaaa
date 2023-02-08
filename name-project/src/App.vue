<script setup>
import { ref } from "vue";
import IcOutlineHome from "./assets/icons/IcOutlineHome.vue";
import MaterialSymbolsSearchRounded from "./assets/icons/MaterialSymbolsSearchRounded.vue";
import category from "./data/items.json";

const isActive = (input) => {
  return (refNum.value = input);
};

const refNum = ref(0);
</script>

<template>
  <div id="main" class="w-full h-[100vh] pl-[50px] flex justify-center ">
    <div
      id="secondary"
      class="flex flex-row w-[1336px] h-[790px] rounded-[59px] "
    >
      <!-- menu -->
      <div
        id="menu"
        class="flex flex-col w-[20%] h-[100%]  "
      >
        <div id="profile" class="flex flex-col mt-10">
          <img id="profilepic" src="" alt="profilePic" class=""/>
          <h1 id="name" class="text-center text-xl font-['Baloo'] ">Dr. Marcus Rashford</h1>
        </div>
        <div id="home" class="flex justify-center mt-[50px] font-['Baloo'] cursor-pointer">
          <div id="home2" class="flex flex-row">
            <div class="w-[61px] h-[57px] bg-white  rounded-[20px] shadow-lg relative pt-[10px] ">
              <IcOutlineHome id="homeIcon"/>
            </div>
            <p class="text-2xl m-auto ml-5">Home</p>
          </div>
        </div>
      </div>
      <!-- order -->
      <div
        id="order"
        class="flex flex-row w-[80%] h-[91%] bg-white rounded-[59px] mt-10 mr-6"
      >
        <div id="selection" class="flex flex-col w-[65.14%] h-[100%]">
          <div id="type" class="flex flex-col w-[100%] h-[50%]">
            <div class="flex flex-row justify-between h-[50%]">
              <!-- selection top -->
              <div class="mt-[50px] ml-[50px]">
                <p class="font-['Baloo'] text-[48px]">Welcome to Hello</p>
              </div>
              <div class="w-[61px] h-[57px] bg-gray-200 rounded-[20px] shadow-lg mt-[55px]">
                <button class="ml-[15px] mt-[12px]">
                  <MaterialSymbolsSearchRounded />
                </button>
              </div>
            </div>
            <!-- selection bottom -->
            <ul class="flex flex-row ml-[50px] gap-3 h-[50%]">
              <li
                v-for="({ type, iconURL }, index) in category"
                :key="index"
                class="target w-[89px] h-[130px] rounded-[59px] bg-white text-black shadow-xl font-['?????'] cursor-pointer"
                @click="isActive(index)"
                :class="refNum === index ? 'bg-black' : 'bg-white'"
              >
                <div class="text-center mt-[20px]">
                  <img :src="iconURL" class="ml-[10px]" />
                  <p :class="refNum === index ? 'text-white' : 'text-black'">
                    {{ type }}
                  </p>
                </div>
              </li>
            </ul>
          </div>
          <div id="item" class="w-[100%] h-[50%] flex flex-col">
            <div class="flex flex-row">
              <p>All Items</p>
              <div>Icon</div>
            </div>
            <div class="grid grid-cols-3">
              <div v-for="(list, index) in category" :key="index">
                
              </div>

            </div>
          </div>
        </div>
        <div id="article" class="w-[35%] h-[100%]"></div>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import url(https://fonts.googleapis.com/css2?family=Baloo:wght@400);
@import url(https://fonts.googleapis.com/css2?family=?????:wght@400);

#main {
  /* background-image: url(./assets/MainBG.png); */

  background: conic-gradient(
    from 260.41deg at 69.86% 79.2%,
    #ffffff 0deg,
    #f76e21 120deg,
    #f76e21 240deg,
    #ffffff 360deg
  );
}

#secondary {
  background: conic-gradient(
    from 270deg at 102.36% 100%,
    rgba(255, 255, 255, 0.5) 0deg,
    rgba(203, 203, 203, 0.5) 90deg,
    rgba(207, 205, 205, 0.5) 180deg,
    rgba(255, 251, 250, 0.5) 270deg,
    rgba(253, 235, 221, 0.5) 360deg
  );
}

#menu {
    /* border-color: red; */
}

#order {
  /* border-color: purple; */
  
}

#profile {

}

#profilepic {
  width: 50px;
  height: 50px;
  margin: auto;
}

#home {

}

#selection {

}

#article {

}

#type {

}

#item {
 
}

</style>
