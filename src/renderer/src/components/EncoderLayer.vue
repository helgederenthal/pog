<template>
  <div
    v-if="keyboardStore.encoderKeymap[lindex] && keyboardStore.encoderKeymap[lindex][eindex]"
    class="mb-4 flex items-center gap-4"
  >
    <p class="w-24">Layer {{ lindex }}</p>
    <input
      v-model="keyboardStore.encoderKeymap[lindex][eindex][0]"
      type="text"
      class="input input-bordered input-sm"
    />
    <input
      v-model="keyboardStore.encoderKeymap[lindex][eindex][1]"
      type="text"
      class="input input-bordered input-sm"
    />
  </div>
</template>

<script lang="ts" setup>
import { keyboardStore } from '../store'
const props = defineProps(['lindex', 'layer', 'eindex'])
if (!keyboardStore.encoderKeymap[props.lindex]) {
  // create the layer
  keyboardStore.encoderKeymap[props.lindex] = []
}
if (!keyboardStore.encoderKeymap[props.lindex][props.eindex]) {
  keyboardStore.encoderKeymap[props.lindex][props.eindex] = ['KC.TRNS', 'KC.TRNS']
}
</script>

<style lang="scss" scoped></style>
