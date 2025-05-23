<script setup lang="ts">
import ItemCard from '@/components/ItemCard.vue'
import type { IItem } from '@/models/item.ts'
import { ref, type Ref } from 'vue'

const maxUserItemsSelectedCount: number = 6
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

const userChosenItems: Ref<IItem[]> = ref([])
const chosenItem: Ref<IItem | undefined> = ref()

const userItemSelect = (item: IItem): void => {
  const itemExistIndex: number = userChosenItems.value.findIndex((i: IItem) => i.id === item.id)
  if (itemExistIndex >= 0) {
    userChosenItems.value.splice(itemExistIndex, 1)
  } else {
    if (userChosenItems.value.length < maxUserItemsSelectedCount) {
      userChosenItems.value.push(item)
    }
  }
}

const itemSelect = (item: IItem): void => {
  chosenItem.value = item
}
const itemUnselect = (): void => {
  chosenItem.value = undefined
}
</script>

<template>
  <div class="container items">
    <div class="items-row">
      <div class="items-chosen-wrapper">
        <div class="items-chosen">
          <ItemCard
            v-for="item in userChosenItems"
            :key="item.id"
            :item="item"
            @click="userItemSelect(item)"
          />
        </div>
      </div>
      <div class="single-item-wrapper">
        <ItemCard v-if="chosenItem" class="single-item" :item="chosenItem" @click="itemUnselect" />
      </div>
    </div>
    <div class="items-row">
      <div class="items-list">
        <ItemCard
          v-for="item in userItems"
          :key="item.id"
          :item="item"
          @click="userItemSelect(item)"
        />
      </div>
      <div class="items-list">
        <ItemCard
          v-for="item in itemsToChoose"
          :key="item.id"
          :item="item"
          @click="itemSelect(item)"
        />
      </div>
    </div>
  </div>
</template>

<style scoped lang="sass">
.items
  display: flex
  flex-direction: column
  gap: 20px

  &-row
    width: 100%
    display: flex
    align-items: stretch
    gap: 20px
    justify-content: space-between

  &-list
    width: 100%
    border: 2px solid #000
    padding: 10px
    display: grid
    grid-template-columns: repeat(4, 1fr)
    grid-gap: 10px
    min-height: 500px
    align-content: start

  &-chosen
    width: 100%
    max-width: 200px
    border: 2px solid #000
    padding: 10px
    display: grid
    grid-template-columns: repeat(2, 1fr)
    grid-gap: 10px
    flex: auto
    min-height: 107px

    &-wrapper
      width: 100%

.single-item
  width: 100%
  max-width: 107px

  &-wrapper
    width: 100%
    display: flex
    justify-content: flex-end
</style>
