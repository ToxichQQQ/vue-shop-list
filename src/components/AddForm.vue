<template>
  <form class="form">
    <div class="input-container">
    <label class="input-label" for="item_name">Наименование товара</label>
    <input class="input" id="item_name" placeholder="Введите наименование товара"/>
    </div>

    <div class="input-container">
    <label class="input-label" for="item_description">Описание товара</label>
    <textarea class="input textarea" id="item_description" placeholder="Введите описание товара"></textarea>
    </div>

    <div class="input-container">
    <label class="input-label" for="item_link">Ссылка на изображение товара</label>
    <input class="input" id="item_link" placeholder="Введите ссылку"/>
    </div>

    <div class="input-container">
    <label class="input-label" for="item_price">Цена товара</label>
    <input class="input" id="item_price" placeholder="Введите цену"/>
    </div>

    <div class="button-container">
      <button class="form-button" type="submit">Добавить товар</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "AddForm"
}
</script>

<style scoped>
.form{
  padding: 24px;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  background-color: #FFFEFB;
}
  .input-container{
    margin-bottom: 16px;
  }
  .input-label{
    margin-bottom: 4px;
    font-size: 10px;
    font-weight: 400;
    display: block;
  }
  .input{
    display: block;
    width: 284px;
    padding: 10px 0 10px 16px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    border: none;
    border-radius: 4px;
    font-size: 12px;
    color: #B4B4B4;
    font-family: 'Source Sans Pro', Avenir, Helvetica, Arial, sans-serif;
  }
  .input:last-child{
    margin-bottom: 24px;
  }
  .textarea{
    height: 108px;
    resize: none;
  }
  .button-container{
    display: flex;
    justify-content: center;
  }
  .form-button{
    width: 100%;
    padding: 10px 0;
    border-radius: 10px;
    background-color: #EEE;
    border: none;
  }
</style>