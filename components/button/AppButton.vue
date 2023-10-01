<template>
  <button
    :class="['app-button', { circle, fill, disabled }]"
    @click="$emit('onCkick')"
  >
    <svg
      v-if="circlePlay"
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 65 66"
      fill="none"
    >
      <path
        d="M40.3889 33.1687C41.0556 33.5536 41.0556 34.5158 40.3889 34.9007L30.3889 40.6742C29.7222 41.0591 28.8889 40.578 28.8889 39.8082L28.8889 28.2612C28.8889 27.4914 29.7222 27.0103 30.3889 27.3952L40.3889 33.1687Z"
        fill="white"
      />
    </svg>
    <svg
      v-if="arrowRight"
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 62 62"
      fill="none"
    >
      <path
        d="M35.5 29.9465C36.1667 30.3314 36.1667 31.2936 35.5 31.6785L29.5 35.1426C28.8333 35.5275 28 35.0464 28 34.2766L28 27.3484C28 26.5786 28.8333 26.0975 29.5 26.4824L35.5 29.9465Z"
        fill="#083E4C"
      />
    </svg>
    <svg
      v-if="arrowLeft"
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 62 62"
      fill="none"
    >
      <path
        d="M26.5 29.9465C25.8333 30.3314 25.8333 31.2936 26.5 31.6785L32.5 35.1426C33.1667 35.5275 34 35.0464 34 34.2766L34 27.3484C34 26.5786 33.1667 26.0975 32.5 26.4824L26.5 29.9465Z"
        fill="#083E4C"
      />
    </svg>
    <slot></slot>
  </button>
</template>

<script setup>
import { defineEmits, defineProps } from "vue";

defineEmits(["onCkick"]);
defineProps({
  circle: Boolean,
  circlePlay: Boolean,
  fill: Boolean,
  arrowLeft: Boolean,
  arrowRight: Boolean,
  disabled: Boolean,
});
</script>

<style lang="scss" scoped>
.app-button {
  display: inline-flex;
  padding: 20px 25px;
  border-radius: 100px;
  border: 1px solid $green;
  position: relative;
  background-color: $white;
  font-size: 16px;
  font-style: normal;
  font-weight: 500;
  line-height: 100%;
  color: $green;
  cursor: pointer;

  &:hover {
    background-color: $green;
    color: $white;
  }

  &.circle {
    width: 60px;
    min-width: 60px;
    height: 60px;
    min-height: 60px;
    border-radius: 50%;
  }

  &.fill {
    background-color: $green;
    color: $white;

    &:hover {
      background-color: $white;
      color: $green;
    }

    svg {
      &:hover {
        path {
          fill: $green;
        }
      }
    }
  }

  svg {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;

    &:hover {
      path {
        fill: $white;
      }
    }
  }

  &.disabled {
    opacity: 0.4;
    pointer-events: none;
  }
}
</style>
