<script setup lang="ts">
import { customRef, ref } from "vue"

const count = ref(1)
const plusOne = customRef<number>((onGet, onSet) => ({
  get() {
    onGet()
    return count.value + 1
  },
  set(newValue) {
    onSet()
    count.value = newValue - 1
  },
}))

/**
 * Make the `plusOne` writable.
 * So that we can get the result `plusOne` to be 3, and `count` to be 2.
 */

plusOne.value++
</script>

<template>
  <div>
    <p>{{ count }}</p>
    <p>{{ plusOne }}</p>
  </div>
</template>
