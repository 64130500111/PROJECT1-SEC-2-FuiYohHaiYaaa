<script setup>
import IcOutlineHome from "./components/icons/IcOutlineHome.vue";
</script>

<template>
  <div id="main">
    <div id="secondary" class="flex flex-row">
      <!-- menu -->
      <div id="menu" class="flex flex-col border border-red-500">
        <div id="profile" class="border border-blue-300 mt-10">
          <img id="Pic" src="./assets/Dr.rash.jpg" alt="profilePic" />
          <h1 id="name" class="text-center text-sm">Dr. Marcus Rashford</h1>
        </div>
        <div id="home" class="border border-green-400 mt-5">
          <div id="home2" class="flex flex-row">
            <IcOutlineHome id="homeIcon" />
            <div class="text-base ml-5">Home</div>
          </div>
        </div>
      </div>
      <!-- order -->
      <div id="order" class="flex flex-row border border-r-purple-500">
        <div id="selection" class="flex flex-col">
          <div id="type" class="border border-black"></div>
          <div id="item" class="border border-black"></div>
        </div>
        <div id="article" class="border border-black"></div>
      </div>
    </div>
  </div>
</template>

<style scoped>
#main {
  position: absolute;
  width: 100%;
  height: 100%;

  /* background: conic-gradient(
    from 260.41deg at 69.86% 79.2%,
    #ffffff 0deg,
    #f76e21 120deg,
    #f76e21 240deg,
    #ffffff 360deg
  ); */
}

#secondary {
  /* 1336/1440 910/1024 */
  position: absolute;
  width: 92.78%;
  height: 88.87%;
  margin: 3em;

  /* background: conic-gradient(
    from 270deg at 102.36% 100%,
    #ffffff 0deg,
    #cbcbcb 90deg,
    #cfcdcd 180deg,
    #fffbfa 270deg,
    #fdebdd 360deg
  ); */
  /* opacity: 0.55; */
  border-radius: 59px;
}

#menu {
  /* 256/1336 910/910 */
  width: 20%;
  height: 100%;
}

#Pic {
  width: 50px;
  height: 50px;

  margin: auto;
}

#home2 {
  margin-left: 97px;
}
#order {
  /* 1047/1336 825/910 */
  width:78.3%;
  height: 90.7%;
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


</style>
