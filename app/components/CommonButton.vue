<script setup>
const props = defineProps({
  type: {
    type: String,
    defalut: 'primary', // 'primary' | 'secondary' | 'inverse' | 'primary-outline' | 'secondary-outline'
  },
  size: {
    type: String,
    defalut: 'md', // 'sm' | 'md' | 'lg'
  },
  disabled: {
    type: Boolean,
    defalut: false,
  },
})
const classResult = computed(() => {
  let typeClass = ''
  let sizeClass = ''
  switch (props.type) {
    case 'secondary':
      typeClass = 'btn--secondary'
      break
    case 'inverse':
      typeClass = 'btn--inverse'
      break
    case 'primary-outline':
      typeClass = 'btn--primary--outline'
      break
    case 'secondary-outline':
      typeClass = 'btn--secondary--outline'
      break
    default:
      typeClass = 'btn--primary'
  }
  switch (props.size) {
    case 'sm':
      sizeClass = 'btn--sm'
      break
    case 'lg':
      sizeClass = 'btn--lg'
      break
    default:
      sizeClass = ''
  }

  return [typeClass, sizeClass]
})
</script>
<template>

    <button class="btn" :class="classResult" :disabled="props.disabled" type="button">
        <slot/>
    </button>

</template>
