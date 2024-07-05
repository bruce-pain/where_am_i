<script lang="ts">
  import { onMount } from "svelte";

  let payload: any;
  let clientIP: any;
  let geoData: any;

  let continent: any;
  let country: string;
  let city: string;
  let region: string;
  let localTime: any;

  let options: RequestInit = {
    method: "GET",
    headers: {
      "Content-Type": "application/json",
    },
  };

  onMount(async () => {
    const dataResponse = await fetch(
      `https://where-am-i-api.vercel.app/api/get-me`,
      options
    );

    payload = await dataResponse.json();

    console.log(payload);

    clientIP = payload["client_ip"];
    geoData = payload["geodata"];

    continent = geoData["continent"];
    country = geoData["country"];
    city = geoData["city"];
    region = geoData["region"];
    localTime = geoData["localtime"];
  });
</script>

<div class="container">
  <p class="title">i know where you are!</p>
  <p class="subtitle">your IP address: {clientIP}</p>
  <div class="data">
    <p>continent: {continent}</p>
    <p>country: {country}</p>

    <p>region: {region}</p>
    <p>city: {city}</p>
    <p>local time: {localTime}</p>
  </div>
</div>

<style>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .title {
    font-weight: 700;
    font-size: 3rem;
    text-align: center;
    text-transform: capitalize;
    margin: 0;
  }

  .subtitle {
    font-weight: 700;
    font-size: 2rem;
    text-align: center;
    text-transform: capitalize;
  }

  .data {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .data > p {
    text-align: center;
    font-size: 1.5rem;
    text-transform: capitalize;
    margin: 0;
  }
</style>
