<script>
  import { onMount } from "svelte";
  import Draggable from "../components/Draggable.svelte";
  export let name = "NAMEOFSERVER";
  export let hostname = "";
  onMount(() => (hostname = window.location.href));
</script>

<div class="container noselect">
  <div class="inner">
    <p class="title">{name}</p>
    <div class="blink-dot"></div>
  </div>
  <Draggable>
    <p>{hostname}</p>
  </Draggable>
  <div class="nebula-div">***</div>
</div>

<style>
  .container {
    --dot-bg: #07080a;
    --dot-color: #242424;
    --dot-size: 2px;
    --dot-space: 30px;
    background:
      linear-gradient(
          90deg,
          var(--dot-bg) calc(var(--dot-space) - var(--dot-size)),
          transparent 1%
        )
        center / var(--dot-space) var(--dot-space),
      linear-gradient(
          var(--dot-bg) calc(var(--dot-space) - var(--dot-size)),
          transparent 1%
        )
        center / var(--dot-space) var(--dot-space),
      var(--dot-color);
    width: 100vw;
    height: 100vh;
    background-origin: border-box;
    overflow: hidden;
  }
  :global(p) {
    font-family: monospace;
    color: #3c3c3c;
  }
  .inner {
    position: absolute;
    padding-top: 15px;
    padding-left: 10px;
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    gap: 5px;
  }
  .title {
    background-color: #07080a;
  }
  :global(body) {
    margin: 0;
    padding: 0;
    background-color: #07080a;
    box-sizing: border-box;
  }
  .blink-dot {
    width: 5px;
    height: 5px;
    align-self: center;
    background-color: green;
    border-radius: 50%;
    animation: blink 1s infinite;
  }

  @keyframes blink {
    50% {
      opacity: 0;
    }
  }
  .nebula-div {
    position: absolute;
    bottom: 10px;
    right: 10px;
    font-size: 6rem;
    color: #a5a5a5;
    font-family: monospace;
    background-color: #07080a;
  }
  .noselect {
    -webkit-touch-callout: none;
    -webkit-user-select: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }
</style>
