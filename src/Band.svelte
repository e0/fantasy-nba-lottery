<script>
  export let items = [];

</script>

<style>
  @keyframes box {
    from {
      transform: rotateX(0deg);
    }
    to {
      transform: rotateX(360deg);
    }
  }

  .box-wrapper {
    width: 100px;
    height: 100px;
    overflow: hidden;
  }

  .box {
    width: 100px;
    height: 100px;
    animation: box 2s linear infinite;
    transform-style: preserve-3d;
    transform-origin: center center -50px;
  }

  .digit {
    position: absolute;
    width: 100px;
    height: 100px;
    border-radius: 50px;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 42px;
  }

</style>

<div class="box-wrapper">
  <div class="box">
    <div class="digit bg-green-500">1</div>
    <div class="digit bg-red-500"
      style="transform: rotateX(-90deg) translate3d(0, 50px, 50px);"
    >2</div>
    <div class="digit bg-purple-500"
      style="transform: rotateX(-180deg) translate3d(0, 0, 100px);"
    >3</div>
    <div class="digit bg-blue-500"
      style="transform: rotateX(-270deg) translate3d(0, -50px, 50px);"
    >4</div>
  </div>
</div>

<!--
<ul>
  {#each items as item, i}
    <li
      class="absolute w-32 h-32 p-10 rounded bg-gray-300 opacity-30"
      style="transform: rotate3d(1, 0, 0, {360 / items.length * i}deg);"
    >
      {item}
    </li>
  {/each}
</ul>
//-->

