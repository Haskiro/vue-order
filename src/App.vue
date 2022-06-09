<template>
  <div id="app">
    <header class="header container">
      <div class="header__body">
        <h1 class="header__title">Vue: order</h1>
        <div class="header__switcher switcher">
          <p class="switcher__text">Темная тема</p>
          <div class="switcher__icon icon-switcher">
            <div class="icon-switcher__circle"></div>
          </div>
        </div>
      </div>
    </header>
    <main class="main container">
      <section class="column">
        <div class="column__header">
          <h2 class="column__title">Заказы</h2>
          <div class="column__refresh-btn column__refresh-btn_position_right">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
              <title>refresh</title>
              <g id="Layer_2" data-name="Layer 2">
                  <g id="refresh">
                      <g id="refresh-2" data-name="refresh">
                          <path id="refresh-btn" d="M20.3,13.43a1,1,0,0,0-1.25.65A7.14,7.14,0,0,1,12.18,19,7.1,7.1,0,0,1,5,12a7.1,7.1,0,0,1,7.18-7,7.26,7.26,0,0,1,4.65,1.67l-2.17-.36a1,1,0,0,0-1.15.83,1,1,0,0,0,.83,1.15l4.24.7h.17a1,1,0,0,0,.34-.06.33.33,0,0,0,.1-.06.78.78,0,0,0,.2-.11l.09-.11c0-.05.09-.09.13-.15s0-.1.05-.14a1.34,1.34,0,0,0,.07-.18l.75-4a1,1,0,0,0-2-.38l-.27,1.45A9.21,9.21,0,0,0,12.18,3,9.1,9.1,0,0,0,3,12a9.1,9.1,0,0,0,9.18,9A9.12,9.12,0,0,0,21,14.68,1,1,0,0,0,20.3,13.43Z"/>
                      </g>
                  </g>
              </g>
            </svg>
          </div>
        </div>
        <order-list></order-list>
        <modal-window></modal-window>
      </section>
      <section class="column">
        <div class="column__header">
          <h2 class="column__title">Отгрузки</h2>
          <div class="column__refresh-btn column__refresh-btn_position_left">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
              <title>refresh</title>
              <g id="Layer_2" data-name="Layer 2">
                  <g id="refresh">
                      <g id="refresh-2" data-name="refresh">
                          <path id="refresh-btn" d="M20.3,13.43a1,1,0,0,0-1.25.65A7.14,7.14,0,0,1,12.18,19,7.1,7.1,0,0,1,5,12a7.1,7.1,0,0,1,7.18-7,7.26,7.26,0,0,1,4.65,1.67l-2.17-.36a1,1,0,0,0-1.15.83,1,1,0,0,0,.83,1.15l4.24.7h.17a1,1,0,0,0,.34-.06.33.33,0,0,0,.1-.06.78.78,0,0,0,.2-.11l.09-.11c0-.05.09-.09.13-.15s0-.1.05-.14a1.34,1.34,0,0,0,.07-.18l.75-4a1,1,0,0,0-2-.38l-.27,1.45A9.21,9.21,0,0,0,12.18,3,9.1,9.1,0,0,0,3,12a9.1,9.1,0,0,0,9.18,9A9.12,9.12,0,0,0,21,14.68,1,1,0,0,0,20.3,13.43Z"/>
                      </g>
                  </g>
              </g>
            </svg>
          </div>
        </div>
        <shipment-list></shipment-list>
      </section>
    </main>
    <footer class="footer container">
      <div class="footer__body">
        <p class="footer_text">Кондратьев Павел Евгеньевич, 211-321</p>
        <button class="scroll-btn">
          <svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
            viewBox="0 0 100 100" style="enable-background:new 0 0 100 100;" xml:space="preserve">
            <path 
              d="M51.6,97.1V9.5l7.6,7.7c1,1,2.6,1,3.5,0l0,0c1-1,1-2.6,0-3.5l-13-12.9c-0.4-0.4-1-0.4-1.4,0l-13,12.9c-1,1-1,2.6,0,3.5l0,0
              c1,1,2.6,1,3.5,0l7.6-7.7v87.6c0,1.4,1.1,2.5,2.5,2.5l0,0C50.5,99.6,51.6,98.5,51.6,97.1z"
            />
          </svg>
        </button>
      </div>
    </footer>
  </div>
</template>

<script>
import OrderList from './components/OrderList.vue'
import ShipmentList from './components/ShipmentList.vue'
import ModalWindow from './components/Modal.vue'
import '../public/styles/styles.scss'
export default {
  name: 'App',
  components: {
    OrderList,
    ShipmentList,
    ModalWindow,
    
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  // text-align: center;
  // color: #2c3e50;
  // margin-top: 60px;
}
</style>
