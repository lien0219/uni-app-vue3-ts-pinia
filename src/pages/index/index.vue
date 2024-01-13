<script setup lang="ts">
import { onLoad } from '@dcloudio/uni-app'
import CustomNavbar from './components/CustomNavbar.vue'
import { getHomeBannerAPI } from '@/services/home'
import { ref } from 'vue'
import type { BannerItem } from '@/types/home'

const bannerList = ref<BannerItem[]>([])
const getHomeBannerData = async () => {
  const res = await getHomeBannerAPI()
  bannerList.value = res.result
}

onLoad(() => {
  getHomeBannerData()
})
</script>

<template>
  <!-- 自定义导航 -->
  <CustomNavbar></CustomNavbar>
  <!-- 自定义轮播组件 -->
  <XtxSwiper :list="bannerList"></XtxSwiper>
  <view class="index">index</view>
</template>

<style lang="scss">
//
</style>
