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
<div class="circle-box-item">
  {#each [...Array(12)] as _, i}
    <div>{i + 1}</div>
  {/each}
</div>

<style>
  .circle-box {
    display: flex;
    column-gap: 10px;
    overflow-x: auto;
    white-space: nowrap;
    padding: 10px;
    background-color: #fff;
    border-bottom: 1px solid #646b63;
  }

  .circle {
    height: 130px;
    width: 130px;
    min-width: 130px;
    border-radius: 50%;
    background-color: #646b63;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    cursor: pointer;
  }

  .circle:focus {
    background-color: #c1876b;
  }

  .circle-box::-webkit-scrollbar {
    width: 0;
    height: 0;
  }

  .circle-box-item {
    display: grid;
    flex-wrap: wrap;
    grid-template-columns: 2fr 2fr 2fr 2fr 2fr 2fr;
    background-color: #fff;
    padding: 10px 20px 10px 20px;
    column-gap: 10px;
    row-gap: 10px;
  }

  .circle-box-item > div {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 30px;
    border-radius: 5px;
  }
  .circle-box-item > div:hover {
    color: red;
  }
</style>
