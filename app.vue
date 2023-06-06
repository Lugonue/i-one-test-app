<template>
  <!-- <ClientOnly> -->
  <div class="container">
    <div class="header">
      <h3>{{ "Test from i-one web agency".toLocaleUpperCase() }}</h3>
    </div>
    <div class="body">
      <Content />
    </div>
  </div>
  <!-- </ClientOnly> -->
</template>

<style scoped>

.container {
  height: 1623px;
  width: 1920px;
  display: flex;

  align-items: center;
  flex-direction: column;
  background-color: #0e2f51;
}

.body {
  height: 66%;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.header {
  position: relative;
  animation: animation;
  animation-duration: 2.5s;
  height: 508px;
  width: 100%;
  background-image: url("/image_1.png");
}

.header h3 {
  position: absolute;
  width: 755px;
  top: 50%;
  left: calc(50% - 755px / 2 + 0.5px);
  text-align: center;
  font-size: 44px;
  color: white;
}


@keyframes animation {
  from {
    transition: translateY(100%);
    transform: translateX(5%);
    opacity: 0;
  }

  to {
    transition: translateY(0%);
    transform: translateX(0%);
    opacity: 1;
  }
}
</style>
