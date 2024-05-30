<script setup></script>

<template>
  <header>
    <div class="container-big">
      <div class="row">
        <div class="col-33">
          <div class="categories">
            <a href="">Donna</a>
            <a href="">Uomo</a>
            <a href="">Bambini</a>
          </div>
        </div>
        <div class="col-33 text-center">
          <a href="">
            <img class="logo" src="/img/boolean-logo.png" alt="logo" />
          </a>
        </div>
        <div class="col-33">
          <div class="container-icon">
            <img class="icon" src="/img/user.png" alt="user" />
            <img class="icon" src="/img/like.png" alt="like" />
            <img class="icon" src="/img/shopping-bag.png" alt="shop" />
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<style scoped lang="scss">
@use "../styles/main.scss";
@import "../styles/partials/variables";
/* HEADER */
header {
  position: fixed;
  width: 100%;
  background-color: $header-bg-color;
  z-index: 10;
  font-weight: 600;
  box-shadow: 0 2px 1px gray;
}

.categories {
  display: inline-block;
  vertical-align: middle;
}

.categories a {
  color: white;
  text-decoration: none;
  margin-right: 10px;
}

.logo {
  width: 100px;
}

.container-icon {
  vertical-align: middle;
  float: right;
}

.icon {
  vertical-align: middle;
  width: 20px;
  margin: 0px 5px;
  filter: invert(100%) sepia(100%) saturate(0%) hue-rotate(138deg)
    brightness(102%) contrast(101%);
}
</style>
