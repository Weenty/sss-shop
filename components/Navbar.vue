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
        <button
          @click="showm()"
          class="button-backet"
        >
          Basket <a v-if="basket !== 0">({{ basket }}) </a>
        </button>
        <modal
        v-if="showModal"
          name="my-modal"
          :width="455"
          :height="790"
          :shiftX="1"
          :shiftY="0"
          :adaptive="true"
        >
          <div class="modal-content">
            <div class="container">
              <div style="padding-top: 50px" class="row">
                <div class="col">
                  <div style="text-align: center" class="button-profile">
                    Profile
                  </div>
                </div>
                <div class="col">
                  <button style="text-align: center" class="button-backet">
                    Basket <a v-if="basket !== 0">({{ basket }}) </a>
                  </button>
                </div>
              </div>

              <div class="line" />
              <div class="row">
                <div
                  style="
                    font-family: Inter;
                    font-style: normal;
                    font-weight: bold;
                    font-size: 24px;
                    line-height: 29px;
                    padding-top: 20px
                    text-transform: uppercase;
                    color: #000000;
                  "
                  class="col-12"
                >
                  TOTAL
                </div>
                <div class="row" id="modal-row" >
                  <div class="col-6">Subtotal: </div>
                  <div class="col-6">$99,99</div>
                </div>
                <div class="row" id="modal-row">
                  <div class="col-6">Sale: </div>
                  <div class="col-6">$34:00</div>
                </div>
                <div class="row" id="modal-row">
                  <div class="col-6">Content</div>
                  <div class="col-6">Remove all</div>
                </div>
              </div>
            </div>
          </div>
        </modal>
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
      showModal: false,
    };
  },
  methods: {
    showm() {
      this.showModal = true
      this.$nextTick(()=> {
      this.$modal.show('my-modal')
      })
    },
  }
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
#modal-row {
  width:100%; 
  text-align: center;
  margin-top: 20px;
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