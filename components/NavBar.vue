<script>
export default {
    methods: {
        submit() {
            this.$emit('getContent');
        }
    }
}


</script>
<template>
  <div class="nav-top">
    <button class="nav-btn-second" @click="$emit('getContent', 'toStart')">{{ "|<" }}</button>
    <button class="nav-btn" @click="$emit('getContent', 'previous')">{{ "<" }}</button>
    <button class="nav-btn-random" @click="$emit('getContent', 'randomContent')">{{ "Random".toUpperCase() }}</button>
    <button class="nav-btn" @click="$emit('getContent', 'next')">{{ ">" }}</button>
    <button class="nav-btn-second" @click="$emit('getContent', 'toEnd')">{{ ">|" }}</button>
  </div>
</template>

<style scoped lang="scss">
@keyframes hover-btn {
  from {
    background-color: #a3501d;
  }
  to {
    background-color: #0a2037;
  }
}

.nav-top {
  height: 65px;
  width: 780px;
  display: flex;
  justify-content: space-between;

  * {
    border: none;
    color: white;
    font-size: 0.9rem;
    cursor: pointer;
  }

  .nav-btn {
    border-radius: 50%;
    height: 65px;
    width: 65px;
    background-color: #f26a15;
    &:hover {
      animation: hover-btn;
      animation-duration: 1000ms;
      animation-fill-mode: forwards;
    }
  }

  .nav-btn-second {
    height: 65px;
    width: 80px;
    background-color: #0a2037;
    &:hover {
      background-color: #f26a15;
    }
  }

  .nav-btn-random {
    width: 320px;
    height: 65px;
    background-color: #f26a15;
    &:hover {
      background-color: white;
      color: #f26a15;
    }
  }
}
</style>
