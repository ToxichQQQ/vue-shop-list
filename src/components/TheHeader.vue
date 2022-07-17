<template>
  <header class="header-container">
    <h1 class="header-title">Добавление товара</h1>
    <select class="header-filter" @change="setFilter">
      <option value="default">По умолчанию</option>
      <option value="min">По цене min</option>
      <option value="max"> По цене max</option>
      <option value="name">По наименованию</option>
    </select>
  </header>
</template>

<script>
export default {
  name: "TheHeader",
  methods:{
    setFilter(event){
      this.$emit('set-filter',event.target.value)
    }
  }
}
</script>

<style lang="scss" scoped>
@import "src/assets/variables.scss";

.header-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 16px;
}

.header-title {
  margin: 0;
  font-size: 28px;
  font-weight: $weight-semi-bold;
}

.header-filter {
  padding: 10px 16px;
  color: $header-text;
  font-size: 12px;
  font-weight: $weight-main;
  border: none;
  border-radius: $border-radius-main;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

@media (max-width: 450px) {
  .header-container {
    flex-direction: column;
  }
}
</style>