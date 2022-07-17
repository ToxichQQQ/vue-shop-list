<template>
  <form @submit.prevent="addNewItem" class="form">
    <div class="input-container">
      <label class="input-label" for="item_name">Наименование товара<span class="mark">*</span></label>
      <input v-model="name" class="input" id="item_name" placeholder="Введите наименование товара"
             :class="{error: isValidName}"/>
      <p v-if="isValidName" class="error-text">Поле обязательно для ввода</p>
    </div>
    <div class="input-container">
      <label class="input-label" for="item_description">Описание товара</label>
      <textarea v-model="description" class="input textarea" id="item_description"
                placeholder="Введите описание товара"></textarea>
    </div>

    <div class="input-container">
      <label class="input-label" for="item_link">Ссылка на изображение товара<span class="mark">*</span></label>
      <input v-model="link" class="input" id="item_link" placeholder="Введите ссылку"   :class="{error: isValidLink}"/>
      <p v-if="isValidLink" class="error-text">Поле обязательно для ввода</p>
    </div>

    <div class="input-container">
      <label class="input-label" for="item_price">Цена товара<span class="mark">*</span></label>
      <input v-model="formattedPrice" class="input" id="item_price" placeholder="Введите цену"   :class="{error: isValidPrice}"/>
      <p v-if="isValidPrice" class="error-text">Поле обязательно для ввода</p>
    </div>
    <div class="button-container">
      <button :disabled="isDisabledButton" class="form-button" type="submit">Добавить товар</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "AddForm",
  data() {
    return {
      errors: [],
      name: '',
      description: '',
      link: '',
      price: ''
    }
  },
  methods: {
    addNewItem() {
      const newItem = {
        id: Date.now(),
        name: this.name,
        description: this.description,
        link: this.link,
        price: this.price
      }
      this.$emit('add-new-item', newItem)

      this.name = ''
      this.description = ''
      this.link = ''
      this.price = ''

    },
    checkValidForm() {

      this.errors = []

      if (this.name && this.link && this.price) {
        return false
      }


      if (!this.name) {
        this.errors = [...this.errors, 'name']
      }

      if (!this.price) {
        this.errors = [...this.errors, 'price']
      }

      if (!this.link) {
        this.errors = [...this.errors, 'link']
      }

      return true
    }
  },
  watch: {
    name () {
      this.checkValidForm()
    },
    link () {
      this.checkValidForm()
    },
    price () {
      this.checkValidForm()
    },
  },
  computed: {
    isValidName() {
      return this.errors.find(item => item === 'name')
    },
    isValidLink () {
      return this.errors.find(item => item === 'link')
    },
    isValidPrice () {
      return this.errors.find(item => item === 'price')
    },
    isDisabledButton () {
      return !(this.name && this.price && this.link)
    },
    formattedPrice:{
      get(){
        return this.price
      },
      set(value){
        const newValue = value.replace(/\s/g, '').replace(/\D+/g, "")
        this.price =  Number(newValue).toLocaleString('ru')
      },
    }
  }
}
</script>
<style lang="scss" scoped>
@import "src/assets/variables.scss";

.form {
  width: 332px;
  padding: 24px;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: $border-radius-main;
  background-color: $bg-color
}

.input-container {
  margin-bottom: 16px;
  position: relative;
}

.input-label {
  margin-bottom: 4px;
  font-size: 10px;
  font-weight: $weight-main;
  display: block;
}

.input {
  display: block;
  width: 100%;
  padding: 10px 0 10px 16px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  border: none;
  border-radius:  $border-radius-main;
  font-size: 12px;
  color: $text-color;
  font-family: 'Source Sans Pro', Avenir, Helvetica, Arial, sans-serif;
}

.input[aria-placeholder] {
  color: $placeholder-color;
}

.input:focus-visible {
  outline: none;
}

.input:last-child {
  margin-bottom: 24px;
}

.textarea {
  height: 108px;
  resize: none;
}

.button-container {
  display: flex;
  justify-content: center;
}

.form-button {
  width: 100%;
  padding: 10px 0;
  border-radius:  $border-radius-button;
  background-color: $button-bg;
  color: $button-text;
  border: none;
  cursor: pointer;
  transition: background-color, color 100ms ease;
}

.form-button:disabled {
  background-color: $button-disabled-bg;
  color: $button-disabled-text;
}
.error{
  outline: 1px solid $error-color;
}
.mark{
  color: $error-color;
}
.error-text{
  color:  $error-color;
  font-size: 8px;
  position: absolute;
  margin: 4px 0 0;
}
@media (min-width: 1390px) {
  .form{
    position: fixed;
  }
}

</style>