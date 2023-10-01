<template>
  <div class="badge" :style="{ backgroundColor: bgColor || '#083E4C', color }">
    <slot></slot>
  </div>
</template>

<script setup>
defineProps({
  bgColor: String,
  color: String,
});
</script>

<style lang="scss" scoped>
.badge {
  display: inline-block;
  padding: 10px;
  font-size: 14px;
  font-style: normal;
  font-weight: 500;
  line-height: 100%;
  border-radius: 10px;
  color: $white;
}
</style>
