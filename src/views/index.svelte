<script>
  let circleBox;
  let isDragging = false;
  let startX = 0;
  let scrollLeft = 0;

  function handleMouseDown(event) {
    isDragging = true;
    startX = event.clientX - circleBox.offsetLeft;
    scrollLeft = circleBox.scrollLeft;
  }

  function handleMouseMove(event) {
    if (!isDragging) return;
    const x = event.clientX - circleBox.offsetLeft;
    const walk = (x - startX) * 2;
    circleBox.scrollLeft = scrollLeft - walk;
  }
</script>

<div
  class="circle-box"
  bind:this={circleBox}
  on:mousedown={handleMouseDown}
  on:mouseup={() => (isDragging = false)}
  on:mouseleave={() => (isDragging = false)}
  on:mousemove={handleMouseMove}
>
  {#each [...Array(23)] as _, i}
    <div class="circle"><h3>{i + 1}</h3></div>
  {/each}
</div>

<style>
  .circle-box {
    display: flex;
    column-gap: 10px;
    margin: 10px 0;
    overflow-x: auto;
    white-space: nowrap;
    border: 1px solid red;
  }

  .circle {
    height: 100px;
    width: 100px;
    min-width: 100px;
    border-radius: 50%;
    background-color: #646b63;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
  }

  .circle-box::-webkit-scrollbar {
    width: 0;
    height: 0;
  }
</style>
