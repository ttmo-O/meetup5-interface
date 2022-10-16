<script setup lang="ts">
defineProps({
  type: String,
});
</script>

<template>
  <div class="item" :class="type">
    <i>
      <slot name="time"></slot>
    </i>
    <div class="details">
      <h3 v-if="type == 'main'">
        <slot name="heading"></slot>
      </h3>
      <slot></slot>
    </div>
  </div>
</template>

<style scoped>
.item {
  margin-top: 2rem;
  display: flex;
}

.details {
  flex: 1;
  margin-left: 1rem;
}

i {
  display: flex;
  place-items: center;
  place-content: center;
  width: 32px;
  height: 32px;

  font: inherit;
  color: var(--color-text);
}

h3 {
  font-size: 1.6rem;
  font-weight: 500;
  margin-bottom: 0.4rem;
  color: var(--color-heading);
}

.selected .details {
  color: black;
  transition: 0.4s;
}

@media (min-width: 1024px) {
  .item {
    margin-top: 0;
    padding: 2rem 0 1rem calc(var(--section-gap) / 2);
  }

  i {
    top: calc(50% - 25px);
    left: -48px;
    position: absolute;
    border: 2px solid var(--color-border);
    background: var(--color-background);
    border-radius: 8px;
    width: 96px;
    height: 50px;
  }

  .item:before {
    content: " ";
    border-left: 2px solid var(--color-border);
    position: absolute;
    left: 0;
    bottom: calc(50% + 25px);
    height: calc(50% - 25px);
  }

  .item:after {
    content: " ";
    border-left: 2px solid var(--color-border);
    position: absolute;
    left: 0;
    top: calc(50% + 25px);
    height: calc(50% - 25px);
  }

  .item:first-of-type:before {
    display: none;
  }

  .item:last-of-type:after {
    display: none;
  }
}

.sub {
  margin-top: 2rem;
  display: flex;
}

.sub .details {
  flex: 1;
  margin-left: 1rem;
  margin-top: 0.1em;
  font-size: 1.4rem;
  /* margin-bottom: rem; */
}

.sub i {
  display: flex;
  place-items: center;
  place-content: center;
  width: 32px;
  height: 32px;

  font: inherit;
  font-size: 1.3rem;
  color: var(--color-text);
}

.sub h3 {
  font-size: 1rem;
  font-weight: 500;
  margin-bottom: 0.4rem;
  color: var(--color-heading);
}

@media (min-width: 1024px) {
  .sub {
    margin-top: 0;
    padding: 0.1em 0 0.1em calc(var(--section-gap) / 2);
  }

  .sub i {
    top: calc(50% - 20px);
    left: -32px;
    position: absolute;
    border: 2px solid var(--color-border);
    background: var(--color-background);
    border-radius: 8px;
    width: 64px;
    height: 40px;
  }

  .sub:before {
    content: " ";
    border-left: 2px solid var(--color-border);
    position: absolute;
    left: 0;
    bottom: calc(50% + 20px);
    height: calc(50% - 20px);
  }

  .sub:after {
    content: " ";
    border-left: 2px solid var(--color-border);
    position: absolute;
    left: 0;
    top: calc(50% + 20px);
    height: calc(50% - 20px);
  }
}
</style>
