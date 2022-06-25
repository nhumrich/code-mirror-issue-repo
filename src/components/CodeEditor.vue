<template>
  <Codemirror
      class="editor"
      v-model="code"
      aria-placeholder="Select * from ..."
      :style="{ flex: 1, 'text-align': 'left' }"
      :autofocus="true"
      :indent-with-tab="true"
      :tab-size="4"
      :extensions="extensions"
      />
</template>

<script setup>
import {Codemirror} from 'vue-codemirror';
import {keymap} from '@codemirror/view';
import {sql} from '@codemirror/lang-sql';
import {ref} from "vue";

const code = ref(`
--comment
select * from tables;`)

function modExec() {
  console.log('hit mod enter')
  return true
}

function shiftExec() {
  console.log('hit shift enter')
  return true
}

const extensions = [keymap.of([
    {key: 'Mod-Enter', preventDefault: true,
      run: modExec}, {key: 'Shift-Enter', preventDefault: true, run: shiftExec}]),
  sql()]

</script>

<style scoped>

</style>
