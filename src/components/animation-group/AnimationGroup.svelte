<script>
  import "./aninmationGroup.css";
  import { navigate } from "svelte-routing";
  import animGroupList from "./animation-group-list.json";

  let params = new URLSearchParams(window.location.search);
  let g = params.get("g") || "scale-up";
  let v = params.get("v");

  const handleChangeParams = (group, various) => {
    if (group) g = group;
    if (various) v = various;
    navigate(`/basic?g=${group}&v=${various || ""}`, { replace: true });
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

  $: animVariousList = animGroupList.find((group) => group.key === g);
</script>

<div
  class="circle-box"
  bind:this={circleBox}
  on:mousedown={handleMouseDown}
  on:mouseup={() => (isDragging = false)}
  on:mouseleave={() => (isDragging = false)}
  on:mousemove={handleMouseMove}
>
  {#each animGroupList as group}
    <div class="circle-group">
      <button
        style="background-color: {group.key === g ? '#c1876b' : ''};"
        class="circle"
        on:click={() => handleChangeParams(group.key)}
      >
        <h4>{group.label}</h4>
      </button>
      {#if group.key === g}
        <div>
          <i class="fa-solid fa-caret-up" />
        </div>
      {/if}
    </div>
  {/each}
</div>
<div class="circle-box-item">
  {#each animVariousList.item as various}
    <button
      class={v === various.label ? "isVariousSelected" : ""}
      on:click={() => handleChangeParams("", various.label)}
    >
      {various.label}
    </button>
  {/each}
</div>
