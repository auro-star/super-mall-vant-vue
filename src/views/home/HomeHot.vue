/*
 * @Author: Shen Xianhui 
 * @Date: 2019-01-27 17:54:56 
 * @Last Modified by: ShenXianhui
 * @Last Modified time: 2019-02-21 16:54:15
 */
<!-- 首页-热卖 -->
<template>
    <div class="home-hot">
        <!-- 下拉刷新 -->
        <van-pull-refresh v-model="isLoading" @refresh="onRefresh">
            <!-- 轮播图 -->
            <div class="banner">
                <van-swipe :autoplay="4000" indicator-color="white">
                    <van-swipe-item v-for="item in banners" :key="item.id">
                        <img :src="setImg(item.imgSrc)" alt="轮播图" @click="getDetails(item)">
                    </van-swipe-item>
                </van-swipe>
            </div>
            <!-- 商品分类 -->
            <div class="tabs">
                <div class="tab" @click="getList()">
                    <img src="@/images/common/tab_1.png" alt="icon">
                    <p>热卖商品</p>
                </div>
                <div class="tab" @click="getList()">
                    <img src="@/images/common/tab_2.png" alt="icon">
                    <p>小米闪购</p>
                </div>
                <div class="tab" @click="getList()">
                    <img src="@/images/common/tab_3.png" alt="icon">
                    <p>以旧换新</p>
                </div>
                <div class="tab" @click="getList()">
                    <img src="@/images/common/tab_4.png" alt="icon">
                    <p>1分拼团</p>
                </div>
                <div class="tab" @click="getList()">
                    <img src="@/images/common/tab_5.png" alt="icon">
                    <p>超值特卖</p>
                </div>
                <div class="tab" @click="getList()">
                    <img src="@/images/common/tab_6.png" alt="icon">
                    <p>真心想要</p>
                </div>
                <div class="tab" @click="getList()">
                    <img src="@/images/common/tab_7.png" alt="icon">
                    <p>每日甄选</p>
                </div>
                <div class="tab" @click="getList()">
                    <img src="@/images/common/tab_8.png" alt="icon">
                    <p>电视特卖</p>
                </div>
                <div class="tab" @click="getList()">
                    <img src="@/images/common/tab_9.png" alt="icon">
                    <p>游戏配件</p>
                </div>
                <div class="tab" @click="getList()">
                    <img src="@/images/common/tab_10.png" alt="icon">
                    <p>更多商品</p>
                </div>
            </div>
            <!-- 优惠专区 -->
            <div class="preferential">
                <h2>特价专区</h2>
                <div class="preferential-content">
                    <div class="content-left">
                        <img src="@/images/common/mi_electric_cooker_4L.png" alt="商品">
                    </div>
                    <div class="content-right">
                        <div class="content-top">
                            <img src="@/images/common/mi_electric_cooker.png" alt="商品">
                        </div>
                        <div class="content-bottom">
                            <img src="@/images/common/mi_loudspeaker_box.png" alt="商品">
                        </div>
                    </div>
                </div>
            </div>
        </van-pull-refresh>
    </div>
</template>

<script>
import { mapMutations } from 'vuex';

export default {
    name: 'HomeHot',
    components: {},
    props: {},
    data() {
        return {
            isLoading: false, // 下拉刷新

            banners: [ // 轮播图
                {
                    select: true,
                    label: '热卖',
                    name: '小米8 青春版',
                    specifications: '潮流镜面渐变色, 2400万像素',
                    currentPrice: 1399,
                    costPrice: 1599,
                    imgSrc: 'images/common/banner_1.png'
                },
                {
                    select: true,
                    label: '热卖',
                    name: '红米6 AI双摄',
                    specifications: '小屏高性能',
                    currentPrice: 899,
                    costPrice: 999,
                    imgSrc: 'images/common/banner_2.png'
                },
                {
                    select: true,
                    label: '热卖',
                    name: '小米手环3 NFC版',
                    specifications: '能刷公交车、地铁',
                    currentPrice: 199,
                    costPrice: 299,
                    imgSrc: 'images/common/banner_3.png'
                }
            ]
        };
    },
    computed: {},
    watch: {},
    created() {},
    methods: {
        ...mapMutations([
            'setGoods' // 商品信息
        ]),

        // 下拉刷新
        onRefresh() {
            setTimeout(() => {
                this.$toast('刷新成功');
                this.isLoading = false;
            }, 500);
        },

        // 商品列表导航
        getList() {
            this.$router.push('/categories');
        },

        // 获取商品详情
        getDetails(data) {
            this.setGoods(data);
            this.$router.push('/goods');
        },

        // 设置图片地址
        setImg(v) {
            return require('../../' + v);
        }
    }
};
</script>

<style scoped lang='less'>
.home-hot {
    width: 100%;
    height: 100%;
    background-color: #fff;
    /deep/ .van-pull-refresh {
        overflow: auto;
    }
    .banner {
        margin-top: 0.1rem;
        padding: 0 0.1rem;
        /deep/ .van-swipe {
            width: 100%;
            height: 1.5rem;
            border-radius: 0.06rem;
            box-shadow: 2px 2px 15px 0px rgba(120, 120, 120, 0.3);
            img {
                width: 100%;
                height: 100%;
            }
        }
    }
    .tabs {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;

        width: 100%;
        margin-top: 0.3rem;
        padding: 0 0.1rem;
        .tab {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;

            width: 20%;
            &:nth-child(n + 6) {
                margin-top: 0.2rem;
            }
            img {
                width: 0.4rem;
            }
            p {
                color: #999;
                font-size: 0.12rem;
                margin-top: 0.05rem;
            }
        }
    }
    .preferential {
        width: 100%;
        margin-top: 0.2rem;
        padding: 0 0.1rem;
        h2 {
            font-size: 0.18rem;
            color: #333;
        }
        .preferential-content {
            display: flex;
            justify-content: space-between;

            width: 100%;
            margin-top: 0.1rem;
            padding-bottom: 0.2rem;
            .content-left {
                width: 1.75rem;
                height: 2.64rem;
                img {
                    width: 100%;
                    height: 100%;
                    border-radius: 0.04rem;
                    box-shadow: 2px 2px 15px 0px rgba(120, 120, 120, 0.3);
                }
            }
            .content-right {
                display: flex;
                flex-direction: column;
                justify-content: space-between;

                width: 1.75rem;
                div {
                    width: 100%;
                    height: 1.3rem;
                    img {
                        width: 100%;
                        height: 100%;
                        border-radius: 0.04rem;
                        box-shadow: 2px 2px 15px 0px rgba(120, 120, 120, 0.3);
                    }
                }
            }
        }
    }
}
.home-hot::-webkit-scrollbar { /* 隐藏滚动条, 这种方式不兼容 火狐 和 IE */
    display: none;
}
</style>
