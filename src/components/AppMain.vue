<script>
import AppCards from "./AppCards.vue";
export default {
  data() {
    return {
      cards: [
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
          like: true,
        },
        {
          name: "Voglia di colori pastello",
          brand: "Come Zucchero Filato",
          image: "../public/img/3.webp",
          imageAlt: "../public/img/3b.webp",
          price: 184.99,
          discount: 30,
          sustainability: false,
          like: false,
        },
        {
          name: "Tee Unisex",
          brand: "Levi's",
          image: "../public/img/4.webp",
          imageAlt: "../public/img/4b.webp",
          price: 29.99,
          discount: 50,
          sustainability: false,
          like: false,
        },
        {
          name: "Stripe Bodice",
          brand: "Maya Deluxe",
          image: "../public/img/5.webp",
          imageAlt: "../public/img/5b.webp",
          price: 99.99,
          sustainability: false,
          like: false,
        },
        {
          name: "Maglione - Black",
          brand: "Esprit",
          image: "../public/img/6.webp",
          imageAlt: "../public/img/6b.webp",
          price: 29.99,
          sustainability: true,
          like: false,
        },
      ],
    };
  },
  components: {
    AppCards,
  },
  methods: {
    //ObjName is passed from the event like-button in AppCards component
    toggleLike(objName) {
      //Find the card that have the same name of the one clicked
      let toggle = this.cards.find((card) => card.name === objName);
      //Toggle like key
      toggle.like = !toggle.like;
    },
  },
};
</script>

<template>
  <main>
    <div class="container-big">
      <div class="row">
        <div class="col-33" v-for="card in cards">
          <AppCards
            :name="card.name"
            :brand="card.brand"
            :image="card.image"
            :imageAlt="card.imageAlt"
            :price="card.price"
            :discount="card.discount"
            :sustainability="card.sustainability"
            :like="card.like"
            @like-button="toggleLike"
          /><!-- like-button event is generated on AppCard component -->
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped lang="scss">
@use "../styles/main.scss";
</style>
