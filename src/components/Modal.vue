<template>
  <div class="modal">
    <div class="modal__blackout">
      <div class="modal__window">
        <div class="modal__header">
          <p class="modal__title">Заказ #123</p>
          <button class="modal__close">
            x
          </button>
        </div>
        <div class="modal__body">
          <p class="modal__subtitle">Корзина</p>
          <ul class="modal__list">
            <li class="modal__item card">
              <p class="card__name">Товар первый</p>
              <div class="card__block">
                <p class="card__count">1 шт.</p>
                <div class="card__price">12,123.00 руб</div>
              </div>
            </li>
            <li class="modal__item card">
              <p class="card__name">Товар второй</p>
              <div class="card__block">
                <p class="card__count">3 шт.</p>
                <div class="card__price">22,123.00 руб</div>
              </div>
            </li>
          </ul>
          <div class="modal__total total">
            <p class="total__text">Итого:</p>
            <p class="total__price">34,246.00 руб</p>
          </div>
        </div>
        <div class="modal__footer">
          <button class="modal__btn modal__btn_color_green">К отгрузке</button>
          <button class="modal__btn modal__btn_color_red">Отменить</button>
          </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalWindow',
  props: {
    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .modal {
    display: none;
    width: 100vw;
    height: 100vh;
    position: fixed;
    z-index: 3;
    top: 0;
    left: 0;
		&__blackout {
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.4);
      padding-top: 150px;
		}
		&__window {
      width: 500px;
      margin: 0px auto;
      background: white;
      padding: 15px;
      border: 2px black solid;
      border-radius: 10px;
      
		}
		&__header {
      width: 100%;
      text-align: center;
      align-items: center;
      position: relative;
		}
		&__title {
      font-size: 1.5rem;
      line-height: 1.5;
		}
		&__close {
      cursor: pointer;
      position: absolute;
      right: 0;
      top: 50%;
      transform: translateY(-50%);
      font-size: 1.4rem;
      line-height: 1.2;
      background: none;
      border: 2px black solid;
      border-radius: 10px;
      width: 35px;
      height: 35px;

		}
		&__body {
		}
		&__subtitle {
      margin-bottom: 15px;
		}
		&__list {
      border: 2px black solid;
      border-radius: 10px;
		}
		&__item {
      border-bottom: 2px black solid;
      &:nth-last-child(-n+1) {
        border-bottom: none;
      }
		}
		&__total {
		}
		&__footer {
      display: flex;
      justify-content: space-between;
		}
		&__btn {
      background: none;
      border: 2px black solid;
      border-radius: 5px;
      font-size: 1.2rem;
      line-height: 1.3;
      padding: 5px 50px;
      cursor: pointer;
			&_color_red {
        color: red;
			}
			&_color_green {
        color: green;
			}
		}
}
.card {
    display: flex;
    justify-content: space-between;
    padding: 15px;
		&__name {
		}
		&__block {
      display: flex;
      gap: 20px;
		}
		&__count {
		}
		&__price {
		}
}
.total {
  padding: 20px 0px;
  display: flex;
  justify-content: right;
  gap: 15px;
  align-items: center;
		&__text {
      font-size: 1.3rem;
      line-height: 1.2;
		}
		&__price {
		}
}
</style>
