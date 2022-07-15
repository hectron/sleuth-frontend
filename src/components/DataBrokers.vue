<script setup>
import { ref, onMounted } from "vue"
import axios from "axios";

const brokers = ref([])

const requestBrokers = async () => {
  axios
    .get("http://localhost:3000/data_brokers")
    .then(response => {
      brokers.value = response.data.brokers
    })
    .catch(err => console.log(err))
    .then(() => console.log("Done"))
}

onMounted(async () => {
  requestBrokers();
})
</script>

<template>
  <li v-for="broker in brokers">
    {{ broker }}
    <a :href="broker.url"> {{ broker.name }} - {{ broker.notes }}</a>
  </li>
</template>
