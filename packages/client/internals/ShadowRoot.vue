<script setup lang="ts">
import { computed, ref, watchEffect } from 'vue'

const props = defineProps<{
  innerHtml: string
}>()

const el = ref<HTMLDivElement>()
const shadow = computed(() => el.value ? (el.value.shadowRoot || el.value.attachShadow({ mode: 'open' })) : null)
watchEffect(() => {
  if (shadow.value)
    shadow.value.innerHTML = props.innerHtml
})
</script>

<template>
  <div ref="el" />
</template>
