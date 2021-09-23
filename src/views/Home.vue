<template>
  <div class="container mx-20 mt-32">
    <div class="flex space-x-12">
      <div>
        <span class="font-medium text-purple-900">Halo Gamers</span>
        <h1 class="font-bold text-6xl text-purple-900">Topup Gaming</h1>

        <p class="w-72 mt-20 font-bold text-purple-600">
          Kami menyediakan jutaan cara untuk membantu players menjadi pemenang
          sejati
        </p>
        <div class="m-3 p-5 space-x-10">
          <button class="w-56 p-5 bg-blue-600 rounded-full font-bold text-blue-200">
            Get started
          </button>
          <a href="">Learn More</a>
        </div>
      </div>
      <div class="w-3/5">
        <img
          class="rounded-3xl shadow-lg"
          src="https://www.epingi.com/wp-content/uploads/2020/03/Battlefield-5-PC-Version-Full-Game-Setup-Free-Download.jpg.webp"
          alt="jpg"
        />
      </div>
    </div>
    <div class="mt-28">
      <h1 class="font-bold text-5xl p-5 text-purple-900">Games</h1>
      <div class="w-full flex flex-wrap mt-6">
        <div class="w-1/7" v-for="(arr, idx) in subArrays" :key="idx">
          <div v-for="(game, idx) in arr" :key="idx">
            <div class="w-full p-2">
              <CardPC :game="game" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import { reactive, toRefs } from "vue";
import axios from "axios";
import CardPC from "../components/CardPC/CardPC.vue";

export default {
  name: "Home",
  components: {
    CardPC,
  },
  data() {
    return {
      games: [],
    };
  },
  computed: {
    subArrays() {
      let length = Math.ceil(this.games.length / 3);

      const result = new Array(length).fill().map((i) => {
        console.log(i)
        return this.games.splice(0, length);
      });

      return result;
    },
  },
  mounted() {
    axios({
      method: "GET",
      url: "https://free-epic-games.p.rapidapi.com/free",
      headers: {
        "x-rapidapi-host": "free-epic-games.p.rapidapi.com",
        "x-rapidapi-key": "6a7327da9dmshab9b848bd86bd5cp1b091djsn1fe6f22c68d1",
      },
    })
      .then((res) => {
        this.games = res.data.freeGames.current;
        console.log(res.data.freeGames.current);
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>
