<script setup>
import errorIcon from '@/assets/icons/error.svg'
import eyeIcon from '@/assets/icons/eye.svg'
import eyeOffIcon from '@/assets/icons/eye-off.svg'
import searchIcon from '@/assets/icons/search.svg'
const props = defineProps({
  type: { type: String, default: 'text' },
  placeholder: { type: String, default: '' },
  errorMsg: { type: String, default: '' },
  disabled: { type: Boolean, default: false },
  title: { type: String, default: '' },
})
const id = useId()
const showPassword = ref(false)

const classResult = computed(() => {
  const errorClass = props.errorMsg !== '' ? 'border-danger' : 'border-font-muted-color'
  const disabledClass = props.disabled ? 'bg-gray-300 cursor-not-allowed' : ''
  return [errorClass, disabledClass]
})

const inputRef = ref(null)
const focus = () => {
  inputRef.value?.focus()
}

defineExpose({
  focus,
})

</script>
<template>
    <div class="relative">
        <template v-if="props.type === 'password' || props.type === 'search' || props.type === 'text' || props.type === ''">
            <label :for="id" class="text-font-color text-base font-semibold">{{ props.title }}</label><br>
            <input :id="id" ref="inputRef" :disabled="props.disabled" :class="classResult" :placeholder="props.placeholder" :type="props.type === 'password' ? 'password' : 'text'"           class="caret-primary-light input-thick-caret focus:outline-primary-light h-14 rounded-lg border-1 bg-white px-2 pr-3 text-base font-normal focus:border-transparent focus:shadow-[0_0_6px_#2c6084] focus:outline-2">
            <button v-if="props.type === 'password'" class="absolute -translate-y-1/2 top-1/2 right-3" @click="showPassword = !showPassword">
                <img :src="showPassword ? eyeIcon : eyeOffIcon">
            </button>
            <button v-if="props.type === 'search'">
                <img :src="searchIcon" class="absolute -translate-y-1/2 top-1/2 right-3">
            </button>
            <div v-if="props.errorMsg !== ''" class=" bg-danger-light text-danger flex min-h-[30px] items-center mt-1.5 rounded-lg px-2 text-base font-normal">
                <img :src="errorIcon">
                {{ props.errorMsg }}
            </div>
        </template>
        <template v-else>
            <label class="text-font-color me-3 inline-flex cursor-pointer items-center space-x-1.5 text-base font-normal">
                <input class="h-5 w-5 focus:outline-primary-light accent-primary text-primary focus:outline-2 focus:outline-offset-[2px]" :type="props.type" :disabled="props.disabled">
                <span>{{ props.title }}</span>
            </label>
        </template>
    </div>
</template>
