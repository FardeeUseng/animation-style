<script>
  import "./aninmationGroup.css";
  import { navigate } from "svelte-routing";
  import animGroupList from "./animation-group-list.json";

  export let g;
  export let v;
  export let setGroup;
  export let setVarious;
  export let handleVActive;

  const handleChangeParams = (group, various) => {
    if (various) setVarious(various);
    if (group) setGroup(group);
    navigate(`/basic?g=${group}&v=${various || ""}`, { replace: true });
    handleVActive();
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
  {#each animGroupList as item}
    <div class="circle-group">
      <button
        style="background-color: {item.key === g ? '#c1876b' : ''};"
        class="circle"
        on:click={() => handleChangeParams(item.key)}
      >
        <h4>{item.label}</h4>
      </button>
      {#if item.key === g}
        <div>
          <i class="fa-solid fa-caret-up" />
        </div>
      {/if}
    </div>
  {/each}
</div>
<div class="circle-box-item">
  {#each animVariousList.item as item}
    <button
      class={v === item.label ? "isVariousSelected" : ""}
      on:click={() => handleChangeParams(g, item.label)}
    >
      {item.label}
    </button>
  {/each}
</div>
