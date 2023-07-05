<div class="navbar">
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <h2 on:click={() => window.location.replace("/", "_self")}>
    Animation Style
  </h2>
  <div class="profile">
    <h4>Dee</h4>
    <img
      src="https://images.unsplash.com/photo-1547425260-76bcadfb4f2c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80"
      alt="profile"
    />
  </div>
</div>

<style>
  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 60px;
    padding: 0 10px 0 10px;
    background-color: #646b63;
    color: #fff;
  }
  .navbar > h2 {
    cursor: pointer;
  }
  .profile {
    display: flex;
    align-items: center;
    column-gap: 10px;
  }
  .profile > img {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    object-fit: cover;
  }
</style>
