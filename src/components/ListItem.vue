<template>
  <li class="item-container">
    <img class="item-img" :src="item.img" alt="item_img"/>
    <div class="item-info">
      <h3 class="item-header">{{item.name}}</h3>
      <p class="item-description">{{item.description}}</p>
      <p class="item-price">{{item.price}} руб.</p>
    </div>
  </li>
</template>

<script>
export default {
  name: "ListItem",
  props:{
    item:Object
  }
}
</script>

<style scoped>
.item-container{
  background-color: #FFFEFB;
  border-radius: 4px;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);
  margin-right: 16px;
  flex: 0 1 33%;
  width: 332px;
}

.item-container:nth-child(3n){
  margin-right: 0;
}
.item-img{
  border-radius: 4px 4px 0 0;
  width: 100%;
}
.item-info{
  padding:12px 16px 16px;
  color:#3F3F3F;
  font-family: 'Source Sans Pro', Avenir, Helvetica, Arial, sans-serif;
}
.item-header{
  margin: 0;

  font-size: 20px;
  font-weight: 600;
}
.item-description{
  font-size: 16px;
  font-weight: 400;
  line-height: 20px;

}
.item-price{
  font-size: 24px;
  font-weight: 600;
}
</style>