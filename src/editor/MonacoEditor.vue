<script setup lang="ts">
import Monaco from '../monaco/Monaco.vue'
import type { EditorEmits, EditorProps } from '../types'

defineProps<EditorProps>()
const emit = defineEmits<EditorEmits>()

defineOptions({
  editorType: 'monaco',
})

const onChange = (code: string) => {
  emit('change', code)
}
const onSelection = (code: string) => {
  emit('selection', code)
}
const onCodeSelecte = (codeInfo: object) => {
  emit('codeSelected', codeInfo)
}
</script>

<template>
  <Monaco
    :filename="filename"
    :value="value"
    :readonly="readonly"
    :mode="mode"
    @change="onChange"
    @selection="onSelection"
    @codeSelected="onCodeSelecte"
  />
</template>
