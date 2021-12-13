<template>
  <div>
    <div class="row" style="padding-top: 5.5%">
      <div id="panel-text" class="col-xl-3">
        Search
        <div>
          <b-dropdown
            id="dropdown-left"
            :text="dropdown1"
            variant="light"
            class="m-2"
            style="width: 100%; height: 61px;"
          >
            <b-dropdown-item
              v-for="(dropdown, index) in dropdowns"
              :key="dropdown"
              :value="index"
              @click="clicked(index, 0)"
              >{{ dropdowns[0][index] }}</b-dropdown-item
            >
          </b-dropdown>
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
            style="width: 100%; height: 61px;"
          >
            <b-dropdown-item
              v-for="(dropdown, index) in dropdowns"
              :key="dropdown"
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
            style="width: 100%; height: 61px;"
          >
            <b-dropdown-item
              v-for="(dropdown, index) in dropdowns"
              :key="dropdown"
              :value="index"
              @click="clicked(index, 2)"
              >{{ dropdowns[2][index] }}</b-dropdown-item
            >
          </b-dropdown>
        </div>
      </div>
      <div id="panel-text" class="col-xl-3">
        <button class="apply-button">Apply</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dropdowns: "",
      dropdown1: "",
      dropdown2: "",
      dropdown3: "",
    };
  },
  methods: {
    clicked(index, number) {
      switch (number) {
        case 0:
          this.dropdown1 = this.dropdowns[number][index];
          break;
        case 1:
          this.dropdown2 = this.dropdowns[number][index];
          break;
        case 2:
          this.dropdown3 = this.dropdowns[number][index];
          break;
      }
    },
  },
  mounted() {
    this.dropdowns = [
      ["первый", "второй", "третий"],
      ["первый", "второй", "третий"],
      ["первый", "второй", "третий"],
    ];
    this.dropdown1 = this.dropdowns[0][0];
    this.dropdown2 = this.dropdowns[1][1];
    this.dropdown3 = this.dropdowns[2][2];
  },
};
</script>

<style scoped>
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
}
</style>