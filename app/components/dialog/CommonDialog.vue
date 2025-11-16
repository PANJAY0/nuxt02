<script setup>
import closeIcon from '@/assets/icons/close.svg'
const model = ref(false)
const showClose = ref(true)
const aa = () => {
  console.log('aaa')
  model.value = !model.value
}
</script>
<template>
    <div>
        <CommonButton @click="aa">按鈕</CommonButton>
        <Transition name="show-ani">
            <div v-if="model" class="inset-0">
                <div class="flex items-center justify-between gap-4 relative">
                    <h2>
                        <slot name="title"/>
                    </h2>
                    <button v-if="showClose" class="cursor-pointer absolute top-0 right-0" @click="handleClose">
                        <img :src="closeIcon" alt="">
                    </button>
                </div>
            </div>
        </Transition>
    </div>
</template>
<style scoped>
.show-ani-enter-active,
.show-ani-leave-active {
  transition: opacity 0.5s ease;
}
.show-ani-enter-from,
.show-ani-leave-to {
  opacity: 0;
}
</style>
