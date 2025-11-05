<script setup>
import homeIcon from '@/assets/icons/home.svg'
import arrowIcon from '@/assets/icons/arrow-right.svg'
defineProps({
  items: { type: Array, default: () => [] },
})
</script>
<template>
    <nav>
        <ol class="flex space-x-2">
            <li>
                <NuxtLink to="/" class="flex hover:underline">
                    <img :src="homeIcon" alt="" class=" size-6">
                    <span>首頁</span>
                </NuxtLink>
            </li>
            <template v-for="(item, index) in items" :key="index">
                <li class="flex items-center space-x-1">
                    <img :src="arrowIcon" alt="" class=" size-6">
                    <NuxtLink v-if="item.to" :to="item.to" class="hover:underline">
                        {{ item.label }}
                    </NuxtLink>
                    <span v-else>{{ item.label }}</span>
                </li>
            </template>
        </ol>
    </nav>
</template>
