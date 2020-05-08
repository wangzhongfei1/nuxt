<template>
    <div>
        <ul class="fixed">
            <nuxt-link to="/film/nowplaying" tag="li" activeClass="myActive">正在热映</nuxt-link>
            <nuxt-link to="/film/comingsoon" tag="li" activeClass="myActive">即将上映</nuxt-link>
        </ul>
        <!-- 二级路由占位符 -->
         <nuxt-child></nuxt-child>
    </div>
</template>

<style lang="scss" scoped>
ul {
    display: flex;
    margin-bottom: 10px;
    li {
        flex: 1;
        height: 40px;
        text-align: center;
        line-height: 40px;
        background-color: white;
        list-style: none;
    }
}
.myActive {
    color: red;
    border-bottom: 2px solid red;
}
.fixed {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 40px;
    background-color: white;
}
</style>