<template>
  <div>
    <div v-if="nonContent" class="container" style="margin-top: 10%">
      <div class="hight-text">
        {{ hight_text }}:
        <div class="count">{{ count }}</div>
      </div>
      <div class="row">
        <div
          v-for="(card, index) in filteredProducts"
          :key="index"
          :class="{
            'col-xl-3 col-lg-4 col-md-6 col-auto col-sm-auto': index !== 2,
            'col-xl-6 col-lg-4 col-md-6 col-auto col-sm-auto': index == 2,
            'col-xl-3 col-lg-4 col-md-6 col-auto col-sm-auto card-pad':
              (index == 0 || index == 1) && Sortedproducts.length >= 3,
          }"
          style="padding-top: 30px"
        >
          <div :id="['card' + index]" class="card">
            <img :src="'img/' + card.img" />
            <div
              v-if="
                card.Sale !== 0 && card.Sale !== '' && card.Sale !== undefined
              "
              class="Sale"
            >
              <div class="Sale-text">Sale -{{ card.Sale }}%</div>
            </div>
            <div class="card-text">{{ card.name }}</div>
            <div class="card-price">${{ card.price }}</div>
            <div v-if="index == 2">
              <div class="row">
                <div class="col-xl-6">
                  <button
                    v-if="locked(card.uid)"
                    class="card-button"
                    :id="card.uid"
                    @click="[Add(card.uid), lock(card.uid)]"
                    :class="{ active: false }"
                  >
                    <div class="row">
                      <div class="col-8">
                        <div class="button-text">Add to basket</div>
                      </div>
                      <div class="col">
                        <svg
                          style="margin-bottom: 3px"
                          width="16"
                          height="16"
                          viewBox="0 0 16 17"
                          fill="none"
                          xmlns="http://www.w3.org/2000/svg"
                        >
                          <path
                            d="M8 0.5V8.5M8 16.5V8.5M8 8.5H0H16"
                            stroke="white"
                            stroke-width="1.5"
                          />
                        </svg>
                      </div>
                    </div>
                  </button>
                  <button
                    class="card-button-white"
                    v-else
                    @click="[unlock(card.uid), remove(card.uid)]"
                  >
                    <div class="row">
                      <div class="col-8">
                        <div>Added</div>
                      </div>
                      <div class="col">
                        <svg
                          width="16"
                          height="13"
                          viewBox="0 0 16 13"
                          fill="none"
                          xmlns="http://www.w3.org/2000/svg"
                        >
                          <path
                            d="M1 6L6 11L15 1"
                            stroke="black"
                            stroke-width="1.5"
                          />
                        </svg>
                      </div>
                    </div>
                  </button>
                </div>
              </div>
            </div>
            <div v-else>
              <button
                v-if="locked(card.uid)"
                class="card-button"
                :id="card.uid"
                @click="[Add(card.uid), lock(card.uid)]"
              >
                <div class="row">
                  <div class="col-8">
                    <div class="button-text">Add to basket</div>
                  </div>
                  <div class="col">
                    <svg
                      style="margin-bottom: 3px"
                      width="16"
                      height="16"
                      viewBox="0 0 16 17"
                      fill="none"
                      xmlns="http://www.w3.org/2000/svg"
                    >
                      <path
                        d="M8 0.5V8.5M8 16.5V8.5M8 8.5H0H16"
                        stroke="white"
                        stroke-width="1.5"
                      />
                    </svg>
                  </div>
                </div>
              </button>
              <button
                class="card-button-white"
                v-else
                @click="[unlock(card.uid), remove(card.uid)]"
              >
                <div class="row">
                  <div class="col-8">
                    <div>Added</div>
                  </div>
                  <div class="col">
                    <svg
                      width="16"
                      height="13"
                      viewBox="0 0 16 13"
                      fill="none"
                      xmlns="http://www.w3.org/2000/svg"
                    >
                      <path
                        d="M1 6L6 11L15 1"
                        stroke="black"
                        stroke-width="1.5"
                      />
                    </svg>
                  </div>
                </div>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div v-else id="notFounded" class="container">Not Found</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      hight_text: "All",
      Sortedproducts: [],
      button_lock: [],
      cards: [
        {
          uid: "1",
          name: "123",
          price: "49.99",
          img: "iugQZtch-fg.jpg",
          category: "Sneakers",
          Sale: 4,
        },
        {
          uid: "2",
          name: "Converse Kids 70",
          price: "49.99",
          img: "iugQZtch-fg.jpg",
          category: "Sneakers",
          Sale: 2,
        },
        {
          uid: "3",
          name: "Converse Kids 70",
          price: "49.99",
          img: "iugQZtch-fg.jpg",
          category: "Sneakers",
          Sale: 2,
        },
        {
          uid: "4",
          name: "Converse Kids 70",
          price: "49.99",
          img: "iugQZtch-fg.jpg",
          category: "Sneakers",
          Sale: 2,
        },
        {
          uid: "5",
          name: "Converse Kids 70",
          price: "49.99",
          img: "iugQZtch-fg.jpg",
          category: "Sneakers",
          Sale: 2,
        },
        {
          uid: "6",
          name: "Converse Kids 70",
          price: "49.99",
          img: "iugQZtch-fg.jpg",
          category: "Sneakers",
          Sale: 2,
        },
        {
          uid: "7",
          name: "Converse Kids 70",
          price: "49.99",
          img: "iugQZtch-fg.jpg",
          category: "Sneakers",
          Sale: 2,
        },
        {
          uid: "8",
          name: "Converse Kids 70",
          price: "49,99",
          img: "iugQZtch-fg.jpg",
          category: "Sneakers",
          Sale: 2,
        },
      ],
    };
  },
  methods: {
    removeAll() {
      this.button_lock = [];
    },
    unlock(uid) {
      this.button_lock.splice(this.button_lock.indexOf(uid), 1);
    },
    locked(uid) {
      return this.button_lock.indexOf(uid) == -1;
    },
    lock(uid) {
      if (this.button_lock.indexOf(uid) == -1) {
        this.button_lock.push(uid);
      }
    },
    remove(uid) {
      this.$root.$refs.Navbar_component.remove(uid);
    },
    Add(uid) {
      this.$root.$refs.Navbar_component.Add(
        this.cards
          .map((item) => {
            return item.uid == uid ? item : null;
          })
          .filter((el) => el !== null)
      );
    },
    SORT(text, category, sale) {
      this.Sortedproducts = [];
      let contex = this;
      this.cards.map((item) => {
        if (category === "All") {
          contex.Sortedproducts = contex.cards;
          this.break;
        }
        if (item.category == category) {
          contex.Sortedproducts.push(item);
        }
      });
      this.hight_text = category;
      if (text !== "" && text !== 0 && text !== undefined) {
        let arr = text.split(" ");
        let bufer = contex.Sortedproducts;
        contex.Sortedproducts = bufer.filter((item) => {
          if (
            item.name.split(" ").some((item1, index) => {
              return String(item1) == String(arr[index]);
            })
          ) {
            return item;
          }
        });
        this.hight_text = "Результаты по " + text;
      }
    },
  },
  computed: {
    count() {
      return this.Sortedproducts.length;
    },
    nonContent() {
      return this.Sortedproducts.length !== 0 ? true : false;
    },
    filteredProducts() {
      if (this.Sortedproducts.length !== 0) {
        return this.Sortedproducts;
      } else {
        return this.cards;
      }
    },
  },
  created() {
    this.$root.$refs.Content_component = this;
  },
  beforeMount() {
    this.Sortedproducts = this.cards;
  },
};
</script>

<style scoped>
.card-button-white {
  width: 100%;
  height: 60px;
  background: #ffffff;
}
#notFounded {
  padding-top: 20%;
  text-align: center;
  size: 20px;
}
.card-pad {
  margin-top: 320px;
}
.Sale-text {
  font-family: Inter;
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 19px;
  text-align: center;
  color: #ffffff;
}
.Sale {
  position: absolute;
  top: 8px;
  right: 16px;
  background: #ff6b00;
  width: 121px;
  height: 43;
}
.button-text {
  font-family: Inter;
  font-style: normal;
  font-weight: 500;
  font-size: 18px;
  line-height: 22px;
  color: #ffffff;
}
.card-button {
  width: 100%;
  height: 60px;
  background: #2e2e2e;
}
.hight-text {
  font-family: Inter;
  font-style: normal;
  font-weight: bold;
  font-size: 40px;
  line-height: 48px;
  text-transform: uppercase;
  color: #000000;
}
@media (max-width: 1099px) {
  #card0 {
    margin-top: 0px;
  }
  #card1 {
    margin-top: 0px;
  }
}
</style>