<template>
  <div class="container" style="margin-top:10%">
    <div class="bestsellers">
      BESTSELLERS:
      <div>{{ count }}</div>
    </div>
    <div class="row">
        <div class="col">
            1
        </div>
        <div class="col">
            2
        </div>
        <div class="col">
            3
        </div>
        <div class="col">
            4
        </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: '321',
    };
  },
};
</script>

<style scoped>
.bestsellers {
  font-family: Inter;
  font-style: normal;
  font-weight: bold;
  font-size: 40px;
  line-height: 48px;
  text-transform: uppercase;
  color: #000000;
}
</style>