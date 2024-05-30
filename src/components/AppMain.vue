<script>
import AppCards from "./AppCards.vue";

export default {
  data() {
    return {
      objects: [
        {
          name: "Relaxed Fit Tee Unisex",
          brand: "Levi's",
          image: "/img/1.webp",
          imageAlt: "/img/1b.webp",
          price: 29.99,
          discount: 50,
          sustainability: true,
          like: false,
        },
        {
          name: "Roses Tee",
          brand: "Guess",
          image: "../public/img/2.webp",
          imageAlt: "../public/img/2b.webp",
          price: 29.99,
          discount: 30,
          sustainability: false,
          like: false,
        },
      ],
    };
  },
  components: {
    AppCards,
  },
};
</script>

<template>
  <main>
    <div class="container-big">
      <div class="row">
        <div class="col-33" v-for="object in objects">
          <AppCards
            :name="object.name"
            :brand="object.brand"
            :image="object.image"
            :imageAlt="object.imageAlt"
            :price="object.price"
            :discount="object.discount"
            :sustainability="object.sustainability"
            :like="object.like"
          />
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped lang="scss">
@use "../styles/main.scss";
</style>
