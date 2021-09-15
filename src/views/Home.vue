<template>
  <div class="container mx-20 mt-40">
    <div class="flex space-x-72">
      <div>
        <span class="font-medium text-purple-900">Halo Gamers</span>
        <h1 class="font-bold text-6xl text-purple-900">Topup Gaming</h1>

        <p class="w-72 mt-20 font-bold text-purple-600">
          Kami menyediakan jutaan cara untuk membantu players menjadi pemenang
          sejati
        </p>
        <div class="m-5 p-5 space-x-10">
          <button class="w-56 p-5 bg-blue-600 rounded-full text-blue-200">
            Get started
          </button>
          <a href="">Learn More</a>
        </div>
      </div>
      <div class="w-96">
        <img
          src="https://media.contentapi.ea.com/content/dam/gin/images/2021/06/battlefield-2042-key-art.jpg.adapt.crop1x1.767p.jpg"
          alt="jpg"
        />
      </div>
    </div>
    <div>
      <h1 class="font-bold text-4xl p-5">Games Category</h1>
      <div 
      v-for="(pc, idx) in productionCompanies"
      :key="idx"
      >
      
      <CardPC  :pc="pc"/>

      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import { reactive, toRefs } from "vue";
import CardPC from "../components/CardPC/CardPC.vue"

export default {
  name: "Home",
  components: {
    CardPC
  },
  setup() {
    const state = reactive({
      productionCompanies: [],
    });

    fetch(
      "https://api.themoviedb.org/3/movie/550?api_key=90a3c5e5e5e365ab277ee5e39ee0971f"
    )
      .then((res) => res.json())
      .then((data) => {
        state.productionCompanies = data.production_companies;
        console.log(data.production_companies);
      });

    return { ...toRefs(state) };
  },
};
</script>
