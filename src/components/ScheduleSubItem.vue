<template>
  <div class="ara-item">
    <i>
      <slot name="time"></slot>
    </i>
    <div class="details">
      <slot></slot>
    </div>
  </div>
</template>

<style scoped>
.ara-item {
  margin-top: 2rem;
  display: flex;
}

.details {
  flex: 1;
  margin-left: 1rem;
  margin-top: 0.1em;
  font-size: 1.4rem;
  /* margin-bottom: rem; */
}

i {
  display: flex;
  place-items: center;
  place-content: center;
  width: 32px;
  height: 32px;

  font: inherit;
  font-size: 1.3rem;
  color: var(--color-text);
}

h3 {
  font-size: 1rem;
  font-weight: 500;
  margin-bottom: 0.4rem;
  color: var(--color-heading);
}

.selected .details {
  color: black;
  transition: 0.4s;
}

@media (hover: hover) {
  .ara-item:hover {
    /* background-color: hsla(160, 100%, 37%, 0.2); */
    background-color: #b6a338;
    border-radius: 25px;
    transition: 0.4s;
  }

  .ara-item:hover .details {
    color: black;
  }
}

@media (min-width: 1024px) {
  .ara-item {
    margin-top: 0;
    padding: 0.1em 0 0.1em calc(var(--section-gap) / 2);
  }

  i {
    top: calc(50% - 20px);
    left: -32px;
    position: absolute;
    border: 2px solid var(--color-border);
    background: var(--color-background);
    border-radius: 8px;
    width: 64px;
    height: 40px;
  }

  .ara-item:before {
    content: " ";
    border-left: 2px solid var(--color-border);
    position: absolute;
    left: 0;
    bottom: calc(50% + 20px);
    height: calc(50% - 20px);
  }

  .ara-item:after {
    content: " ";
    border-left: 2px solid var(--color-border);
    position: absolute;
    left: 0;
    top: calc(50% + 20px);
    height: calc(50% - 20px);
  }

  .ara-item:first-of-type:before {
    display: none;
  }

  .item:last-of-type:after {
    display: none;
  }
}
</style>
