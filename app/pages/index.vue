<script setup>
import rightIcon from '@/assets/icons/arrow-right-small.svg'
import member from '@/assets/icons/member.svg'
import CommonStep from '~/components/CommonStep.vue'

const errorMsg = ref('')
const inputRef = ref(null)

const a = () => {
  inputRef.value?.focus()
}

const optionResult = ref(['選項A', '選項B', '選項C'])
const steps = [{ title: '步驟1', content: '說明1' }, { title: '步驟2', content: '說明2' }, { title: '步驟3', content: '說明3' }]
const pathItems = [
  { to: '/', label: '路徑1' },
  { to: '/', label: '路徑2' },
  { to: '/', label: '路徑3' },
  { label: '路徑4' },
]
</script>
<template>
  <div class="flex justify-around">
    <h1 class="text-primary text-8xl">首頁</h1>
    <div class="">
      <CommonBreadcrumb :items="pathItems"/>
      <br>
      <CommonButton type="primary" @click="a">
        Button
      </CommonButton>
      <br>
      <CommonInput ref="inputRef" :error-msg="errorMsg" type="password" title="aaa"/>
      <br>
      <CommonSelect error-msg="" :options="optionResult"/>
      <br>
      <CommonStep :steps="steps" current-step="2"/>
      <br>
      <CommonBack/>
    </div>
  </div>
</template>
