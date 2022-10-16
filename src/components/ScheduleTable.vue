<script setup lang="ts">
import ScheduleItem from "./ScheduleItem.vue";
import ScheduleSubItem from "./ScheduleSubItem.vue";
import { ref } from "vue";

const selected = ref(0);

window.addEventListener(
  "keydown",
  (ev: KeyboardEvent) => {
    if (ev.key == " ") {
      selected.value = (selected.value + 1) % 8;
    }
  },
  { passive: true }
);
</script>

<template>
  <ScheduleItem :class="{ selected: selected === 0 }" @click="selected = 0">
    <template #time> 1230 </template>
    <template #heading>quack-8 (Arda Akın)</template>

    TTMO için yazılmış, reverse edilmeye Linux kadar açık bir JIT mi?
  </ScheduleItem>

  <ScheduleSubItem :class="{ selected: selected === 1 }" @click="selected = 1">
    <template #time> 1315 </template>

    Ara
  </ScheduleSubItem>

  <ScheduleItem :class="{ selected: selected === 2 }" @click="selected = 2">
    <template #time> 1330 </template>
    <template #heading>tarayıcı patlatmaca (Alp Eren Işık)</template>

    v8 Javascript engine dünyasına giriş
  </ScheduleItem>

  <ScheduleSubItem :class="{ selected: selected === 3 }" @click="selected = 3">
    <template #time> 1400 </template>

    PiZZA!
  </ScheduleSubItem>

  <ScheduleItem :class="{ selected: selected === 4 }" @click="selected = 4">
    <template #time> 1515 </template>
    <template #heading>hyper-v internals (Alperen Şirin)</template>

    Zafiyet araştırmacısı perspektifinden Hyper-v'ye ilk bakış
  </ScheduleItem>

  <ScheduleSubItem :class="{ selected: selected === 5 }" @click="selected = 5">
    <template #time> 1600 </template>

    Ara
  </ScheduleSubItem>

  <ScheduleItem :class="{ selected: selected === 6 }" @click="selected = 6">
    <template #time> 1615 </template>
    <template #heading>onaylanmak veya onaylanmamak (eybisi)</template>

    Derinlemesine Android RASP analizi
  </ScheduleItem>

  <ScheduleSubItem :class="{ selected: selected === 7 }" @click="selected = 7">
    <template #time> 1700 </template>

    Kapanış
  </ScheduleSubItem>
</template>

<style scoped>
.selected {
  background-color: #b6a338;
  border-radius: 25px;
  transition: 1.2s;
}
</style>
