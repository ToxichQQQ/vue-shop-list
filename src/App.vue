<template>
  <TheHeader/>
  <div class="parent">
    <div class="div1">
        <AddForm/>
    </div>
    <div class="div2">
      <CardList :items="this.cardList"/>
    </div>
  </div>
</template>

<script>
import TheHeader from "@/components/TheHeader";
import AddForm from "@/components/AddForm";
import CardList from "@/components/CardList";

export default {
  name: 'App',
  components: {
    CardList,
    AddForm,
    TheHeader,
  },
  data() {
    return {
      cardList: [{
        id: '1',
        name: 'Наименование товара',
        description: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        img: '/images/item.png',
        price: '10000'
      },{
        id: '1',
        name: 'Наименование товара',
        description: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        img: '/images/item.png',
        price: '10000'
      },{
        id: '1',
        name: 'Наименование товара',
        description: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        img: '/images/item.png',
        price: '10000'
      }]
    }
  },
}
</script>

<style>
#app {
  font-family: 'Source Sans Pro',Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 32px;
}
.parent {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(2, 1fr);
  grid-column-gap: 0px;
  grid-row-gap: 0px;
}

.div1 { grid-area: 1 / 1 / 3 / 2; }
.div2 { grid-area: 1 / 2 / 3 / 5; }
</style>
