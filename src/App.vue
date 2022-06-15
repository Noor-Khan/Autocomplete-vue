<template>
  <div id="app" style="display: flex; justify-content: space-around">
    <div class="form-group">
      <label class="text-uppercase font-weight-bold">Address</label>
      <input v-model="search" type="text" class="form-control" />
      <ul v-if="search">
        <li v-for="(list, index) in filterArr" :key="index">
          <button @click="getItem(list)">
            {{ list }}
          </button>
        </li>
      </ul>
    </div>
    <p>selected obj: {{ selectedObj }}</p>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      search: "",
      selectedObj: null,
      arr: [
        {
          currency: "USDT",
          userID: "6877fded-57e9-42de-80b6-45bd01f15b03",
          updatedAt: "2022-06-13T09:49:15.305Z",
          createdAt: "2022-06-13T09:49:15.305Z",
          address: "TFwZVeEuE3soB1S1PocFHb38pFCiw9QAkL",
          id: "6877fded-57e9-42de-80b6-45bd01f15b03-TFwZVeEuE3soB1S1PocFHb38pFCiw9QAkL",
          name: "Camaechi Autos",
        },
        {
          currency: "ETH",
          userID: "6877fded-57e9-42de-80b6-45bd01f15b03",
          updatedAt: "2022-06-13T09:49:15.305Z",
          createdAt: "2022-06-13T09:49:15.305Z",
          address: "TFyZVeEuE3soB1S1PocFHb38pFCiw9QAkL",
          id: "6877fded-57e9-42de-80b6-45bd01f15b03-TFwZVeEuE3soB1S1PocFHb38pFCiw9QAkL",
          name: "Desmond",
        },
      ],
    };
  },
  methods: {
    getItem(item) {
      this.selectedObj = item;
    },
  },
  computed: {
    filterArr() {
      return this.arr.filter((item) => {
        return (
          item.currency.toLowerCase().includes(this.search.toLowerCase()) ||
          item.address.toLowerCase().includes(this.search.toLowerCase()) ||
          item.name.toLowerCase().includes(this.search.toLowerCase())
        );
      });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
