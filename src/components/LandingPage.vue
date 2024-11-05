<template>
  <div class="landing-page">
    <div class="landing-page__left-side"></div>
    <div class="landing-page__right-side">
        <MortgageCalculator></MortgageCalculator>
    </div>
  </div>
</template>
<script lang="ts" setup>
import MortgageCalculator from './MortgageCalculator.vue';
</script>
<style lang="scss">
.landing-page{
    padding: 5px;
    border-radius: 15px;
    display: flex;
    flex-direction: row;
    $self: &;
    &__right-side {
        width: 75%;
        background-color: white;
        border-radius: 15px;
        
    }
    &__left-side {
        width: 25%;
        border-radius: 15px;
        margin-right: 5px;
        background-color: #bddcef;
        opacity: 0.1;
        background-image: radial-gradient(circle at center center, #d9b1ef, #bddcef), repeating-radial-gradient(circle at center center, #d9b1ef, #bddcef, 4px, transparent 8px, transparent 4px);
        background-blend-mode: multiply;
    }

   
}
</style>