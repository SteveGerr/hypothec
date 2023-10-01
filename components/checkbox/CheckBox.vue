<template>
  <label class="checkbox" :for="id">
    <input
      class="checkbox__input"
      type="checkbox"
      v-model="model"
      :value="value"
      :id="id"
    />
    <div class="checkbox__custom"></div>
    <span>{{ label }}</span>
  </label>
</template>

<script setup>
import { computed, defineEmits, defineProps } from "vue";
const props = defineProps({
  modelValue: { type: [Array, Boolean] },
  value: { type: [Boolean, String] },
  label: { type: String },
  id: {
    type: [String, Number],
    required: true,
  },
});
const emit = defineEmits(["update:modelValue"]);
const model = computed({
  get() {
    return props.modelValue;
  },
  set(value) {
    emit("update:modelValue", value);
  },
});
</script>

<style lang="scss" scoped>
.checkbox {
  display: inline-flex;
  align-items: center;
  gap: 10px;

  &__input {
    display: none;

    &:checked ~ .checkbox__custom::after {
      display: flex;
    }
  }

  &__custom {
    display: flex;
    width: 25px;
    height: 25px;
    border-radius: 6px;
    border: 1px solid $green;
    background: $white;
    box-shadow: 0px 4px 15px 0px rgba(0, 0, 0, 0.02);
    position: relative;

    &::after {
      content: "";
      display: none;
      width: 21px;
      height: 21px;
      background-color: $green;
      border-radius: 6px;
      position: absolute;
      top: 1px;
      left: 1px;
    }
  }
}
</style>
