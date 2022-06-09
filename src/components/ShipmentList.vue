<template>
  <div class="shipments">
    <ul class="shipments__list">
      <li class="shipments__item shipment">
        <div class="shipment__block-id">
          <p class="shipment__name">Отгрузка #123</p>
          <p class="shipment__order-name">Заказ #123</p>
        </div>
        <div class="shipment__block">
          <p class="shipment__date">10.06.2022</p>
          <button class="shipment__button">
            <svg viewBox="0 0 16 16" class="bi bi-three-dots" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
              <path fill-rule="evenodd" d="M3 9.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3zm5 0a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3zm5 0a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3z"/>
            </svg>  
          </button>
          <div class="shipment__additional additional">
            <ul class="additional__list">
              <li class="additional__item additional__item_color_red">Отменить</li>
            </ul>
          </div>
        </div>
      </li>
      <li class="shipments__item shipment">
        <div class="shipment__block-id">
          <p class="shipment__name">Отгрузка #123</p>
          <p class="shipment__order-name">Заказ #123</p>
        </div>
        <div class="shipment__block">
          <p class="shipment__date">10.06.2022</p>
          <button class="shipment__button">
            <svg viewBox="0 0 16 16" class="bi bi-three-dots" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
              <path fill-rule="evenodd" d="M3 9.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3zm5 0a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3zm5 0a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3z"/>
            </svg>  
          </button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ShipmentList',
  props: {
    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .shipments {
    &__list {
      padding: 15px;
		}
		&__item {
      margin-bottom: 20px;
		}
  }
  .shipment {
    border: 2px black solid;
    border-radius: 10px;
    display: flex;
    justify-content: space-between;
    position: relative;
    padding: 15px;
    &__name {
      align-self: center;
      font-size: 1.2rem;
      line-height: 1.3;
    }
    &__order-name{

    }
    &__block-id {
      display: flex;
      gap: 15px;
      align-items: center;
    }
    &__block {
      align-items: center;
      display: flex;
      gap: 15px;
    }
    &__date {
    }
    &__button {
      cursor: pointer;
      background: none;
      background-color: none;
      width: 40px;
      height: 40px;
      border: 2px black solid;
      border-radius: 10px;
      &>svg {
        width: 25px;
        height: 25px;
      }
    }
    &__additional {
      position: absolute;
      bottom: 0;
      right: 0;
      transform: translate(18%, 70%);
    }
  }
  .additional {
    background: white;
    z-index: 2;
    border: 2px black solid;
    border-radius: 5px;
    &__list {
    }
    &__item {
      cursor: pointer;
      text-align: center;
      padding: 10px 15px;
      border-bottom: 2px black solid;
      &:nth-last-child(-n+1) {
        border-bottom: none;
      }
      &_color_red {
        color: red;
      }
      &_color_green {
        color: green;
      }
    }
  }
</style>
