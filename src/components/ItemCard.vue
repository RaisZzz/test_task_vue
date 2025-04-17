<script setup lang="ts">
import { type PropType } from 'vue'
import type { IItem } from '@/models/item.ts'

defineProps({
  item: { type: Object as PropType<IItem>, required: true },
})
</script>

<template>
  <button class="item-card">
    {{ item.name }}
  </button>
</template>

<style scoped lang="sass">
.item-card
  width: 100%
  aspect-ratio: 1
  border: 2px solid #000
  display: flex
  flex-direction: column
  align-items: center
  justify-content: center
  text-align: center
  cursor: pointer
  background: none
  outline: none
</style>
