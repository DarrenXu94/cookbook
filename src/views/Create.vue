<template>
  <div class="create">
    <div class="create__form">
      <input type="text" v-model="title" placeholder="edit me" />
      <textarea v-model="ingredients" placeholder="add multiple lines"></textarea>
      <textarea v-model="directions" placeholder="add multiple lines"></textarea>
      <a href class="btn-secondary">Submit</a>
    </div>
  </div>
</template>

<script>
export default {
  name: "Create",
  data() {
    return {
      title: "",
      ingredients: "",
      directions: ""
    };
  }
};
</script>

<style lang="scss" scoped>
.create {
  padding: 1rem;
  .create__form {
    max-width: 500px;
    padding: 10px 20px;
    background: #f4f7f8;
    margin: 10px auto;
    padding: 20px;
    background: #f4f7f8;
    border-radius: 8px;
  }
  .create__form fieldset {
    border: none;
  }
  .create__form legend {
    font-size: 1.4em;
    margin-bottom: 10px;
  }
  .create__form label {
    display: block;
    margin-bottom: 8px;
  }
  .create__form input[type="text"],
  .create__form input[type="date"],
  .create__form input[type="datetime"],
  .create__form input[type="email"],
  .create__form input[type="number"],
  .create__form input[type="search"],
  .create__form input[type="time"],
  .create__form input[type="url"],
  .create__form textarea,
  .create__form select {
    background: rgba(255, 255, 255, 0.1);
    border: none;
    border-radius: 4px;
    font-size: 15px;
    margin: 0;
    outline: 0;
    padding: 10px;
    width: 100%;
    box-sizing: border-box;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    background-color: #e8eeef;
    color: #8a97a0;
    -webkit-box-shadow: 0 1px 0 rgba(0, 0, 0, 0.03) inset;
    box-shadow: 0 1px 0 rgba(0, 0, 0, 0.03) inset;
    margin-bottom: 30px;
  }
  .create__form input[type="text"]:focus,
  .create__form input[type="date"]:focus,
  .create__form input[type="datetime"]:focus,
  .create__form input[type="email"]:focus,
  .create__form input[type="number"]:focus,
  .create__form input[type="search"]:focus,
  .create__form input[type="time"]:focus,
  .create__form input[type="url"]:focus,
  .create__form textarea:focus,
  .create__form select:focus {
    background: #d2d9dd;
  }
  .create__form select {
    -webkit-appearance: menulist-button;
    height: 35px;
  }
  .create__form .number {
    background: #1abc9c;
    color: #fff;
    height: 30px;
    width: 30px;
    display: inline-block;
    font-size: 0.8em;
    margin-right: 4px;
    line-height: 30px;
    text-align: center;
    text-shadow: 0 1px 0 rgba(255, 255, 255, 0.2);
    border-radius: 15px 15px 15px 0px;
  }

  .create__form input[type="submit"],
  .create__form input[type="button"] {
    position: relative;
    display: block;
    padding: 19px 39px 18px 39px;
    color: #fff;
    margin: 0 auto;
    background: #1abc9c;
    font-size: 18px;
    text-align: center;
    font-style: normal;
    width: 100%;
    border: 1px solid #16a085;
    border-width: 1px 1px 3px;
    margin-bottom: 10px;
  }
  .create__form input[type="submit"]:hover,
  .create__form input[type="button"]:hover {
    background: #109177;
  }
}
</style>