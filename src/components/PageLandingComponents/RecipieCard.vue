<template>
  <router-link :to="'/recipie/'+recipie._id">
    <article class="card">
      <div class="c1">
        <div class="overlay" v-on:click="deleteRecipie" v-if="deleteState">
          <div class="overlay__text__container">
            <div class="overlay__text">Delete this recipie</div>
          </div>
        </div>
        <div class="card__info-hover">
          <div class="card__clock-info">
            <svg class="card__clock" viewBox="0 0 24 24">
              <path
                d="M12,20A7,7 0 0,1 5,13A7,7 0 0,1 12,6A7,7 0 0,1 19,13A7,7 0 0,1 12,20M19.03,7.39L20.45,5.97C20,5.46 19.55,5 19.04,4.56L17.62,6C16.07,4.74 14.12,4 12,4A9,9 0 0,0 3,13A9,9 0 0,0 12,22C17,22 21,17.97 21,13C21,10.88 20.26,8.93 19.03,7.39M11,14H13V8H11M15,1H9V3H15V1Z"
              />
            </svg>
            <span class="card__time">{{recipie.time}} min</span>
          </div>
        </div>
        <div id="card__img" class="card__img"></div>
        <a href="#" class="card_link">
          <div :id="`${recipie._id}-card__img--hover`" class="card__img--hover"></div>
        </a>
        <div class="card__info">
          <span class="card__category">Recipe</span>
          <h3 class="card__title">{{recipie.title}}</h3>
          <span class="card__by">
            by
            <a href="#" class="card__author" title="author">{{recipie.author}}</a>
          </span>
          <div class="card__details layout">
            <div class="card__details__item card__details__time layout-item-33">
              <div class="card__details__item__heading">Time</div>
              <div class="card__details__item__value">{{recipie.time}} min</div>
            </div>
            <div class="card__details__item card__details__rating layout-item-33">
              <div class="card__details__item__heading">Rating</div>
              <div class="card__details__item__value">
                <star-rating
                  class="center-stars"
                  v-model="recipie.rating"
                  :read-only="true"
                  :star-size="15"
                  :show-rating="false"
                  :border-width="4"
                  border-color="#d8d8d8"
                  :rounded-corners="true"
                  :star-points="[23,2, 14,17, 0,19, 10,34, 7,50, 23,43, 38,50, 36,34, 46,19, 31,17]"
                ></star-rating>
              </div>
            </div>
            <div class="card__details__item card__details__cost layout-item-33">
              <div class="card__details__item__heading">Cost</div>
              <div class="card__details__item__value">${{recipie.cost}}</div>
            </div>
          </div>
        </div>
      </div>
    </article>
  </router-link>
</template>

<script>
export default {
  name: "RecipieCard",
  props: {
    recipie: Object,
    deleteState: Boolean
  },
  methods: {
    deleteRecipie(e) {
      e.preventDefault();
      console.log("Deleted");
    }
  },
  mounted() {
    const imgHoverDiv = document.getElementById(
      `${this.recipie._id}-card__img--hover`
    );
    const img = "url(" + this.recipie.image + ")";
    imgHoverDiv.style.backgroundImage = img;
  }
};
</script>

<style lang="scss">
@import "../../scss/variables.scss";

* {
  box-sizing: border-box;
}

.c1 {
  position: relative;
}

.cards {
  width: 100%;
  display: flex;
  display: -webkit-flex;
  justify-content: center;
  -webkit-justify-content: center;
  max-width: 820px;
}

.card__clock {
  width: 15px;
  vertical-align: middle;
  fill: #ad7d52;
}
.card__time {
  font-size: 12px;
  color: #ad7d52;
  vertical-align: middle;
  margin-left: 5px;
}

.card__clock-info {
  float: right;
}

.card__img {
  visibility: hidden;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  width: 100%;
  height: 235px;
  border-top-left-radius: 12px;
  border-top-right-radius: 12px;
}

.card__info-hover {
  position: absolute;
  padding: 16px;
  width: 100%;
  opacity: 0;
  top: 0;
}

.card__img--hover {
  transition: 0.2s all ease-out;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  width: 100%;
  position: absolute;
  height: 235px;
  border-top-left-radius: 12px;
  border-top-right-radius: 12px;
  top: 0;
}
.card {
  margin-right: 25px;
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0, 1);
  background-color: #fff;
  position: relative;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0px 13px 10px -7px rgba(0, 0, 0, 0.1);
}
.card:hover {
  box-shadow: 0px 30px 18px -8px rgba(0, 0, 0, 0.1);
  /*     transform: scale(1.10, 1.10); */
}

.card__info {
  z-index: 2;
  background-color: #fff;
  border-bottom-left-radius: 12px;
  border-bottom-right-radius: 12px;
  padding: 16px 24px 24px 24px;
}

.card__category {
  /* font-family: "Raleway", sans-serif; */
  text-transform: uppercase;
  font-size: 13px;
  letter-spacing: 2px;
  font-weight: 500;
  color: #868686;
}

.card__title {
  margin-top: 5px;
  margin-bottom: 10px;
  /* font-family: "Roboto Slab", serif; */
}

.card__by {
  font-size: 12px;
  font-family: "Raleway", sans-serif;
  font-weight: 500;
}

.card__author {
  font-weight: 600;
  text-decoration: none;
  color: #ad7d52;
}

.card:hover .card__img--hover {
  height: 100%;
  opacity: 0.3;
}

.card:hover .card__info {
  background-color: transparent;
  position: relative;
}

.card:hover .card__info-hover {
  opacity: 1;
}

.card__details {
  padding-top: 15px;
  margin-top: 15px;
  border-top: 1px solid $background;
}

.card__details__item {
  text-align: center;
}

.card__details__item__heading {
  padding-bottom: 5px;
}

.card__details__item__value {
  font-size: 1.1rem;
}

.overlay {
  background-color: rgba(217, 83, 79, 0.25);
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  z-index: 10;
}

.overlay__text__container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  color: white;
  font-size: 1.5rem;
}

.overlay__text {
  background-color: rgba(217, 83, 79, 1);
  padding: 0.5rem;
  border-radius: 5px;
}
</style>