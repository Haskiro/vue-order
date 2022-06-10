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
        <order-list @openModal="openModal"></order-list>
        <modal-window v-show="modalIsVisible" @closeModal="modalVisibilityToggle"
        :modal="modal" :modalOrders="modalOrders">
        </modal-window>
      </section>
      <section class="column">
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
  data() {
    return {
      modalIsVisible: false,
      modal: {},
      modalOrders: [],
    }
  },
  components: {
    OrderList,
    ShipmentList,
    ModalWindow,
    
  },
  methods: {
    openModal: function(modal) {
      this.modalVisibilityToggle();
      this.modal = modal;
      this.modalOrders = modal.basket_items;
    },
    modalVisibilityToggle: function() {
      this.modalIsVisible = !this.modalIsVisible;
    }
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
