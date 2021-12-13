<template>
  <div class="Footer">
    <div class="container"> 
        <div class="row">
            <div class="col" style="padding-top: 40px">
                S-SHOP
            </div>
            <div class="col-8 col-md-10 col-lg-10 col-sm-9" style="word-spacing: 20px; padding-top: 40px">
                Contacts Copyright
            </div>
        </div>
    </div>
  </div>
</template>

<style scoped>
.Footer {
  width: 100%;
  height: 110px;
  background-color: black;
  margin-top: 10%;
}
.container {
  font-family: Inter;
  font-style: normal;
  font-weight: 500;
  font-size: 18px;
  line-height: 22px;
  color: #ffffff;
  text-align: right;
}
@media (max-width: 500px) {
    .Footer {
        display: none;
    }
}
</style>