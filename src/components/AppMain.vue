<script>
import db from "../data/db.json";
import AppCards from "./AppCards.vue";
export default {
  data() {
    return {
      db,
    };
  },
  components: {
    AppCards,
  },
  methods: {
    //ObjName is passed from the event like-button in AppCards component
    toggleLike(objName) {
      //Find the card that have the same name of the one clicked
      let toggle = this.db.products.find((product) => product.name === objName);
      //Toggle like key
      toggle.isInFavorites = !toggle.isInFavorites;
    },
  },
};
</script>

<template>
  <main>
    <div class="container-big">
      <div class="row">
        <div class="col-33" v-for="product in db.products">
          <AppCards
            :id="product.id"
            :name="product.name"
            :brand="product.brand"
            :frontImage="product.frontImage"
            :backImage="product.backImage"
            :price="product.price"
            :badges="product.badges"
            :isInFavorites="product.isInFavorites"
            @like-button="toggleLike"
          />
          <!-- like-button event is generated on AppCard component -->
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped lang="scss">
@use "../styles/main.scss";
</style>
