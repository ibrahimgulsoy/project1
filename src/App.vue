<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="site logo">
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />

    <!-- <p>{{ jobs[0].title }} </p> -->
    <!--<p>{{ name }} - {{ age }} {{ message }}</p>

    <button @click="changeName('taha', 25)">change taha</button>
    <button @click="changeName('ibrahim', 30)">change ibrahim</button>
    <button @click="changeAge('20')">change age</button>
    <input v-model="message" />-->
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import JobList from "./components/JobList.vue";
import Job from "@/types/Job";
import OrderTerm from "@/types/OrderTerm";

const name = ref("Link");
const age = ref<number | string>(0);
const message = ref("");
components: {
  JobList;
}

const jobs = ref<Job[]>([
  { title: "Farm worker", location: "lon lon ranch", salary: 30000, id: "1" },
  { title: "Quarryman", location: "death mountain", salary: 40000, id: "2" },
  { title: "Flute player", location: "the lost woods", salary: 35000, id: "3" },
  { title: "Fisherman", location: "lake hylia", salary: 21000, id: "4" },
  { title: "Prison guard", location: "gerudo valley", salary: 32000, id: "5" },
]);
const order = ref<OrderTerm>("title");
const handleClick = (term: OrderTerm) => {
  order.value = term;
  return { jobs, handleClick };
};


/*const changeName = (newName: string, newAge: number) => {
  name.value = newName;
  age.value = newAge;
  changeAge(age.value);
};*/

const changeAge = (newAge: string | number) => {
  age.value = newAge;
};

</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
header .title {
  display: flex;
  justify-content: center;
}
header img {
  width: 60px;
  margin-right: 20px;
}
header h1{
  font-size: 3em;
}
</style>
