<script>
  export let left = getRandomInt(500);
  export let top = getRandomInt(500);

  let moving = false;

  function onMouseDown() {
    moving = true;
  }

  function onMouseMove(e) {
    if (moving) {
      left += e.movementX;
      top += e.movementY;
    }
  }

  function onMouseUp() {
    moving = false;
  }

  function getRandomInt(max) {
    return Math.floor(Math.random() * max);
  }

  // 	$: console.log(moving);
</script>

<section
  on:mousedown={onMouseDown}
  style="left: {left}px; top: {top}px;"
  class="draggable"
  role="textbox"
  tabindex="0"
>
  <slot />
</section>

<svelte:window on:mouseup={onMouseUp} on:mousemove={onMouseMove} />

<style>
  .draggable {
    user-select: none;
    cursor: move;
    border: solid 1px darkgrey;
    position: absolute;
    font-size: larger;
    padding: 5px;
  }
</style>
