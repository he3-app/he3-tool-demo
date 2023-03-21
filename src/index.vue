<template>
  <h-layout-single mode="middle" :width="1280">
    <div>
      <h-multiline-input
        v-model="input"
        auto-select
        :title="$t('input')"
        @change="encode" />
    </div>
    <h-multiline
      :value="output"
      :title="$t('output')" />
  </h-layout-single>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { toASCII } from 'punycode';

const EXAMPLE_DOMAIN = '中文.com';
const input = ref(EXAMPLE_DOMAIN);
const output = ref('');

onMounted(() => {
  encode();
});

function encode() {
  output.value = toASCII(input.value);
}
</script>

<style scoped lang="less"></style>
