<script setup>
import rightIcon from '@/assets/icons/arrow-right-small.svg'
import member from '@/assets/icons/member.svg'

const errorMsg = ref('')
const inputRef = ref(null)

const a = () => {
  inputRef.value?.focus()
}
const optionResult = ref(['選項A', '選項B', '選項C'])
</script>
<template>
  <div class="flex justify-around">
    <h1 class="text-primary text-8xl">首頁</h1>
    <div class="">
      <CommonButton type="primary" @click="a">
        Button
      </CommonButton>
      <br>
      <CommonInput ref="inputRef" :error-msg="errorMsg" type="password" title="aaa"/>
      <br>
      <CommonSelect error-msg="" :options="optionResult"/>
    </div>
  </div>
</template>
