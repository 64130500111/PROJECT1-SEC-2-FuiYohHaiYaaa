<script setup></script>

<template>
  <div id="main" class="w-screen h-screen">
    <div id="secondary" class="flex flex-row">
      <div id="menu1" class="flex flex-col">
        <div id="profilePic" class="">

        </div>
    
      </div>
      <div id="menu2"></div>
    </div>
  </div>
</template>

<style scoped>
#main {
    /* width: 1440px
       height: 1024px*/

  position: relative;

  background: conic-gradient(
    from 260.41deg at 69.86% 79.2%,
    #ffffff 0deg,
    #f76e21 120deg,
    #f76e21 240deg,
    #ffffff 360deg
  );
}

#secondary {
  position: absolute;
  /* width 1336/1440 height 910/1024 */
  width: 92.8%; 
  height: 88.9%;
  left: 58px;
  top: 61px;

  opacity: 0.55;
  border-radius: 59px;

  background: conic-gradient(
    from 270deg at 102.36% 100%,
    #ffffff 0deg,
    #cbcbcb 90deg,
    #cfcdcd 180deg,
    #fffbfa 270deg,
    #fdebdd 360deg
  );
}
#menu1 {
  position: absolute;
  /* width 256/1336 height 910/910*/
  width: 19.17%;
  height: 100%;
}

#menu2 {
  position: absolute;
  /* width 1047/1336 height 828/910 */
  width: 78.4%;
  height: 91%;
  left: 250px;
  top: 50px;

  background: #ffffff;
  border-radius: 59px;
}

#profilePic {
    position: absolute;
    /* width 77/256 height 82/910 */
    /* width: 30.07%; */
    height: 8% ;
    /* left 81/256 top 100/910 */
    left: 31.64%;
    top: 10.99%;
    
    background: url(GettyImages-1358257346.jpg);

}
</style>
