/*
 * @Author: Shen Xianhui 
 * @Date: 2019-01-26 22:55:24 
 * @Last Modified by: ShenXianhui
 * @Last Modified time: 2019-01-29 14:05:40
 */
<!-- 主页 -->
<template>
    <div class="main">
        <router-view></router-view>
        <Tabbar></Tabbar>
    </div>
</template>

<script>
import Tabbar from '@/components/Tabbar';

export default {
    name: 'Main',
    components: {
        Tabbar
    }
}
</script>

<style scoped lang='less'>
.main {
    width: 100%;
    height: 100%;
    padding-bottom: 0.5rem;
}
</style>