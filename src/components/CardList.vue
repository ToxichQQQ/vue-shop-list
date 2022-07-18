<template>
  <ul class="list">
    <transition-group name="list">
      <TheLoader v-if="loading" />
      <ListItem
        v-for="item in items"
        :key="item.id"
        :item="item"
        @delete-item="deleteItem"
      />
    </transition-group>
  </ul>
</template>

<script>
import ListItem from "@/components/ListItem";
import TheLoader from "@/components/TheLoader";

export default {
  name: "CardList",
  components: { TheLoader, ListItem },
  props: {
    items: Array,
    loading: Boolean,
  },
  methods: {
    deleteItem(id) {
      this.$emit("delete-item", id);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "src/assets/variables.scss";

.list {
  margin: 0;
  padding-left: 16px;
  list-style-type: none;

  display: flex;
  flex-wrap: wrap;
}
.list-enter-active,
.list-leave-active {
  transition: all 2s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}

@media (max-width: 680px) {
  .list {
    padding-left: 0;
  }
}
</style>
