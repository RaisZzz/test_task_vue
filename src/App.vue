<script setup lang="ts">
import ItemCard from '@/components/ItemCard.vue'
import type { IItem } from '@/models/item.ts'

const userItems: IItem[] = [
  { id: 1, name: 'Shoes 1' },
  { id: 2, name: 'Shoes 2' },
  { id: 3, name: 'Shoes 3' },
  { id: 4, name: 'Shoes 4' },
  { id: 5, name: 'T-shirt 1' },
  { id: 6, name: 'T-shirt 2' },
  { id: 7, name: 'T-shirt 3' },
  { id: 8, name: 'T-shirt 4' },
]

const itemsToChoose: IItem[] = [
  { id: 11, name: 'Jacket 1' },
  { id: 12, name: 'Jacket 2' },
  { id: 13, name: 'Jacket 3' },
  { id: 14, name: 'Jacket 4' },
  { id: 15, name: 'Hoodie 1' },
  { id: 16, name: 'Hoodie 2' },
  { id: 17, name: 'Hoodie 3' },
  { id: 18, name: 'Hoodie 4' },
]
</script>

<template>
  <div class="container">
    <div class="items-row">
      <div class="items-list">
        <ItemCard v-for="item in userItems" :key="item.id" :item="item" />
      </div>
      <div class="items-list">
        <ItemCard v-for="item in itemsToChoose" :key="item.id" :item="item" />
      </div>
    </div>
  </div>
</template>

<style scoped lang="sass">
.items
  &-row
    width: 100%
    display: flex
    align-items: stretch
    gap: 10px

  &-list
    width: 100%
    border: 2px solid #000
    padding: 10px
    display: grid
    grid-template-columns: repeat(4, 1fr)
    grid-gap: 10px
    min-height: 500px
    align-content: start
</style>
