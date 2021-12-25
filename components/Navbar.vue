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
        <button @click="showm()" class="button-backet">
          Basket <a v-if="basket_count !== 0">({{ basket_count }}) </a>
        </button>
        <modal
          v-if="showModal"
          name="my-modal"
          :width="455"
          :height="760"
          :shiftX="1"
          :scrollable="true"
          :shiftY="0"
          :adaptive="true"
          :styles="{ 'overflow: hidden;': showModal }"
        >
          <div class="modal-content" style="overflow-y: scroll; height: 700px">
            <div class="container">
              <div style="padding-top: 50px" class="row">
                <div class="col">
                  <div style="text-align: center" class="button-profile">
                    Profile
                  </div>
                </div>
                <div class="col">
                  <button
                    @click="showModal = false"
                    style="text-align: center"
                    class="button-backet"
                  >
                    Basket
                    <a v-if="basket_count !== 0">({{ basket_count }}) </a>
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
                  <div class="container">TOTAL</div>
                </div>
                <div class="row" id="modal-row">
                  <div class="col-6">Subtotal:</div>
                  <div class="col-6">${{ Subtotal }}</div>
                </div>
                <div class="row" id="modal-row">
                  <div class="col-6">Sale:</div>
                  <div class="col-6">${{ Sale }}</div>
                </div>
                <div class="row" id="modal-row">
                  <div class="col-6">Content</div>
                  <button
                    style="
                      border: 0;
                      font-family: Inter;
                      font-style: normal;
                      font-weight: 500;
                      font-size: 16px;
                      line-height: 19px;
                      text-decoration-line: underline;
                      color: #000000;
                    "
                    @click="[remove('All'), removeAll()]"
                    class="col-6"
                  >
                    Remove all
                  </button>
                </div>
                <div class="line" />
                <div class="container">
                  <div class="row" id="modal-row">
                    <div
                      class="col-6"
                      style="
                        font-family: Inter;
                        font-style: normal;
                        font-weight: 500;
                        font-size: 20px;
                        line-height: 24px;

                        color: #000000;
                      "
                    >
                      Order Total
                    </div>
                    <div class="col-6">${{ OrderTotal }}</div>
                  </div>
                </div>
                <div class="line" />
                <div class="container">
                  <div
                    v-for="(product, index) in basket"
                    :key="index"
                    class="row"
                    id="modal-row"
                  >
                    <div class="col-6">
                      <img
                        style="width: 120px; height: 120px"
                        :src="'img/' + 'iugQZtch-fg.jpg'"
                        alt=""
                      />
                    </div>
                    <div
                      class="col-6"
                      style="
                        text-align: left;
                        font-family: Inter;
                        font-style: normal;
                        font-weight: normal;
                        font-size: 16px;
                        line-height: 19px;
                        color: #818181;
                      "
                    >
                      {{ product.name }}
                      <div
                        style="
                          font-family: Inter;
                          font-style: normal;
                          font-weight: 500;
                          font-size: 16px;
                          line-height: 19px;
                          color: #000000;
                        "
                      >
                        ${{ product.price }}
                      </div>
                      <button
                        @click="[remove(product.uid), unlock(product.uid)]"
                        style="
                          font-family: Inter;
                          font-style: normal;
                          font-weight: normal;
                          font-size: 16px;
                          line-height: 19px;
                          text-decoration-line: underline;
                          border: 0;
                          margin-top: 30px;
                          color: #000000;
                        "
                      >
                        remove
                      </button>
                    </div>
                  </div>
                  <div style="margin-top: 41px"></div>
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
      showModal: false,
      basket: [],
    };
  },
  methods: {
    unlock(uid) {
      this.$root.$refs.Content_component.unlock(uid);
    },
    removeAll() {
      this.$root.$refs.Content_component.removeAll();
    },
    showm() {
      this.showModal = true;
      this.$nextTick(() => {
        this.$modal.show("my-modal");
      });
    },
    remove(uid) {
      if (uid === "All") {
        this.basket = [];
      } else {
        let index = this.basket
          .map((item, index) => {
            if (item.uid == uid) return index;
          })
          .filter((item) => item != undefined)[0];
        this.basket.splice(index, 1);
      }
    },
    Add(arr) {
      this.basket.push(arr[0]);
    },
  },
  created() {
    this.$root.$refs.Navbar_component = this;
  },
  computed: {
    Subtotal() {
      return this.OrderTotal - this.Sale
    },
    Sale() {
      return (this.basket
        .map((item) => {
          return parseFloat(item.price) * parseFloat(item.Sale)/100
        })
        .reduce((sum, current) =>{
          return sum + current;
        }, 0)).toFixed(2)
    },
    OrderTotal() {
      return (this.basket.reduce((sum, current) => {
        return sum + parseFloat(current.price);
      }, 0)).toFixed(2)
    },
    basket_count() {
      return this.basket.length
    }
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
#modal-row {
  width: 100%;
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