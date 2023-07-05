<div class="home-page">
  <h1>Animation Style</h1>
  <button on:click={() => window.location.assign("/basic")}>START</button>
</div>

<style>
  .home-page {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 90%;
  }

  .home-page > h1 {
    font-size: 60px;
    margin-bottom: 50px;
  }

  .home-page > button {
    height: 100px;
    width: 100px;
    border-radius: 50%;
    cursor: pointer;
    border: none;
    background-color: #dc9d00;
    font-weight: 500;
    font-size: 22px;
    color: #1d1e33;
    box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
  }
</style>
