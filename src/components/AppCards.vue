<script>
export default {
  props: {
    name: {
      type: String,
      required: true,
    },
    brand: {
      type: String,
      required: true,
    },
    image: {
      type: String,
      required: true,
    },
    imageAlt: {
      type: String,
      required: false,
    },
    price: {
      type: Number,
      required: true,
    },
    discount: {
      type: Number,
      required: false,
    },
    sustainability: {
      type: Boolean,
      required: true,
    },
    like: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    calcDiscount(price, discount) {
      return (price - (price * discount) / 100).toFixed(2);
    },
    likeButton(like) {
      like = !like;
    },
  },
};
</script>

<template>
  <div class="content">
    <!-- IMAGES -->
    <div class="img-content">
      <img class="main-pic" :src="image" alt="img1" />
      <img class="hover-pic" :src="imageAlt" alt="img1b" />
      <!-- LABELS -->
      <div class="labels">
        <span class="discount-label" v-show="discount">
          {{ `-${discount}%` }}
        </span>
        <span class="sus-label" v-show="sustainability"> Sostenibilità </span>
      </div>
      <div class="hearts-label" @click="likeButton(like)" v-show="like">
        &hearts;
      </div>
    </div>
    <!-- TEXT -->
    <div class="text">
      <div class="brand">{{ brand }}</div>
      <div class="item">{{ name }}</div>
      <div class="price">
        {{ calcDiscount(price, discount) }} &euro;
        <span class="discount-txt">{{ price }} &euro;</span>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import "../styles/partials/variables";

/* IMAGES */
// .content {
// }

img {
  width: 100%;
}
.img-content {
  position: relative;
}

.hover-pic {
  display: none;
}

.content:hover .main-pic {
  display: none;
}

.content:hover .hover-pic {
  display: inline-block;
}

/* ----- TEXT ----- */
.text {
  padding-bottom: 5px;
}

.brand {
  font-size: 15px;
}

.item {
  font-weight: 600;
}

.price {
  font-size: 15px;
  font-weight: 600;
  color: $text-price;
}

.discount-txt {
  font-size: 15px;
  font-weight: 400;
  color: $text-discounted;
  text-decoration: line-through;
}

.labels {
  position: absolute;
  bottom: 30px;
}

.discount-label {
  font-size: 15px;
  background-color: $label-discount;
  color: $text-discount;
  font-weight: 600;
  padding: 5px 12px;
  margin-right: 5px;
}

.sus-label {
  font-size: 15px;
  background-color: $label-sustainability;
  color: $text-sustainability;
  font-weight: 600;
  padding: 5px 10px;
}

.hearts-label {
  position: absolute;
  background-color: $label-hearts;
  padding: 2px 10px;
  font-size: 30px;
  top: 10px;
  right: 0px;
}

.hearts-label:hover {
  color: $text-hearts-hover;
}
</style>
