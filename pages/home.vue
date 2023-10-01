<template>
  <div class="app">
    <header class="app__header">
      <h1>Варианты покупки</h1>
      <div class="app__header-buttons">
        <AppButton class="app__header-button">Подробнее</AppButton>
        <AppButton
          class="app__header-button"
          circle
          arrow-left
          disabled
        ></AppButton>
        <AppButton class="app__header-button" circle arrow-right></AppButton>
      </div>
    </header>
    <div class="app__cards">
      <ObjectCard
        src="/static/img-1.png"
        text="Выгодные условия при оформлении у банков-партнеров"
        badge-name="Ипотека от 4,3%"
      />
      <ObjectCard
        src="/static/img-1.png"
        text="Выгодные условия при оформлении у банков-партнеров"
        badge-name="Рассрочка 0%"
        v-motion
        :initial="initial"
        :enter="enter"
      />
      <ObjectCard
        src="/static/img-1.png"
        text="Выгодные условия при оформлении у банков-партнеров"
        badge-name="Покупка в Trade-in"
        v-motion
        :initial="initial2"
        :enter="enter2"
      />
    </div>
    <FormCalc v-motion :initial="initial2" :enter="enter2" />
  </div>
</template>

<script setup>
import AppButton from "@/components/button/AppButton.vue";
import ObjectCard from "@/components/card/ObjectCard.vue";

const initial = ref({
  y: 80,
  opacity: 0,
});

const enter = ref({
  y: 0,
  opacity: 1,
  transition: {
    stiffness: "20",
  },
});

const initial2 = ref({
  y: 100,
  opacity: 0,
});

const enter2 = ref({
  y: 0,
  opacity: 1,
  transition: {
    stiffness: "20",
    delay: "80",
  },
});
</script>

<style lang="scss">
.app {
  width: 100%;
  max-width: 1440px;
  margin: 0 auto;
  padding: 55px;

  &__header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0 0 36px 0;

    &-button {
      &:nth-child(2) {
        margin: 0 12px 0 20px;
      }
    }
  }

  &__header-buttons {
    display: flex;
  }

  &__cards {
    display: flex;
    justify-content: space-between;
    margin: 0 0 75px 0;
    gap: 36px;
  }
}
</style>
