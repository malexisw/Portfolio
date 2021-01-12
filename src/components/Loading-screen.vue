<template>
    <div class="loading-screen">
        <div class="circle one"></div>
        <div class="circle two"></div>
        <div class="circle three"></div>
    </div>
</template>

<script>
export default {
    
}
</script>

<style scoped>
.loading-screen{
    position: absolute;
    
    width: 100%;
    height: 100vh;

    display: flex;
    justify-content: center;
    align-items: center;

    background: #221f1f;

    z-index: 100;
}

.circle{
    height: 25px;
    width: 25px;

    border-radius: 50%;

    background: #534e4e;

    margin-left: 30px;

    animation: load 1.5s linear infinite;
}

.two{
    animation-delay: .2s;
}

.three{
    animation-delay: .4s;
}

@keyframes load {
    50%{
        width: 50px;
        height: 50px;
    }
    100%{
        width: 25px;
        height: 25px;
    }
}
</style>