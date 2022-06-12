<template>
  <div id="app" v-bind:class="{ modalIsOpen: modalIsVisible }">
    <header class="header container">
      <div class="header__body">
        <h1 class="header__title">Vue: order</h1>
        <div class="header__switcher switcher">
          <p class="switcher__text">Темная тема</p>
          <div class="switcher__icon icon-switcher">
            <div class="icon-switcher__circle" @click="changeTheme" v-bind:class="{ active: darkTheme }"></div>
          </div>
        </div>
      </div>
    </header>
    <main class="main container">
      <section class="column">
        <order-list @openModal="openModal" @dragOrder="dragOrder"></order-list>
        <modal-window v-show="modalIsVisible" @closeModal="modalVisibilityToggle"
        :modal="modal" :modalOrders="modalOrders">
        </modal-window>
      </section>
      <section class="column" @drop="onDrop" @dragover.prevent @dragenter.prevent>
        <shipment-list></shipment-list>
      </section>
    </main>
    <footer class="footer container">
      <div class="footer__body">
        <p class="footer_text">Кондратьев Павел Евгеньевич, 211-321</p>
        <a class="scroll-btn" href="#">
          <svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
            viewBox="0 0 100 100" style="enable-background:new 0 0 100 100;" xml:space="preserve">
            <path 
              d="M51.6,97.1V9.5l7.6,7.7c1,1,2.6,1,3.5,0l0,0c1-1,1-2.6,0-3.5l-13-12.9c-0.4-0.4-1-0.4-1.4,0l-13,12.9c-1,1-1,2.6,0,3.5l0,0
              c1,1,2.6,1,3.5,0l7.6-7.7v87.6c0,1.4,1.1,2.5,2.5,2.5l0,0C50.5,99.6,51.6,98.5,51.6,97.1z"
            />
          </svg>
        </a>
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
      darkTheme: false,
      order_dragged: '',
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
    },
    changeTheme: function() {
      this.darkTheme = !this.darkTheme;
      document.getElementById('html').classList.toggle('dark-theme');
    },
    dragOrder: function(order_id) {
      this.order_dragged = order_id;
    },
    onDrop: async function() {
      await fetch(`https://justcors.com/tl_26283e1/demo-api.vsdev.space/api/orders_admin/2021-0637/orders/${this.order_dragged}/delivery`, {
        method: 'POST',
      });
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
