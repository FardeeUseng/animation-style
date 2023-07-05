<script>
  import "./scaleUp.css";

  export let v;
  export let isVActive;
  export let handleVActive;
  let isLoveActive = false;
</script>

<div class="anim-control">
  <button on:click={handleVActive}>
    <i class="fa-solid fa-rotate-right" />
  </button>
  <button on:click={() => (isLoveActive = !isLoveActive)}>
    <i class="fa-{isLoveActive ? 'solid' : 'regular'} fa-heart" />
  </button>
  <button><i class="fa-solid fa-code" /></button>
</div>

<div class="scale-up-box">
  <div class="scale-up {isVActive ? v : ''}" />
</div>
