<template>
  <div class="container">
    <div class="row" id="nav-text">
      <div class="col-3" id="logo-hide">
        <div class="logo">S-SHOP</div>
      </div>
      <div class="col-xl-6 col-lg-6 col-md-6 col-sm col">
        <div class="button-catalog">Catalogy</div>
      </div>
      <div class="col"><div class="button-profile">Profile</div></div>
      <div class="col">
        <button @click="visible = !visible" class="button-backet">
          Basket <a v-if="basket !== 0">({{ basket }}) </a>
        </button>
      </div>
    </div>
    <div class="line" />
  </div>
</template>
<script>
export default {
  data() {
    return {
      basket: 2,
      visible: false,
    };
  },
};
</script>
<style scoped>
#nav-text {
  padding-top: 2.5%;
}
.line {
  width: 100%;
  border: 1px solid #bdbdbd;
  margin-top: 2.5%;
}
.logo {
  font-family: Inter;
  font-style: normal;
  font-weight: 600;
  font-size: 24px;
  line-height: 29px;
  color: #000000;
}
.button-catalog {
  font-family: Inter;
  font-style: normal;
  font-weight: 500;
  font-size: 18px;
  line-height: 22px;
  color: #ff6b00;
}
.button-profile {
  font-family: Inter;
  font-style: normal;
  font-weight: normal;
  font-size: 18px;
  line-height: 22px;
  color: #000000;
}
.button-backet {
  outline: none;
  border: 0;
  background: transparent;
  font-family: Inter;
  font-style: normal;
  font-weight: normal;
  font-size: 18px;
  line-height: 22px;
  color: #000000;
}
@media (max-width: 467px) {
  .logo {
    display: none;
  }
  #logo-hide {
    display: none;
  }
}
</style>