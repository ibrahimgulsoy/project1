<template>
  <div class="app">      
    <JobList :jobs="jobs"/>

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
import type Job from '@/types/Job'


const name = ref("Link");
const age = ref<number | string>(0);
const message = ref('');
components: {JobList}


const jobs = ref<Job[]>([
  { title: 'Farm worker', location: 'lon lon ranch', salary: 30000, id: '1' },
  { title: 'Quarryman', location: 'death mountain', salary: 40000, id: '2' },
  { title: 'Flute player', location: 'the lost woods', salary: 35000, id: '3' },
  { title: 'Fisherman', location: 'lake hylia', salary: 21000, id: '4' },
  { title: 'Prison guard', location: 'gerudo valley', salary: 32000, id: '5' }
]);

const changeName = (newName: string, newAge: number) => {
  name.value = newName;
  age.value = newAge;
  changeAge(age.value);
};

const changeAge = (newAge: string | number) => {
  age.value = newAge;
};
</script>

<style>
 
</style>
