<script>
export default {
  props: {
    id: {
      type: Number,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    brand: {
      type: String,
      required: true,
    },
    frontImage: {
      type: String,
      required: true,
    },
    backImage: {
      type: String,
      required: false,
    },
    price: {
      type: Number,
      required: true,
    },
    badges: {
      type: Array,
      required: false,
    },
    isInFavorites: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    calcOriginalPrice(price, discount) {
      console.log(discount);
      if (discount > 0) {
        return (price + (price * discount) / (100 - discount)).toFixed(2);
      } else {
        return price;
      }
    },
    likeButton() {
      // Call the like-button event on AppMain and pass the name value
      this.$emit("like-Button", this.name);
      console.log(this.like);
    },
    sortedBadges(badges) {
      return badges.slice().sort((a, b) => {
        if (a.type === "discount" && b.type !== "discount") {
          return -1;
        }
        if (a.type !== "discount" && b.type === "discount") {
          return 1;
        }
        return 0;
      });
    },
  },
};
</script>

<template>
  <div class="content">
    <!-- IMAGES -->
    <div class="img-content">
      <img class="main-pic" :src="'/img/' + frontImage" :alt="frontImage" />
      <img class="hover-pic" :src="'/img/' + backImage" :alt="backImage" />
      <!-- LABELS -->
      <div class="labels">
        <span
          v-for="badge in sortedBadges(badges)"
          :class="{
            discountLabel: badge.type === 'discount',
            susLabel: badge.type === 'tag',
          }"
        >
          {{ badge.value }}
        </span>

        <!-- <span class="discount-label" v-show="discount">
          {{ `-${badges}%` }}
        </span> -->
        <!-- <span class="sus-label" v-show="badge"> Sostenibilità </span> -->
      </div>
      <div
        :class="{ liked: this.isInFavorites }"
        class="hearts-label"
        @click="likeButton(isInFavorites)"
      >
        &hearts;
      </div>
    </div>
    <!-- TEXT -->
    <div class="text">
      <div class="brand">{{ brand }}</div>
      <div class="item">{{ name }}</div>
      <div class="price">
        {{ price }} &euro;
        <span
          class="discount-txt"
          v-show="sortedBadges(badges)[0].type === 'discount'"
          >{{
            calcOriginalPrice(
              price,
              sortedBadges(badges)[0].value.replace(/[^\d.]/g, "")
            )
          }}
          &euro;</span
        >
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

.discountLabel {
  font-size: 15px;
  background-color: $label-discount;
  color: $text-discount;
  font-weight: 600;
  padding: 5px 12px;
  margin-right: 5px;
}

.susLabel {
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
  &.liked {
    color: $text-hearts-hover;
  }
  // About 2 hour on this and the result not so beuty :')
  // &:hover {
  //   color: $text-hearts-hover;
  // }
  // &.liked {
  //   color: $text-hearts-hover;
  //   &:hover {
  //     color: $text-hearts;
  //   }
  // }
}
</style>
