<script setup>
import downIcon from '@/assets/icons/arrow-down-small.svg'
</script>
<template>
  <div>
    <h1 class="text-primary text-8xl">首頁</h1>
    <CommonButton>
      <img :src="downIcon">
      測試
    </CommonButton>
  </div>
</template>
