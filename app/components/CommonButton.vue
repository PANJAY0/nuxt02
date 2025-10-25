<script setup>
const props = defineProps({
  color: {

  },
})
</script>
<template>
    <div>
        <button class="btn btn--primary--inverse btn--lg" type="button">
            <slot/>
        </button>
    </div>
</template>
