<script setup>
import arrowIcon from '@/assets/icons/arrow-down.svg'
import errorIcon from '@/assets/icons/error.svg'
// const optionResult = ref(['選項A', '選項B', '選項C'])
const props = defineProps({
  options: { type: Array, default: () => {} },
  errorMsg: { type: String, default: '' },
  placeholder: { type: String, default: '請選擇' },
  disable: { type: Boolean, default: false },
})

const classResult = computed(() => {
  const errorClass = props.errorMsg !== '' ? 'border-danger' : 'border-font-muted-color'

  return [errorClass]
})
</script>
<template>
    <div>
        <div class="relative">
            <select :class="classResult" class="bg-white caret-primary-light focus:outline-primary-light rounded-lg h-14 w-[400px] appearance-none border-1 px-2 text-base font-normal focus:border-transparent focus:shadow-[0_0_6px_#2c6084] focus:outline-2">
                <option v-for="(item, index) in props.options" :key="index">
                    {{ item }}
                </option>
            </select>
            <img :src="arrowIcon" class=" absolute top-1/2 right-3 h-4 w-4 -translate-y-1/2 pointer-events-none" >
        </div>
        <div v-if="errorMsg !== ''" class=" bg-danger-light text-danger mt-1.5 flex min-h-[30px] rounded-lg items-center px-2 text-base font-normal">
            <img :src="errorIcon" class=" mr-1 h-5 w-5">
            {{ props.errorMsg }}
        </div>
    </div>
</template>
