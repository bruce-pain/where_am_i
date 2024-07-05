<script lang="ts">
  let options: RequestInit = {
    method: "GET",
    headers: {
      "Content-Type": "application/json",
    },
  };

  const getGeoData = async () => {
    const dataResponse = await fetch(
      `https://where-am-i-api.vercel.app/api/get-me`,
      options
    );

    let payload = await dataResponse.json();

    console.log(payload);

    return payload;
  };
</script>

<div class="container">
  <p class="title">i know where you are!</p>
  {#await getGeoData()}
    <p>fetching data...</p>
  {:then data}
    <p class="subtitle">your IP address: {data["client_ip"]}</p>
    <div class="data">
      <p>continent: {data["geodata"]["continent"]}</p>
      <p>country: {data["geodata"]["country"]}</p>

      <p>region: {data["geodata"]["region"]}</p>
      <p>city: {data["geodata"]["city"]}</p>
      <p>local time: {data["geodata"]["localtime"]}</p>
    </div>
  {/await}
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
