<template>
  <div class="button-block">
    <button class="button-block__button" @click="changeVisibility">
      <svg viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg">
        <path d="M3 9.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3zm5 0a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3zm5 0a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3z"/>
      </svg>  
    </button>
    <div v-show="isVisible" class="button-block__options options">
      <ul class="options__list">
        <li @click="openModal" class="options__item">Подробнее</li>
        <li @click="toShipment" class="options__item options__item_color_green">К отгрузке</li>
        <li @click="deleteOrder" class="options__item options__item_color_red">Отменить</li>
      </ul>
    </div>
  </div>
</template>

<script>


export default {
  name: 'OrderOptions',
  props: ['order_id'],
  data() {
    return {
      isVisible: false,
    }
  },
  methods: {
    changeVisibility: function() {
      this.isVisible = !this.isVisible;
    },
    openModal: function() {
      this.$emit("openModal", this.order_id);
      this.changeVisibility();
    }, 
    toShipment: function() {
      this.$emit("toShipment", this.order_id);
      this.changeVisibility();
    },
    deleteOrder: function() {
      this.$emit("deleteOrder", this.order_id);
      this.changeVisibility();
    },
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .options {
    background: var(--background-color);
    z-index: 2;
    border: 2px var(--text-and-stroke-color) solid;
    border-radius: 5px;
    &__list {
    }
    &__item {
      cursor: pointer;
      text-align: center;
      padding: 5px 15px;
      border-bottom: 2px var(--text-and-stroke-color) solid;
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
      transform: translate(33%, 90%);
    }
    &__button {
      cursor: pointer;
      background: none;
      background-color: none;
      width: 40px;
      height: 40px;
      border: 2px var(--text-and-stroke-color) solid;
      border-radius: 10px;
      &>svg {
        width: 25px;
        height: 25px;
        fill: var(--text-and-stroke-color);
      }
    }
  }
</style>
