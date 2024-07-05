<div class="container">
  <p class="title">i know where you are!</p>
  <div class="data">
    <p>continent: europe</p>
    <p>country: Spain</p>

    <p>city: Madrid</p>
    <p>local time: 20:13</p>
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
  }

  .data {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .data > p {
    font-size: 1.5rem;
    text-transform: capitalize;
    margin: 0;
  }
</style>
