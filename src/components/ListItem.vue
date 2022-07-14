<template>
  <li class="item-container" @mouseover="mouseOver" @mouseleave="mouseLeave">
    <button class="delete-button" v-show="isActive" @click="deleteItem">
      <img src="../assets/delete.svg" alt="Delete Icon"/>
    </button>
    <img class="item-img" :src="item.link" alt="item_img"/>
    <div class="item-info">
      <h3 class="item-header">{{ item.name }}</h3>
      <p class="item-description">{{ item.description }}</p>
      <p class="item-price">{{ item.price }} руб.</p>
    </div>
  </li>
</template>

<script>
export default {
  name: "ListItem",
  props: {
    item: Object
  },
  data(){
    return{
      isActive:false
    }
  },
  methods:{
    mouseOver: function (){
      this.isActive = true
    },
    mouseLeave: function (){
      this.isActive = false
    },
    deleteItem: function (){
      this.$emit('delete-item',this.item.id)
    }
  }
}
</script>

<style scoped>
.item-container {
  cursor: pointer;
  position: relative;
  background-color: #FFFEFB;
  border-radius: 4px;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);
  margin: 0 16px 16px 0;
  flex: 0 1 347px;
  transition: all 1s ease;
}

.item-container:hover {
  transform: scale(1.05);
}

.item-container:nth-child(3n) {
  margin-right: 0;
}

.delete-button{
  background-color: #FF8484;
  border: none;
  border-radius: 10px;
  padding: 8px 10px;
  position: absolute;
  right: 0;
  top: -9px;
}
.item-img {
  border-radius: 4px 4px 0 0;
  width: 100%;
  max-height: 190px;
}

.item-info {
  padding: 12px 16px 16px;
  color: #3F3F3F;
  font-family: 'Source Sans Pro', Avenir, Helvetica, Arial, sans-serif;
}

.item-header {
  margin: 0;

  font-size: 20px;
  font-weight: 600;
}

.item-description {
  font-size: 16px;
  font-weight: 400;
  line-height: 20px;

}

.item-price {
  font-size: 24px;
  font-weight: 600;
}

@media (max-width: 680px) {
  .item-container {
    flex: 0 1 auto;
    margin: 10px 0 0;
  }
}

@media (min-width: 1068px) and (max-width: 1379px) {
  .item-container:nth-child(3n) {
    margin-right: 16px;
  }

  .item-container:nth-child(2n) {
    margin-right: 0;
  }
}

@media (min-width: 1813px) {
  .item-container:nth-child(3n) {
    margin-right: 16px;
  }

  .item-container:nth-child(4n) {
    margin-right: 0;
  }

  @media (min-width: 2251px) {
    .item-container:nth-child(4n) {
      margin-right: 16px;
    }

    .item-container:nth-child(5n) {
      margin-right: 0;
    }
  }
}
</style>