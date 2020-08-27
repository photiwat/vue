<template>
  <div class="bg">
    <b-container class="text-center">
      <b-row class="pt-5 pl-5 pr-5">
        <b-col class="bgcol border1">
          <b-img
            v-bind="mainProps"
            rounded="circle"
            alt="Circle image"
            class="color2"
          ></b-img>
        </b-col>
        <b-col class="bgcol border2">
          <b-img
            v-bind="mainProps"
            rounded="0"
            alt="Not rounded image"
            class="color1"
          ></b-img>
        </b-col>
      </b-row>

      <b-row class="pb-5 pl-5 pr-5">
        <b-col class="bgcol border3">
          <b-img
            v-bind="mainProps"
            rounded="0"
            alt="Not rounded image"
            class="color2"
          ></b-img>
        </b-col>
        <b-col class="bgcol border4">
          <b-img
            v-bind="mainProps"
            rounded="circle"
            alt="Circle image"
            class="color1"
          ></b-img>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script>
  export default {
    name: "Styling",
    data() {
      return {
        mainProps: {
          blank: true,
          width: 150,
          height: 150,
          class: "m1",
        },
      };
    },
  };
</script>
<style scoped>
  .bg {
    background-color: #4f4f51;
  }
  .bgcol {
    background-color: white;
    height: 250px;
    padding: 50px;
  }
  .color1 {
    background-color: #6f7072;
  }
  .color2 {
    background-color: #f19202;
  }
  .border1 {
    border-right: 10px solid;
    border-right-color: #dcdcdc;
    border-bottom: 10px solid;
    border-bottom-color: #dcdcdc;
  }
  .border2 {
    border-left: 10px solid;
    border-left-color: #dcdcdc;
    border-bottom: 10px solid;
    border-bottom-color: #dcdcdc;
  }
  .border3 {
    border-right: 10px solid;
    border-right-color: #dcdcdc;
    border-top: 10px solid;
    border-top-color: #dcdcdc;
  }
  .border4 {
    border-left: 10px solid;
    border-left-color: #dcdcdc;
    border-top: 10px solid;
    border-top-color: #dcdcdc;
  }
</style>
