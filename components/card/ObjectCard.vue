<template>
  <div class="card">
    <div class="card__img-wrapper">
      <img class="card__img" :src="src" alt="" />
    </div>
    <svg
      id="mask"
      class="card__gradient"
      xmlns="http://www.w3.org/2000/svg"
      width="100%"
      height="303"
      viewBox="0 0 420 303"
      fill="none"
    >
      <path
        d="M0.458642 27.1687C0.481522 13.4179 11.6053 2.26692 25.356 2.21049L366 0.8125L395.694 1.63734C409.226 2.01322 420 13.0909 420 26.6277V39.3125V204.312C420 218.12 408.807 229.312 395 229.312H385C364.013 229.312 347 246.326 347 267.312V277.812C347 291.62 335.807 302.812 322 302.812H25.0416C11.2183 302.812 0.018666 291.594 0.0416665 277.771L0.458642 27.1687Z"
        fill="url(#paint0_linear_1_1862)"
        fill-opacity="0.7"
      />
      <defs>
        <linearGradient
          id="paint0_linear_1_1862"
          x1="172"
          y1="294.812"
          x2="172"
          y2="121.813"
          gradientUnits="userSpaceOnUse"
        >
          <stop offset="0.500753" />
          <stop offset="1" stop-opacity="0" />
        </linearGradient>
      </defs>
    </svg>
    <AppBadge class="card__badge" bg-color="#FFF" color="#545863">{{
      badgeName
    }}</AppBadge>
    <div class="card__footer">
      <div class="card__text">{{ text }}</div>
      <AppButton class="card__button" circle fill circle-play> </AppButton>
    </div>
  </div>
</template>

<script setup>
import AppBadge from "@/components/badge/AppBadge.vue";
import AppButton from "@/components/button/AppButton.vue";

defineProps({
  src: String,
  alt: String,
  text: String,
  badgeName: String,
});
</script>

<style lang="scss" scoped>
.card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-start;
  max-width: 420px;
  height: 302px;
  padding: 20px 0 0 20px;
  position: relative;
  background-color: $white;

  &:hover {
    img {
      transform: scale(1.1);
      transition: all 0.5s ease-in-out;
    }
  }

  &__img-wrapper {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    mask-image: url("/static/img-1.png");
    mask-repeat: no-repeat;
    -webkit-mask-image: url("/static/img-1.png");
    -webkit-mask-repeat: no-repeat;
  }

  &__img {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 0;
    transition: all 0.5s ease-in-out;
    object-fit: cover;
  }

  &__badge {
    font-size: 26px;
    font-style: normal;
    font-weight: 500;
    line-height: 130%;
    z-index: 10;
  }

  &__footer {
    display: flex;
    justify-content: space-between;
  }

  &__text {
    margin: 0 0 44px 0;
    font-size: 16px;
    font-style: normal;
    font-weight: 500;
    line-height: 140%;
    color: $white;
    position: relative;

    &::after {
      content: "";
      width: 100%;
      max-width: 316px;
      height: 1px;
      background-color: $white;
      position: absolute;
      top: -18px;
      left: 0;
    }
  }

  &__button {
    align-self: flex-end;
  }

  &__gradient {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
  }
}
</style>
