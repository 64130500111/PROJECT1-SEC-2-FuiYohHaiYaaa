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
  <div id="main" class="w-full h-[60vw]">
    <div
      id="secondary"
      class="flex flex-row relative w-[1336px] h-[790px] top-[86px] left-[101px] border rounded-[59px]"
    >
      <!-- menu -->
      <div
        id="menu"
        class="flex flex-col w-[20%] h-[100%] border border-red-500"
      >
        <div id="profile" class="flex flex-col border border-blue-300 mt-10">
          <img id="Pic" src="./assets/Dr.rash.jpg" alt="profilePic" />
          <h1 id="name" class="text-center text-sm">Dr. Marcus Rashford</h1>
        </div>
        <div id="home" class="flex justify-center border border-green-400">
          <div id="home2" class="flex flex-row">
            <IcOutlineHome id="homeIcon" />
            <div class="text-base ml-5">Home</div>
          </div>
        </div>
      </div>
      <!-- order -->
      <div
        id="order"
        class="flex flex-row w-[80%] h-[91%] border border-r-purple-500 z-[20]"
      >
        <div id="selection" class="flex flex-col">
          <div id="type" class="flex flex-col border border-black">
            <div class="flex justify-between h-[50%]">
              <!-- selection top -->
              <div class="mt-[50px] ml-[50px]">
                <p class="font-['Baloo'] text-[48px]">Welcome to Hello</p>
              </div>
              <button class="mr-[50px]">
                <MaterialSymbolsSearchRounded />
              </button>
            </div>
            <!-- selection bottom -->
            <ul class="flex flex-row ml-[50px] gap-3 h-[50%]">
              <li
                v-for="({ type, iconURL }, index) in category"
                :key="index"
                class="target w-[89px] h-[130px] border rounded-[59px] bg-white text-black shadow-xl font-['?????'] cursor-pointer"
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
          <div id="item" class="border border-black">
            <div>
              <h1>Selection type</h1>
            </div>
          </div>
        </div>
        <div id="article" class="border border-black"></div>
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
  z-index: 3;
}

#order {
  z-index: 3;
}

#Pic {
  width: 50px;
  height: 50px;

  margin: auto;
}

#selection {
  /* 682/1047 825/825 */
  width: 65.14%;
  height: 100%;
}

#article {
  /* 365/1047 825/825 */
  width: 34.86%;
  height: 100%;
}

#type {
  width: 100%;
  height: 50%;
}

#item {
  widows: 100%;
  height: 50%;
}

/* :target {
  background-color: black;
  color: white;
} */
</style>
