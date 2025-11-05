<!-- common/CommonBackButton.vue -->
<script setup>
import backIcon from '@/assets/icons/arrow-back.svg'
defineProps({
  to: {
    type: [String, Object],
    default: '',
  },
  goBack: {
    type: Boolean,
    default: false,
  },
})

const router = useRouter()
</script>
<template>
  <NuxtLink :to="to" class="text-font-color inline-flex cursor-pointer items-center font-semibold" @click="goBack ? router.back() : null">
    <img :src="backIcon" alt="返回" aria-hidden="true" class="h-5 w-5" >
    <span class="ml-2">
      <slot>返回</slot>
    </span>
  </NuxtLink>
</template>
