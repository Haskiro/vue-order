<template>
  <div class="button-block">
    <button class="button-block__button" @click="changeVisibility">
      <svg viewBox="0 0 16 16" class="bi bi-three-dots" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
        <path fill-rule="evenodd" d="M3 9.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3zm5 0a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3zm5 0a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3z"/>
      </svg>  
    </button>
    <div class="button-block__options options" v-show="isVisible">
      <ul class="options__list">
        <li class="options__item options__item_color_red">Отменить</li>
      </ul>
    </div>
  </div>
</template>

<script>


export default {
  name: 'OrderOptions',
  data() {
    return {
      modal: {},
      isVisible: false,
    }
  },
  methods: {
    getOrderInformation: async function(order_id) {
      const response = await fetch(`https://demo-api.vsdev.space/api/orders_admin/2021-0637/orders/${order_id}`, {
        method: 'GET',
      });
      return response.json();
    },
    updateModal: function() {
      this.getOrderInformation().then((data) => {this.modal = data});
    },
    changeVisibility: function() {
      this.isVisible = !this.isVisible;
    },
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .options {
    background: white;
    z-index: 2;
    border: 2px black solid;
    border-radius: 5px;
    &__list {
    }
    &__item {
      cursor: pointer;
      text-align: center;
      padding: 5px 15px;
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
  .button-block {
    position: relative;
    &__options {
      position: absolute;
      bottom: 0;
      right: 0;
      transform: translate(33%, 100%);
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
  }
</style>
