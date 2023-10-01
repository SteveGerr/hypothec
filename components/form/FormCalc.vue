<template>
  <div class="form-calc">
    <form class="form-calc__form" @submit.prevent>
      <Badge class="form-calc__badge" bgColor="rgba(8, 62, 76, 0.50)"
        >Ипотечный калькулятор</Badge
      >
      <div class="form-calc__label">Стоимость, млн ₽</div>
      <MultiRange :min="0" :max="5.6" :step="0.1" coast />
      <div class="form-calc__inputs">
        <CheckBox
          id="1"
          label="Квартира"
          v-model="selected"
          :value="'Квартира'"
        />
        <CheckBox
          id="2"
          label="Апартамент"
          v-model="selected"
          :value="'Апартамент'"
        />
      </div>
      <div class="form-calc__label">Первоначальный взнос, ₽</div>
      <MultiRange
        class="form-calc__init-payment"
        :min="0"
        :max="4000000"
        :step="100000"
        :input-value="5600000"
        init-payment
        single
        @getValue="getValue"
      />
      <div class="form-calc__label">Срок выплат</div>
      <MultiRange
        :min="0"
        :max="30"
        :step="1"
        years
        single
        @getValue="getValue"
      />
    </form>
    <div class="form-calc__submit-result">
      <div class="form-calc__result">
        <div class="form-calc__result-header">
          <a
            class="form-calc__result-link"
            href="#"
            target="_blank"
            rel="noopener noreferrer"
            >Узнайте о других интересных предложениях</a
          >
        </div>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 871 317"
          fill="none"
        >
          <path
            d="M0 30.8125C0 14.244 13.4315 0.8125 30 0.8125L521.257 0.8125C531.391 0.8125 540.839 5.92823 546.379 14.4138L552.121 23.2112C557.661 31.6968 567.109 36.8125 577.243 36.8125H841C857.569 36.8125 871 50.244 871 66.8125V286.812C871 303.381 857.569 316.812 841 316.812H30C13.4314 316.812 0 303.381 0 286.812L0 30.8125Z"
            fill="#083E4C"
          />
        </svg>
        <div class="form-calc__big-badge">Ипотека {{ 0.1 }}%</div>
        <div class="form-calc__conditions">
          <div class="form-calc__conditions-item">
            <p class="form-calc__conditions-item-heading">Ежемесячный платёж</p>
            <div class="form-calc__conditions-item-value">12 591 ₽</div>
          </div>
          <div class="form-calc__conditions-item">
            <p class="form-calc__conditions-item-heading">Ставка</p>
            <div class="form-calc__conditions-item-value">0.1%</div>
          </div>
          <div class="form-calc__conditions-item">
            <p class="form-calc__conditions-item-heading">Сумма кредита</p>
            <div class="form-calc__conditions-item-value">4 465 050 ₽</div>
          </div>
          <div class="form-calc__conditions-item">
            <p class="form-calc__conditions-item-heading">Срок кредита</p>
            <div class="form-calc__conditions-item-value">5 лет</div>
          </div>
        </div>
      </div>
      <p class="form-calc__result-warning">
        Приведенные расчеты носят предварительный характер. Окончательный расчет
        суммы кредита и размер ежемесячного платежа производится банком после
        предоставления оценки платежеспособности клиента.
      </p>
      <div class="form-calc__submit">
        <AppButton fill>Подать заявку на точный расчёт</AppButton>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import MultiRange from "@/components/multi-range/MultiRange.vue";
import CheckBox from "@/components/checkbox/CheckBox.vue";
import Badge from "@/components/badge/AppBadge.vue";
import AppButton from "@/components/button/AppButton.vue";

const selected = ref([]);

const getValue = (e) => {
  console.log(e);
};
</script>

<style lang="scss" scoped>
.form-calc {
  display: flex;
  justify-content: space-between;
  gap: 39px;

  &__inputs {
    display: flex;
    margin: 34px 0;
    gap: 10px;
  }

  &__form {
    width: 420px;
    padding: 35px;
    border: 1px solid $green;
    border-radius: 50px;
  }

  &__label {
    margin: 0 0 13px 0;
    color: $gray;
    font-size: 14px;
    font-style: normal;
    font-weight: 500;
    line-height: 100%;
  }

  &__badge {
    margin: 0 0 13px 0;
  }

  &__init-payment {
    margin: 0 0 34px 0;
  }

  &__submit-result {
    display: flex;
    flex-direction: column;
    max-width: 872px;
  }

  &__result {
    display: flex;
    flex-direction: column;
    padding: 60px 40px 40px;
    position: relative;

    svg {
      // width: 100%;
      height: 100%;
      position: absolute;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      z-index: 10;
    }
  }

  &__result-header {
    display: flex;
    justify-content: flex-end;
    position: absolute;
    top: 10px;
    right: 0;
    z-index: 11;
  }

  &__result-link {
    font-size: 14px;
    font-style: normal;
    font-weight: 500;
    line-height: 100%;
    color: $gray;
  }

  &__big-badge {
    display: inline-flex;
    max-width: 482px;
    margin: 0 0 50px 0;
    padding: 12px 15px;
    background-color: $white;
    border-radius: 16px;
    font-size: 74px;
    font-style: normal;
    font-weight: 500;
    line-height: 110%;
    color: $green;
    z-index: 11;
  }

  &__result-warning {
    margin: 25px 0 40px 0;
    font-size: 14px;
    font-style: normal;
    font-weight: 500;
    line-height: 140%;
    color: $greenGray;
    z-index: 11;
  }

  &__conditions {
    display: flex;
    gap: 67px;
    z-index: 11;
  }

  &__conditions-item {
    display: flex;
    flex-direction: column;
    gap: 14px;
  }

  &__conditions-item-heading {
    font-family: Gilroy;
    font-size: 14px;
    font-style: normal;
    font-weight: 500;
    line-height: 100%;
    color: rgba(255, 255, 255, 0.7);
  }

  &__conditions-item-value {
    font-family: Gilroy;
    font-size: 30px;
    font-style: normal;
    font-weight: 500;
    line-height: 120%;
    color: $white;
  }
}
</style>
