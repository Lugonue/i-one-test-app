<template>
        <div class="nav-top">
        <button class="nav-btn-second">{{'<|'}}</button>
        <button class="nav-btn">{{ '<' }}</button>
        <button class="nav-btn-random">{{'Random'.toLocaleUpperCase()}}</button>
        <button class="nav-btn">{{ '>' }}</button>
        <button class="nav-btn-second">{{ '|>' }}</button>
      </div>
</template>
<script>
export default {

}
</script>
<style scoped lang="scss">

.nav-top {

    height: 65px;
    width: 780px;
    display: flex;
    justify-content: space-between;

    * {
        border: none;
        color: white;
        font-size: 0.7rem;
    }

    .nav-btn {
        border-radius: 50%;
        height: 65px;
        width: 65px;
        background-color: #F26A15;
    }

    .nav-btn-second {
        height: 65px;
        width: 80px;
        background-color: #0A2037;
    }

    .nav-btn-random {
        width: 320px;
        height: 65px;
        background-color: #F26A15;
    }
}
</style>