<template>
  <div class="multi-range">
    <div v-if="coast" class="multi-range__value">
      <span class="multi-range__value-min">{{ barMinValue }}</span>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="2"
        height="15"
        viewBox="0 0 2 15"
        fill="none"
      >
        <path d="M1 0.8125L1 14.8125" stroke="#083E4C" stroke-opacity="0.5" />
      </svg>
      <span class="multi-range__value-max">{{ barMaxValue }}</span>
    </div>
    <div v-if="initPayment" class="multi-range__value">
      <div class="multi-range__init-payment">{{ barMaxValue.toFixed() }}</div>
      <div class="multi-range__percent">{{ percent }}%</div>
    </div>
    <div v-if="years" class="multi-range__value">
      {{ barMaxValue.toFixed() }} лет
    </div>
    <MultiRangeSlider
      :class="{ single }"
      :min="min"
      :max="max"
      :step="0.1"
      :ruler="false"
      :label="false"
      :minValue="barMinValue"
      :maxValue="barMaxValue"
      @input="UpdateValues"
    />
  </div>
</template>

<script setup>
import MultiRangeSlider from "multi-range-slider-vue";
import { ref, defineProps, defineEmits, computed } from "vue";
import "../../../node_modules/multi-range-slider-vue/MultiRangeSliderBarOnly.css";

const p = defineProps({
  min: Number,
  max: Number,
  step: Number,
  single: Boolean,
  coast: Boolean,
  initPayment: Boolean,
  years: Boolean,
  inputValue: Number,
});

const emit = defineEmits(["getValue"]);

const barMinValue = ref(p.min);
const barMaxValue = ref(p.max);

const UpdateValues = (e) => {
  barMinValue.value = e.minValue;
  barMaxValue.value = e.maxValue;

  emit("getValue", {
    min: barMinValue.value || 0,
    max: barMaxValue.value || 0,
    percent: percent.value || 0,
    years: barMaxValue.value || 1,
  });
};

const percent = computed(() => {
  return ((barMaxValue.value / p.inputValue) * 100).toFixed();
});
</script>

<style lang="scss" scoped>
.multi-range {
  display: flex;
  flex-direction: column;
  width: 100%;
  max-width: 350px;
  padding: 20px 20px 22px 20px;
  justify-content: space-between;
  align-items: flex-start;
  flex-shrink: 0;
  border-radius: 100px;
  background: $bg-range;
  box-shadow: 0px 4px 15px 0px rgba(0, 0, 0, 0.02);

  &__value {
    display: flex;
    justify-content: space-between;
    width: 100%;

    &-min,
    &-max {
      width: 25px;
    }
  }
}
</style>
<style lang="scss">
.multi-range-slider {
  width: 100%;
  padding: 0;
  bottom: -20px;
  border: none;
  box-shadow: none;

  &.single {
    .thumb-left {
      display: none;
      pointer-events: none;
    }
  }

  .bar-inner {
    margin: 0 8px;
    background-color: $green;
  }

  .bar-right,
  .bar-left {
    background-color: transparent;
    box-shadow: none;
  }

  .bar-left {
    padding: 1px 0;
  }

  .thumb::before {
    width: 12px;
    height: 12px;
    margin: -6px;
    background-color: $green;
    border: none;
    box-shadow: none;
  }

  .thumb:active {
    .caption {
      display: none;
    }
  }
}
</style>
