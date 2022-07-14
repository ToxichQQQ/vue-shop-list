<template>
  <TheHeader @set-filter="setFilter"/>
  <div class="parent">
    <div class="add-section">
      <AddForm @add-new-item="addNewItem"/>
    </div>
    <div class="list-section">
      <CardList :loading="loading" :items="filteredArray" @delete-item="deleteItem"/>
    </div>
  </div>
</template>

<script>
import TheHeader from "@/components/TheHeader";
import AddForm from "@/components/AddForm";
import CardList from "@/components/CardList";
import {itemsArray} from "@/constants";

export default {
  name: 'App',
  components: {
    CardList,
    AddForm,
    TheHeader,
  },
  data() {
    return {
      filter: 'default',
      loading: false,
      cardList: []
    }
  },
  methods: {
    addNewItem(item) {
      this.cardList = [...this.cardList, item]
      this.saveItems()
    },
    deleteItem(id) {
      this.cardList = this.cardList.filter(item => item.id !== id)
      this.saveItems()
    },
    setFilter(value) {
      this.filter = value
    },
    saveItems() {
      localStorage.setItem('cardList', JSON.stringify(this.cardList))
    },
  },
  computed: {
    filteredArray() {
      switch (this.filter) {
        case 'max':
          return this.cardList.slice().sort(function (a, b) {
            return Number(a.price.replace(/\s/g, '')) < Number(b.price.replace(/\s/g, '')) ? 1 : -1
          })
        case 'min':
          return this.cardList.slice().sort(function (a, b) {
            return Number(a.price.replace(/\s/g, '')) > Number(b.price.replace(/\s/g, '')) ? 1 : -1
          })
        case 'name':
          return this.cardList.slice().sort(function (a, b) {
            return a.name.toUpperCase() > b.name.toUpperCase() ? 1 : -1
          })
        default:
          return this.cardList
      }
    }
  },
  created() {
    this.loading = true
    setTimeout( () =>{
      if (localStorage.getItem('cardList')) {
        this.cardList = JSON.parse(localStorage.getItem('cardList'))
      }else {
        this.cardList = itemsArray
      }
      this.loading = false
    },2000)
  }
}
</script>

<style>
#app {
  font-family: 'Source Sans Pro', Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 32px;
}

.parent {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(4, 1fr);
  grid-column-gap: 0;
  grid-row-gap: 0;
}

.add-section {
  grid-area: 1 / 1 / 3 / 2;
}

.list-section {
  grid-area: 1 / 2 / 3 / 5;
}

@media (max-width: 680px) {
  .parent {
    display: flex;
    flex-direction: column;
  }
}
</style>
