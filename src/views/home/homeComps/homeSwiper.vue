<template>
        <Swiper>
            <SwiperItem v-for="(item,index) in banners" :key="index">
                <a :href="item.link">
                    <img :src="item.image" @load="imgLoad">
                </a>
            </SwiperItem> 
        </Swiper>
</template>

<script>
import {Swiper, SwiperItem} from 'components/common/swiper/index'

export default {
    name: 'HomeSwiper',
    data() {
        return {
            isLoad: false
        }
    },
    components: {
        Swiper,
        SwiperItem
    },
    props: {
        banners: {
            type: Array,
            default: []
        }
    },
    methods: {
        imgLoad() {
            if (!this.isLoad) {
                this.$emit('swiperImgLoad')
                this.isLoad = true
            }
        }
    }
}
</script>

<style>
    #home {
        color: white;
    }
</style>