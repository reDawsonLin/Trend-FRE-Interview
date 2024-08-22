<script setup>
import Icons from "./Icons.vue";

defineProps({ buttonStyle: String, iconName: String });
</script>

<template>
  <button :class="buttonStyle">
    <Icons v-if="iconName" :name="iconName" />
    <slot></slot>
  </button>
</template>

<style scoped>
button {
  display: flex;
  gap: 0.75rem;
  padding: 1rem 0.75rem;
  background-color: var(--primary);
  color: var(--white);
  border-radius: 0.25rem;
  transition: box-shadow 0.15s ease;

  .box_icon{
    width: 1rem;
  }

  &:hover{
    box-shadow: 2px 2px 5px var(--primary);
  }


  &.line {
    background-color: #fff;
    color: var(--black);
    border: 1px solid var(--primary);
    transition: background-color 0.15s ease, color 0.15s ease;

    .box_icon {
      color: var(--primary);
    }

    &:hover {
      background-color: var(--primary);
      color: var(--white);
      box-shadow: none;

      .box_icon {
        color: var(--white);
      }
    }

  }




}
</style>
