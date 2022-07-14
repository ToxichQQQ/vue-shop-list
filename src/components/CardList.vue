<template>
  <ul class="list">
    <ListItem v-for="item in items" :key="item.id" :item="item"/>
  </ul>
</template>

<script>
import ListItem from "@/components/ListItem";

export default {
  name: "CardList",
  components: {ListItem},
  props:{
    items:Array
  }
}
</script>

<style scoped>
.list{
  margin: 0;
  padding-left: 16px;
  list-style-type: none;

  display: flex;
}
</style>