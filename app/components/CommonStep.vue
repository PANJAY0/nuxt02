<script setup>
import checkCircleIcon from '@/assets/icons/check-circle.svg'
const props = defineProps({
  steps: { type: Array, default: () => {} },
  currentStep: { type: Number, default: 1 },
})

const isCompleted = (index) => {
  return index + 1 < props.currentStep
}

const isActive = (index) => {
  console.log('aaa', index)
  return index + 1 === props.currentStep
}
</script>
<template>
    <div class="space-y-3">
        <div v-for="(item, index) in props.steps" :key="index" class="flex items-start min-h-20 gap-3">
            <div class="flex justify-center items-center gap-3 flex-col">
                <img v-if="isCompleted(index)" :src="checkCircleIcon" alt="" class=" h-8 w-8">
                <div
v-else
                class="border rounded-full h-8 w-8 flex items-center justify-center font-semibold"
                :class="isActive(index)? 'border-primary-light text-primary': 'border-font-muted-color text-shadow-font-muted-color'">
                    {{ ++index }}
                </div>
                <div class=" bg-font-muted-color h-8 w-[1px]"/>
            </div>
            <div>
                <div class=" text-font-color mt-1 font-semibold"> {{ item.title }}</div>
                <div class=" text-gray-500 mt-1">{{ item.content }}</div>
            </div>
        </div>
    </div>
</template>
