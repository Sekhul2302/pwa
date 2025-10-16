<script setup lang="ts">
import { ref, watch } from 'vue'

const props = defineProps<{
  modelValue: string
  label?: string
  type?: string
  placeholder?: string
}>()

const emit = defineEmits(['update:modelValue'])

// local copy
const localValue = ref(props.modelValue)

// kalau prop berubah dari luar → sinkronkan
watch(() => props.modelValue, (val) => {
  localValue.value = val
})
</script>

<template>
  <div class="mb-4">
    <label v-if="props.label" class="block text-sm font-medium text-gray-700 mb-1">
      {{ props.label }}
    </label>
    <input
      :type="props.type ?? 'text'"
      :placeholder="props.placeholder"
      v-model="localValue"
      @input="emit('update:modelValue', localValue)"
      class="w-full px-3 py-2 border rounded-lg text-sm focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 outline-none"
    />
  </div>
</template>
