<script setup lang="ts">
import { ref } from "vue";
import ScheduleItem from "./ScheduleItem.vue";

interface ScheduleEntry {
  type: string;
  time: string;
  heading?: string;
  description: string;
}

let entries: ScheduleEntry[] = [
  {
    type: "main",
    time: "1230",
    heading: "quack-8 (Arda Akın)",
    description:
      "TTMO için yazılmış, reverse edilmeye Linux kadar açık bir JIT mi?",
  },
  { type: "sub", time: "1315", description: "Ara" },
  {
    type: "main",
    time: "1330",
    heading: "tarayıcı patlatmaca (Alp Eren Işık)",
    description: "v8 Javascript engine dünyasına giriş",
  },
  { type: "sub", time: "1400", description: "PiZZA!" },
  {
    type: "main",
    time: "1515",
    heading: "hyper-v internals (Alperen Şirin)",
    description: "Zafiyet araştırmacısı perspektifinden Hyper-v'ye ilk bakış",
  },
  { type: "sub", time: "1230", heading: "1600", description: "Ara" },
  {
    type: "main",
    time: "1615",
    heading: "onaylanmak veya onaylanmamak (eybisi)",
    description: "Derinlemesine Android RASP analizi",
  },
  { type: "sub", time: "1700", description: "Kapanış" },
];

const activeIdx = ref(0);

window.addEventListener(
  "keydown",
  (ev: KeyboardEvent) => {
    if (ev.key == " ") {
      activeIdx.value = (activeIdx.value + 1) % entries.length;
    }
  },
  { passive: true }
);
</script>

<template>
  <ScheduleItem
    :type="entry.type"
    v-for="(entry, index) in entries"
    :key="index"
    :class="{ selected: activeIdx == index }"
  >
    <template #time>{{ entry.time }}</template>
    <template #heading>{{ entry.heading }}</template>
    {{ entry.description }}
  </ScheduleItem>
</template>

<style scoped>
.selected {
  background-color: #b6a338;
  border-radius: 10px;
  transition: 1.2s;
}
</style>
