<template>
  <div class="option-container">
    <h4>{{ option.title }}</h4>
    <div class="option-buttons">
      <button
        class="option"
        v-for="(value, index) in option.buttons"
        :key="index"
        :class="classes(value, index)"
        @click="options[option.category] = value"
      >
        {{ value }}
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { Gender, Length, Popularity, Options } from '../models/Names'

interface OptionProps {
  option: {
    title: string
    category: string
    buttons: Gender[] | Popularity[] | Length[]
  }
  options: Options
}

const props = defineProps<OptionProps>()

const classes = (value, index) => {
  const classNames: string[] = []

  if (props.options[props.option.category] === value) classNames.push(`option-active`)
  if (!index) classNames.push(`option-left`)
  if (++index === props.option.buttons.length) classNames.push(`option-right`)

  return classNames.join(` `)
}
</script>

<style lang="less">
.option-container {
  @apply mb-8;
}

.option {
  @apply bg-white border-purple-500 border-2 p-3 w-1/4 text-xl cursor-pointer;

  &:hover {
    @apply bg-slate-400;
  }
}

h4 {
  @apply font-bold;
}

.option-left {
  border-radius: 1rem 0 0 1rem;
}

.option-right {
  border-radius: 0 1rem 1rem 0;
}

.option-active {
  @apply bg-purple-300 text-white;
}
</style>
