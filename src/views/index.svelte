<script>
  import { navigate } from "svelte-routing";
  let params = new URLSearchParams(window.location.search);
  let g = params.get("g");
  let v = params.get("v");

  const handleChangeParams = (group, various) => {
    if (group) g = group;
    if (various) v = various;
    navigate(`/?g=${g}&v=${v}`, { replace: true });
  };

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
  {#each ["scale-up", "scale-down", "rotate", "rotate-scale", "rotate-90", "flip", "flip-2", "flip-scale", "flip-scale-2", "swing", "slide", "slide-bck", "slide-fwd", "slide-rotate", "shadow-drop", "shadow-drop-2", "shadow-pop", "shadow-inset"] as group}
    <div class="circle-group">
      <button
        style="background-color: {group === g ? '#c1876b' : ''};"
        class="circle"
        on:click={() => handleChangeParams(group)}
      >
        <h4>{group}</h4>
      </button>
      {#if group === g}
        <div>
          <i class="fa-solid fa-caret-up" />
        </div>
      {/if}
    </div>
  {/each}
</div>
<div class="circle-box-item">
  {#each [...Array(12)] as _, i}
    <button
      class={v === i + 1 ? "isVariousSelected" : ""}
      on:click={() => handleChangeParams(_, i + 1)}>{i + 1}</button
    >
  {/each}
</div>
<p>{g}</p>

<style>
  .circle-box {
    display: flex;
    column-gap: 10px;
    overflow-x: auto;
    white-space: nowrap;
    padding: 10px 10px 0 10px;
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
    border: none;
    font-size: 15px;
    text-transform: uppercase;
  }

  .circle-group > div {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .circle-group > div > i {
    padding: 0;
    height: 10px;
    color: #646b63;
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
    row-gap: 3px;
  }

  .circle-box-item > button {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 30px;
    border-radius: 5px;
    border: none;
    background-color: #fff;
    cursor: pointer;
  }
  .circle-box-item > button:hover {
    color: red;
  }

  .isVariousSelected {
    background-color: #c1876b !important;
    color: #fff;
  }
  .isVariousSelected:hover {
    color: #fff !important;
  }
</style>
