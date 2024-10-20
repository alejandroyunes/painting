<template>
  <div class="pricing">
    
    <div class="pricing__section">
      <h3 class="pricing__section-title">{{ $t('dogsCats') }}</h3>
      <ul class="pricing__list">
        <li class="pricing__item">
          <span class="pricing__item-name">{{ $t('fullColorHead') }}</span>
          <span class="pricing__item-price">{{ $t('price1') }}</span>
        </li>
        <li class="pricing__item">
          <span class="pricing__item-name">{{ $t('fullColorBody') }}</span>
          <span class="pricing__item-price">{{ $t('price1') }}</span>
        </li>
        <li class="pricing__item">
          <span class="pricing__item-name">{{ $t('oneColorHead') }}</span>
          <span class="pricing__item-price">{{ $t('price1') }}</span>
        </li>
        <li class="pricing__item">
          <span class="pricing__item-name">{{ $t('oneColorFullBody') }}</span>
          <span class="pricing__item-price">{{ $t('price1') }}</span>
        </li>
      </ul>
    </div>

    <div class="pricing__section">
      <h3 class="pricing__section-title">{{ $t('personWithPet') }}</h3>
      <ul class="pricing__list">
        <li class="pricing__item">
          <span class="pricing__item-name">{{ $t('fullColor') }}</span>
          <span class="pricing__item-price">{{ $t('price1') }}</span>
        </li>
        <li class="pricing__item">
          <span class="pricing__item-name">{{ $t('oneColor') }}</span>
          <span class="pricing__item-price">{{ $t('price2') }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PricingComponent'
}
</script>

<style lang="scss" scoped>
.pricing {
  font-family: Arial, sans-serif;
  color: #333;
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);

  &__title {
    font-size: 32px;
    line-height: 1.4;
    font-weight: bold;
    color: #10BEBA;
    text-align: center;
    margin-bottom: 20px;
  }

  &__description {
    font-size: 16px;
    line-height: 1.6;
    text-align: center;
    margin-bottom: 30px;
    color: #666;
  }

  &__section {
    margin-bottom: 30px;
    background-color: #fff;
    padding: 20px;
    border-radius: 6px;
    box-shadow: 0 1px 5px rgba(0, 0, 0, 0.05);
  }

  &__section-title {
    font-size: 24px;
    font-weight: bold;
    margin-bottom: 15px;
    color: #10BEBA;
    border-bottom: 2px solid #10BEBA;
    padding-bottom: 10px;
  }

  &__list {
    list-style-type: none;
    padding: 0;
  }

  &__item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 16px;
    line-height: 1.6;
    margin-bottom: 10px;
    padding: 10px;
    background-color: #f0f0f0;
    border-radius: 4px;
    transition: background-color 0.3s ease;

    &:hover {
      background-color: #e0e0e0;
    }
  }

  &__item-name {
    flex: 1;
    padding-right: 10px;
  }

  &__item-price {
    flex: 0 0 10px;
    text-align: right;
    font-weight: bold;
    color: #10BEBA;
    white-space: nowrap;
  }

  // Responsive styles
  @media (max-width: 600px) {
    padding: 15px;

    &__title {
      font-size: 28px;
    }

    &__description {
      font-size: 14px;
    }

    &__section-title {
      font-size: 20px;
    }

    &__item {
      flex-direction: column;
      align-items: flex-start;
    }

    &__item-name {
      margin-bottom: 5px;
    }

    &__item-price {
      align-self: flex-end;
    }
  }
}
</style>