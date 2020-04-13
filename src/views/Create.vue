<template>
  <div class="create">
    <div class="create__form">
      <label for="title">Title</label>
      <input class="mb" id="title" type="text" v-model="title" placeholder="Title" />

      <label for="author">Your name</label>
      <input class="mb" id="author" type="text" v-model="author" placeholder="Your name" />

      <label for="ingredients">Ingredients</label>
      <textarea class="mb" id="ingredients" v-model="ingredients" placeholder="List ingredients"></textarea>

      <label for="directions">Directions</label>
      <textarea class="mb" id="directions" v-model="directions" placeholder="Explain directions"></textarea>

      <label for="cost">Cost (dollars)</label>
      <div class="input-container">
        <div class="input-container-icon">
          <i class="fa fa-usd icon"></i>
        </div>
        <input class="input-field" id="cost" v-model.number="cost" type="number" />
      </div>

      <label for="time">Time (minutes)</label>
      <div class="input-container">
        <div class="input-container-icon">
          <i class="fa fa-clock-o icon"></i>
        </div>
        <input class="input-field" id="time" v-model.number="time" type="number" />
      </div>

      <label for="rating">Rating</label>
      <star-rating
        id="rating"
        :star-size="25"
        class="star-rating"
        :border-width="4"
        border-color="#d8d8d8"
        :rounded-corners="true"
        :star-points="[23,2, 14,17, 0,19, 10,34, 7,50, 23,43, 38,50, 36,34, 46,19, 31,17]"
        :show-rating="false"
        v-model="rating"
      ></star-rating>

      <!-- File upload -->
      <label for="image">Upload image</label>
      <div class="dropbox">
        <input
          id="image"
          type="file"
          :name="uploadFieldName"
          :disabled="isSaving"
          @change="filesChange($event.target.name, $event.target.files)"
          accept="image/*"
          class="input-file"
        />
        <p v-if="isInitial">
          Drag your file(s) here to begin
          <br />or click to browse
        </p>
        <p v-if="isSaving">Uploading file...</p>
      </div>
      <!-- File upload -->

      <a href class="btn-secondary">Submit</a>
    </div>
  </div>
</template>

<script>
const STATUS_INITIAL = 0,
  STATUS_SAVING = 1,
  STATUS_SUCCESS = 2,
  STATUS_FAILED = 3;

import { upload } from "../services/fileUpload.service";

export default {
  name: "Create",
  data() {
    return {
      title: "",
      ingredients: "",
      directions: "",
      rating: 1,
      author: "",
      cost: 0,
      time: 0,
      uploadedFile: [],
      uploadError: null,
      currentStatus: null,
      uploadFieldName: "photos"
    };
  },
  computed: {
    isInitial() {
      return this.currentStatus === STATUS_INITIAL;
    },
    isSaving() {
      return this.currentStatus === STATUS_SAVING;
    },
    isSuccess() {
      return this.currentStatus === STATUS_SUCCESS;
    },
    isFailed() {
      return this.currentStatus === STATUS_FAILED;
    }
  },
  methods: {
    reset() {
      // reset form to initial state
      this.currentStatus = STATUS_INITIAL;
      this.uploadedFiles = [];
      this.uploadError = null;
    },
    save(formData) {
      // upload data to the server
      this.currentStatus = STATUS_SAVING;

      upload(formData)
        .then(x => {
          this.uploadedFiles = [].concat(x);
          this.currentStatus = STATUS_SUCCESS;
        })
        .catch(err => {
          this.uploadError = err.response;
          this.currentStatus = STATUS_FAILED;
        });
    },
    filesChange(fieldName, fileList) {
      this.uploadedFile = fileList;
    }
  },
  mounted() {
    this.reset();
  }
};
</script>

<style lang="scss" scoped>
.create {
  padding: 1rem;
  .create__form {
    max-width: 800px;
    padding: 10px 20px;
    background: #fff;
    margin: 10px auto;
    border-radius: 8px;
  }
  .create__form textarea {
    resize: vertical; /* user can resize vertically, but width is fixed */
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
    background-color: #d8d7d8;
    color: #8a97a0;
    -webkit-box-shadow: 0 1px 0 rgba(0, 0, 0, 0.03) inset;
    box-shadow: 0 1px 0 rgba(0, 0, 0, 0.03) inset;
    &.mb {
      margin-bottom: 1rem;
    }
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
    background: #e2e2e2;
  }
  .create__form select {
    -webkit-appearance: menulist-button;
    height: 35px;
  }

  .create__form .star-rating {
    margin-bottom: 30px;
  }
  .input-container {
    display: -ms-flexbox; /* IE10 */
    display: flex;
    width: 100%;
    margin-bottom: 15px;
  }

  .icon {
    // padding: 10px;
    // color: white;
    min-width: 50px;
    text-align: center;
  }

  .input-container-icon {
    display: flex;
    align-items: center;
    background: #d8d7d8;
    border-radius: 4px 0px 0px 4px;
  }

  .input-field {
    width: 100%;
    padding: 10px;
    outline: none;

    border-radius: 0px 4px 4px 0px !important;
  }
}

.dropbox {
  outline: 2px dashed grey; /* the dash box */
  outline-offset: -10px;
  background: #d8d7d8;
  color: dimgray;
  padding: 10px 10px;
  min-height: 200px; /* minimum height */
  position: relative;
  cursor: pointer;
  margin-bottom: 1rem;
}

.input-file {
  opacity: 0; /* invisible but it's there! */
  width: 100%;
  height: 200px;
  position: absolute;
  cursor: pointer;
}

.dropbox:hover {
  background: #e2e2e2; /* when mouse over to the drop zone, change color */
}

.dropbox p {
  font-size: 1.2em;
  text-align: center;
  padding: 50px 0;
}
</style>