
import { ScriptCompileContext } from 'vue/compiler-sfc';
<script setup>
// defineEmits(['reset'])
// const emit = defineEmits(['reset'])
// function emitReset() {
//     emit('reset', 100)
// }

</script>
<template>
    <button @click="$emit('reset', 100)">Reset</button>
    <!-- 別の書き方 -->
    <!-- <button @click="emitReset">Reset</button> -->
</template>
