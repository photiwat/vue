<template>
  <b-container fluid>
    <b-row>
      <b-form-group id="input-group-2" label="Search:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="search"
          required
          placeholder="Search"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Select Year:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="select"
          :options="years"
          required
        ></b-form-select>
      </b-form-group>
    </b-row>
    <b-row>
      <b-col
        cols="3"
        class="pt-3 pb-3"
        :key="key"
        v-for="(cars, key) in sortFunc"
      >
        <b-card :title="cars.model">
          <i class="fas fa-times icondelete" @click="deletecar(key)"></i>
          <b-card-text>
            <p>{{ cars.year }}</p>
            <p :style="{ color: cars.color }">{{ cars.color }}</p>

            <b-img src="@/assets/img.jpg" fluid alt="Fluid image"></b-img>

            <p style="text-align:right">Owner : {{ cars.owner }}</p>
          </b-card-text>
        </b-card>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
  import axios from "axios";
  export default {
    data() {
      return {
        car: [],
        search: "",
        select: "",
        years: ["", 2000, 2001, 2002, 2003, 2004, 2005, 2006, 2007],
      };
    },
    mounted() {
      axios
        .get("https://api.jsonbin.io/b/5f33f98ddddf413f95c2b306", {
          headers: {
            "secret-key":
              "$2b$10$0ve8/zpqfEF0X1kZ0TdfW.ehq645eiEhc.OykoUZABVEdE8D3bpr2",
          },
        })
        .then((response) => {
          this.car = response.data;
          console.log(this.car);
        });
    },
    methods: {
      deletecar() {
        console.log('delete')
      },
    },
    computed: {
      sortFunc: function() {
        let filtered = this.car;
        if (this.search) {
          filtered = this.car.filter(
            (m) => m.model.toLowerCase().indexOf(this.search) > -1
          );
          return filtered;
        }
        if (this.select) {
          filtered = filtered.filter((m) => m.year === this.select);
          return filtered;
        } else {
          let filtered = this.car.filter((cars) => {
            return cars.year >= 2000 && cars.year <= 2007;
          });
          return filtered.slice().sort(function(a, b) {
            return a.year > b.year ? 1 : -1;
          });
        }
      },
    },
  };
</script>
<style scoped>
  .icondelete {
    color: #cbcbcb;
    font-size: 20px;
    position: absolute;
    right: 10px;
    top: 15px;
  }
</style>
