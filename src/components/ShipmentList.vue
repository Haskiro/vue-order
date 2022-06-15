<template>
  <div class="shipments">
    <div class="column__header">
      <h2 class="column__title">Отгрузки</h2>
      <div v-on:click="refreshShipmentList" class="column__refresh-btn column__refresh-btn_position_left">
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
    <ul class="shipments__list">
      <li v-for="shipment in shipments" :key="shipment.id" class="shipments__item shipment">
        <div class="shipment__block-id">
          <p class="shipment__name">Отгрузка #{{ shipment.id }}</p>
          <p class="shipment__order-name">Заказ #{{ shipment.order_id }}</p>
        </div>
        <div class="shipment__block">
          <p class="shipment__date">{{ shipment.delivery_date}}</p>
          <shipment-options :shipment_id="shipment.id" @deleteShipment="deleteShipment"></shipment-options>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import ShipmentOptions from './ShipmentOptions.vue'

export default {
  name: 'ShipmentList',
  components: {
    ShipmentOptions,
  },
  props: ["shipments"],  
  data() {
    return {
    }
  },
  methods: {
    deleteShipment: async function(shipment_id) {
      await fetch(`https://demo-api.vsdev.space/api/orders_admin/2021-0637/deliveries/${shipment_id}`, {
        method: 'DELETE',
      }).then(() => {this.refreshShipmentList()});
    },
    refreshShipmentList: function() {
      this.$emit("refreshShipmentList", null);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .shipments {
    &__list {
      padding: 15px 0px;
		}
		&__item {
      margin-bottom: 40px;
		}
  }
  .shipment {
    border: 2px var(--text-and-stroke-color) solid;
    border-radius: 10px;
    display: flex;
    justify-content: space-between;
    position: relative;
    padding: 15px;
    &__name {
      align-self: center;
    }
    &__order-name{
      font-size: 0.9rem;
      line-height: 1.2;

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
  }
</style>
