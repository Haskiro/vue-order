<template>
  <div class="orders">
    <div class="column__header">
      <h2 class="column__title">Заказы</h2>
      <div v-on:click="refreshOrderList" class="column__refresh-btn column__refresh-btn_position_right">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
          <title>Обновить</title>
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
    <ul class="orders__list">
      <li v-for="order in orders" :key="order.id" class="orders__item order" draggable="true" @dragstart="startDrag(order.id)">
        <p class="order__name">Заказ #{{ order.id }}</p>
        <div class="order__block">
          <p class="order__price">{{ order.total }}руб</p>
          <order-options :order_id="order.id"  @openModal="openModal" @toShipment="addOrderToShipments" @deleteOrder="deleteOrder"></order-options>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import OrderOptions from './OrderOptions.vue'

export default {
  name: 'OrderList',
  props: ["orders"],
  components: {
    OrderOptions,
  },
  data() {
    return {
      showOption: false,
      modal: {},
    }
  },
  methods: {
    refreshOrderList: function() {
      this.$emit("refreshOrderList", null);
    },
    getOrderDetails: async function(order_id) {
      const response = await fetch(`https://justcors.com/tl_6550159/demo-api.vsdev.space/api/orders_admin/2021-0637/orders/${order_id}`, {
        method: 'GET',
      });
      return response.json();
    },
    openModal: function(order_id) {
      this.getOrderDetails(order_id).then((data) => {
        this.modal = data
        this.$emit("openModal", this.modal);
      });
    }, 
    addOrderToShipments: async function(order_id) {
      await fetch(`https://justcors.com/tl_6550159/demo-api.vsdev.space/api/orders_admin/2021-0637/orders/${order_id}/delivery`, {
        method: 'POST',
      });
    },
    deleteOrder: async function(order_id) {
      await fetch(`https://demo-api.vsdev.space/api/orders_admin/2021-0637/orders/${order_id}`, {
        method: 'DELETE',
      }).then(() => {this.refreshOrderList()});
    },
    startDrag: function(order_id) {
      this.$emit("dragOrder", order_id);
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .orders {
    &__list {
      padding: 15px;
		}
		&__item {
      margin-bottom: 40px;
		}
  }
  .order {
    border: 2px var(--text-and-stroke-color) solid;
    border-radius: 10px;
    display: flex;
    justify-content: space-between;
    padding: 15px;
    &__name {
      align-self: center;
    }
    &__block {
      align-items: center;
      display: flex;
      gap: 15px;
    }
    &__price {
    }
  }
</style>
