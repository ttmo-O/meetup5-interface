<script setup lang="ts">
import WelcomeItem from "./WelcomeItem.vue";
import DocumentationIcon from "./icons/IconDocumentation.vue";
import ToolingIcon from "./icons/IconTooling.vue";
import EcosystemIcon from "./icons/IconEcosystem.vue";
import CommunityIcon from "./icons/IconCommunity.vue";
import SupportIcon from "./icons/IconSupport.vue";
import AraItem from "./AraItem.vue";
import { ref } from "vue";

const selected = ref(0);

window.addEventListener("keydown", (ev: KeyboardEvent) => {
  if (ev.key == " ") {
    selected.value = (selected.value + 1) % 8;
  }
}, { passive: true })
</script>

<template>
  <WelcomeItem :class=' { "selected": selected === 0 } '
                @click='selected = 0'
                >
    <template #icon>
      1230
    </template>
    <template #heading>quack-8 (Arda Akın)</template>

    TTMO için yazılmış, reverse edilmeye Linux kadar açık bir JIT mi?
  </WelcomeItem>

  <AraItem :class=' { "selected": selected === 1 } '
                @click='selected = 1'
                >
    <template #icon>
      1315
    </template>

    Ara
  </AraItem>

  <WelcomeItem :class=' { "selected": selected === 2 } '
                @click='selected = 2'
                >
    <template #icon>
      1330
    </template>
    <template #heading>tarayıcı patlatmaca (Alp Eren Işık)</template>

    v8 Javascript engine dünyasına giriş
  </WelcomeItem>

  <AraItem :class=' { "selected": selected === 3 } '
                @click='selected = 3'
                >
    <template #icon>
      1400
    </template>

    PiZZA!
  </AraItem>

  <WelcomeItem :class=' { "selected": selected === 4 } '
                @click='selected = 4'
                >
    <template #icon>
      1515
    </template>
    <template #heading>hyper-v internals (Alperen Şirin)</template>

    Zafiyet araştırmacısı perspektifinden Hyper-v'ye ilk bakış
  </WelcomeItem>

  <AraItem :class=' { "selected": selected === 5 } '
                @click='selected = 5'
                >
    <template #icon>
      1600
    </template>

    Ara
  </AraItem>

  <WelcomeItem :class=' { "selected": selected === 6 } '
                @click='selected = 6'
                >
    <template #icon>
      1615 
    </template>
    <template #heading>onaylanmak veya onaylanmamak (eybisi)</template>

    Derinlemesine Android RASP analizi
  </WelcomeItem>

  <AraItem :class=' { "selected": selected === 7 } '
                @click='selected = 7'
                >
    <template #icon>
      1700
    </template>

    Kapanış
  </AraItem>
</template>

<style scoped>
.selected{
  background-color: #b6a338;
  border-radius: 25px;
  transition: 1.2s;
}
</style>