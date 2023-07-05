<script>
  import ScaleUp from "../../components/anim-basic/scale-up/ScaleUp.svelte";
  import AnimationGroup from "../../components/animation-group/AnimationGroup.svelte";

  let params = new URLSearchParams(window.location.search);
  let g = params.get("g") || "scale-up";
  let v = params.get("v");

  let isVActive = false;

  const setGroup = (group) => {
    g = group;
  };
  const setVarious = (various) => {
    v = various;
  };
  const handleVActive = () => {
    isVActive = true;
    setTimeout(() => {
      isVActive = false;
    }, 400);
  };
</script>

<div>
  <AnimationGroup {handleVActive} {g} {v} {setGroup} {setVarious} />
  <ScaleUp {handleVActive} {v} {isVActive} />
</div>
