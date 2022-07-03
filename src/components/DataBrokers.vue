<script>
import axios from "axios";

const requestBrokers = () => {
  let brokers = []

  axios
    .get("http://localhost:3000/data_brokers")
    .then(response => {
      console.log(response)
      brokers = response.data.brokers
    })
    .catch(err => console.log(err))
    .then(() => console.log("Done"))

  return brokers
}

let brokers = await requestBrokers()
</script>

<template>
  <li v-for="broker in brokers">
    {{ broker.name }}
  </li>
</template>
