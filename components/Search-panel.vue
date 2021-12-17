<template>
  <div>
    <div class="row" style="padding-top: 5.5%">
      <div id="panel-text" class="col-xl-3">
        Search
        <div style="width: 100%; height: 61px; margin-top: 10px;">
          <input
            v-model="text"
            class="Search"
            placeholder="Converse"
            type="text"
          >
        </div>
      </div>
      <div id="panel-text" class="col-xl-3">
        Product category
        <div>
          <b-dropdown
            id="dropdown-left"
            :text="dropdown2"
            variant="light"
            class="m-2"
            style="width: 100%; height: 61px"
          >
            <b-dropdown-item
              v-for="(dropdown, index) in dropdowns"
              :key="index"
              :value="index"
              @click="clicked(index, 1)"
              >{{ dropdowns[1][index] }}</b-dropdown-item
            >
          </b-dropdown>
        </div>
      </div>
      <div id="panel-text" class="col-xl-3">
        Sale
        <div>
          <b-dropdown
            id="dropdown-left"
            :text="dropdown3"
            variant="light"
            class="m-2"
            style="width: 100%; height: 61px"
          >
            <b-dropdown-item
              v-for="(dropdown, index) in dropdowns"
              :key="index"
              @click="clicked(index, 2)"
              >{{ dropdowns[2][index] }}</b-dropdown-item
            >
          </b-dropdown>
        </div>
      </div>
      <div id="panel-text" class="col-xl-3">
        <button class="apply-button" @click="SORT(text, dropdown2, dropdown3)">Apply</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dropdowns: "",
      dropdown2: "",
      dropdown3: "",
      text: "",
    };
  },
  methods: {
    clicked(index, number) {
      switch (number) {
        case 1:
          this.dropdown2 = this.dropdowns[number][index];
          break;
        case 2:
          this.dropdown3 = this.dropdowns[number][index];
          break;
      }
    },
    SORT(text, category, sale) {
      this.$root.$refs.Content_component.SORT(text, category, sale);
    }
  },
  mounted() {
    this.dropdowns = [
      ["первый", "второй", "третий"],
      ["All", "второй", "Sneakers"],
      ["BestSellers"],
    ];
    this.dropdown2 = this.dropdowns[1][0];
    this.dropdown3 = this.dropdowns[2][0];
  },
};
</script>

<style scoped>
.Search {
  background-color: #f5f5f5;
  border-inline: none;
  border-block: none;
  outline: none;
  width: 100%;
  height: 61px;
  padding-left: 30px;
  font-family: Inter;
  font-style: normal;
  font-weight: 500;
  font-size: 18px;
  line-height: 22px;
  color: #000000;
}
#panel-text {
  font-family: Inter;
  font-style: normal;
  font-weight: 500;
  font-size: 18px;
  line-height: 22px;
  color: #000000;
}
.apply-button {
  margin-top: 30px;
  width: 100%;
  height: 61px;
  background: #1b1b1b;
  font-family: Inter;
  font-style: normal;
  font-weight: 500;
  font-size: 18px;
  line-height: 22px;
  text-align: center;
  color: #ffffff;
}
@media (max-width: 1200px) {
  #panel-text {
    text-align: center;
    padding-top: 5%;
  }
  .Search {
    text-align: center;
    padding-left: 0px;
  }
}
</style>