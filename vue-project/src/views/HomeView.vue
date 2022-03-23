<script setup lang="ts">
import { ref } from "vue";
const config = {
  url: "https:newsapi.org/v2/everything?q=Apple&from=2022-03-17&sortBy=popularity&apiKey=4ffc85bf805e42bd9967a8ef3a0e387b",
};
const leftBox = ref(null);

function getTitle() {
  fetch(config.url)
    .then((response) => response.json())
    .then(function (data) {
      for (let news in data.articles) {
        console.log(data.articles[news].title);
        let div = document.createElement("div");
        div.innerHTML = `
        <a href="${data.articles[news].url}">
        <div class="bg-white m-7 card overflow-hidden border rounded-lg">
          <div class="relative pb-52">
            <img
              class="absolute h-full w-full object-cover"
              src="${data.articles[news].urlToImage}"
            />
          </div>
          <div class="p-5 text-center overflow-hidden">
            <h4 class="text-2xl font-bold mb-2">${data.articles[news].title}</h4>
            <p>${data.articles[news].description}</p>
          </div>
        </div>
        </a>
        `;
        leftBox.value.querySelectorAll(".title")[0].append(div);
      }
    });
}
getTitle();
</script>
<template>
  <div class="bg-white head heading flex justify-between p-10 items-center">
    <p class="text-4xl">Destination Info.</p>
    <div>
      <input
        type="text"
        class="rounded-l-lg p-2 border-indigo-700 border-2 text-2xl"
        name="search"
        placeholder="where to ..."
      />
      <button
        class="btn rounded-r-lg bg-indigo-700 border-indigo-700 border-2 p-2 text-2xl text-white"
        type="submit"
      >
        Search by destination
      </button>
    </div>
  </div>
  <div ref="leftBox" class="box bg-gray-800">
    <div class="grid grid-cols-3 grid-rows-3 grid-flow-row">
      <!-- googlenews-->
      <div
        class="upper-left-box row-span-3 title snap-x overflow-x-scroll"
      ></div>
      <!--次のやつ-->
      <div class="col-span-2 heading text-white">
        <div class="m-7 p-7">
          <h4 class="text-7xl">Travel to..</h4>
          <p>the desitaion's infomation currently..</p>
        </div>
      </div>

      <div class="upper-box row-span-1 col-span-1">
        <div class="bg-white long-card m-7 border rounded-lg">
          <div class="relative pb-20">
            <img
              class="absolute h-full w-full object-cover"
              src="../images/photo1.jpg"
            />
          </div>
          <div class="p-5">
            <h4>Wakayama prefecture</h4>
          </div>
        </div>
      </div>
      <div class="upper-box row-span-1 col-span-1">
        <div class="bg-white long-card m-7 border rounded-lg">
          <div class="relative pb-20">
            <img
              class="absolute h-full w-full object-cover"
              src="../images/photo1.jpg"
            />
          </div>
          <div class="p-5">
            <h4>Wakayama prefecture</h4>
          </div>
        </div>
      </div>
      <div class="upper-box row-span-1 col-span-1">
        <div class="bg-white long-card m-7 border rounded-lg">
          <div class="relative pb-20">
            <img
              class="absolute h-full w-full object-cover"
              src="../images/photo1.jpg"
            />
          </div>
          <div class="p-5">
            <h4>Wakayama prefecture</h4>
          </div>
        </div>
      </div>
      <div class="upper-box row-span-1 col-span-1">
        <div class="bg-white long-card m-7 border rounded-lg">
          <div class="relative pb-20">
            <img
              class="absolute h-full w-full object-cover"
              src="../images/photo1.jpg"
            />
          </div>
          <div class="p-5">
            <h4>Wakayama prefecture</h4>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.head {
  height: 10vh;
  width: 100%;
}
.box {
  width: 100%;
  height: 90vh;
}
.card {
  height: 400px;
  width: 400px;
}
.upper-left-box {
  width: 100%;
  height: 90vh;
}
.grid {
  height: 90vh;
}
.long-card {
  height: 200px;
  width: 90%;
}
.heading {
  font-family: Georgia;
}
</style>
