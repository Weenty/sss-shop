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
      <div class="col"><div class="button-backet">Bascket<a v-if="backet!==0">({{bascket}})</a></div></div>
    </div>
    <div class="line" />
    
  </div>
</template>
<script>
export default {
  data() {
    return {
      bascket: 2,
    }
  }
}
</script>
<style scoped>
#nav-text {
  padding-top: 2.5%;
}
.line {
  width: 100%;
  border: 1px solid #BDBDBD;
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
  color: #FF6B00 
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
  font-family: Inter;
  font-style: normal;
  font-weight: normal;
  font-size: 18px;
  line-height: 22px;
  color: #000000;
}
@media (max-width: 443px) {
    .logo {
      display: none;
    }
    #logo-hide {
      display: none;
    }
}
</style>