<script setup>
import { ref, computed } from "vue";
import IcOutlineHome from "./assets/icons/IcOutlineHome.vue";
import MaterialSymbolsSearchRounded from "./assets/icons/MaterialSymbolsSearchRounded.vue";
import CarbonInformation from "./assets/icons/CarbonInformation.vue";
import category from "./data/items.json";

const typeNum = ref(0);

let menuArr = category[0].menu; //default

const search = ref(false);

const userKeywords = ref("");

let filterFood = category[0].menu; //default

const isActive = (index = 0) => {
  // filter type
  typeNum.value = index;

  // get array of food
  menuArr = category[index].menu.sort((a, b) => a.name.localeCompare(b.name));

  // array with computed function
  filterFood = computed(() => {
    return menuArr.filter((arr) =>
      arr.name.toLowerCase().includes(userKeywords.value.toLowerCase())
    );
  });
};

const cartItem = ref([]);

const totalAmount = computed(() => {
  return cartItem.value.reduce((total, currentValue) => total + currentValue.price, 0)
})

</script>

<template>
  <div id="main" class="w-full h-[100vh] pl-[50px] flex justify-center">
    <div id="secondary" class="flex flex-row w-[1336px] h-[790px] rounded-[59px] text-black">
      <!-- menu -->
      <div id="menu" class="flex flex-col w-[20%] h-[100%]">
        <div id="profile" class="flex flex-col mt-[80px]">
          <img id="profilepic" src="./assets/Dr.rash.jpg" alt="profilePic" class="rounded-lg" />
          <h1 id="name" class="text-center text-xl font-['Baloo'] mt-3">
            Dr. Marcus Rashford
          </h1>
        </div>
        <div id="home" class="flex justify-center mt-[50px] font-['Baloo'] cursor-pointer">
          <div id="home2" class="flex flex-row">
            <div class="w-[61px] h-[57px] bg-white rounded-[20px] shadow-lg relative pt-[10px]">
              <IcOutlineHome id="homeIcon" />
            </div>
            <p class="text-2xl m-auto ml-5">Home</p>
          </div>
        </div>
      </div>
      <!-- order -->
    <div id="order" class="flex flex-row w-[80%] h-[91%] bg-white rounded-[59px] mt-10 mr-6">
      <div id="selection" class="flex flex-col w-[65.14%] h-[100%]">
          <div id="type" class="flex flex-col w-[100%] h-[50%]">
            <div class="flex flex-row justify-between h-[50%]">
              <!-- selection top -->
              <div class="mt-[50px] ml-[50px]">
                <p class="font-['Baloo'] text-[48px]">Welcome to Eatland</p>
              </div>
            </div>
            <!-- selection bottom -->
            <ul class="flex flex-row ml-[50px] gap-3 h-[50%]">
              <li v-for="({ type, iconURL }, index) in category" :key="index"
                class="target w-[89px] h-[130px] rounded-[59px] bg-white text-black shadow-xl font-['?????'] cursor-pointer"
                @click="isActive(index)" :class="typeNum === index ? 'bg-black' : 'bg-white'">
                <div class="text-center mt-[20px]">
                  <img :src="iconURL" class="ml-[10px]" />
                  <p :class="typeNum === index ? 'text-white' : 'text-black'">
                    {{ type }}
                  </p>
                </div>
              </li>
            </ul>
          </div>
          <div id="item" class="w-[100%] h-[50%] flex flex-col">
            <div class="flex flex-row h-[20%]">
              <div class="w-full flex justify-center">
                <p class="font-['Baloo'] text-[48px]">Menus</p>
              </div>
              <div class="w-full flex justify-end">
                <div class="w-[45px] h-[45px] flex flex-row mt-3 bg-gray-200 rounded-xl shadow-lg">
                  <button @click="search = !search" class="mt-[5px] ml-[10px]">
                    <MaterialSymbolsSearchRounded />
                  </button>
                </div>
                <input @input="isActive(typeNum)" v-show="search" v-model.trim="userKeywords" type="text"
                  placeholder="Type keyword..."
                  class="w-[10em] h-8 rounded-md ml-3 mt-5 p-2 bg-white border border-gray-500" />
              </div>

              <!-- <div class="w-full flex justify-end">
                  <div>Icon see all</div>
                </div> -->
            </div>
            <!-- Grid -->
            <div class="grid grid-cols-3 justify-items-center gap-y-4 overflow-scroll">
              <div v-for="(menu, index) in filterFood" :key="index"
                class="w-[180px] h-[237px] rounded-[31px] bg-white shadow-lg flex flex-col">
                <div class="flex justify-center">
                  <img :src="menu.picURL" class="w-[120px] h-[120px] rounded-[30px]" />
                </div>
                <div class="flex flex-row justify-center">
                  <p class="font-['Baloo'] text-[0.9em] text-center mt-3">
                    {{ menu.name }}
                  </p>
                  <!-- information modal -->
                  <a :href="`#${index}`" class="mt-[13px] ml-2">
                    <CarbonInformation />
                  </a>
                  <div class="modal" :id="index">
                    <div class="modal-box">
                      <h3 class="font-bold text-lg">
                        Congratulations random Internet user!
                      </h3>
                      <p class="py-4">
                        You've been selected for a chance to get one year of
                        subscription to use Wikipedia for free!
                      </p>
                      <div class="modal-action">
                        <a href="#" class="btn">Yay!</a>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="flex flex-row">
                  <div class="w-full flex justify-center mt-7">
                    <p class="font-['Baloo'] text-lg">{{ menu.price }}฿</p>
                  </div>
                  <div class="w-full">
                    <input type="checkbox" :id="menu" :value="menu" v-model="cartItem"
                      class="checkbox checkbox-success checkbox-md ml-8 mt-7" />
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div id="article" class="w-[35%] h-[100%] flex flex-col">
          <div class="flex justify-center mt-[50px]">
            <h3 class="font-['Baloo'] text-[48px]">Your Cart</h3>
          </div>
          <div class="w-full ml-[20px] font-['?????']">
            <table class="w-full">
              <thead>
                <tr class="text-left">
                  <th class="w-[45%]">Menu</th>
                  <th class="w-[20%]">Price</th>
                  <th class="w-[35%] pl-[15px]">Quantity</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(item, index) in cartItem ">
                  <td>{{ item.name }}</td>
                  <td>{{ item.price }}฿</td>
                  <td class="pl-[15px]">
                    <button class="btn btn-xs btn-circle btn-ghost btn-active">-</button>
                    1
                    <button class="btn btn-xs btn-circle btn-ghost btn-active">+</button>
                  </td>
                </tr>
                <tr class="text-left">
                  <th>Total Amount:</th>
                  <th>{{ totalAmount }} Baht</th>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import url(https://fonts.googleapis.com/css2?family=Baloo:wght@400);
@import url(https://fonts.googleapis.com/css2?family=?????:wght@400);

#main {
  background: conic-gradient(from 260.41deg at 69.86% 79.2%,
      #ffffff 0deg,
      #f76e21 120deg,
      #f76e21 240deg,
      #ffffff 360deg);
}

#secondary {
  background: conic-gradient(from 270deg at 102.36% 100%,
      rgba(255, 255, 255, 0.5) 0deg,
      rgba(203, 203, 203, 0.5) 90deg,
      rgba(207, 205, 205, 0.5) 180deg,
      rgba(255, 251, 250, 0.5) 270deg,
      rgba(253, 235, 221, 0.5) 360deg);
}

#profilepic {
  width: 50px;
  height: 50px;
  margin: auto;
}
</style>
