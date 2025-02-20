<script>
  // With helps from ChatGPT
  let triggered = false;

  export let react = () => {};

  // Toggle the open state when the button is clicked
  function toggle() {
    triggered = !triggered;
    react();
  }
</script>

<!-- Button with transition -->
<button class="triple_bar" on:click={toggle} class:triggered>
  <div class="bar"></div>
  <div class="bar"></div>
  <div class="bar"></div>
</button>

<style>
  .triple_bar {
    margin: 0px;
    padding: 4px;
    border-width: 0px;
    cursor: pointer;
    display: grid;
    row-gap: 3px;
    background-color: rgba(0, 0, 0, 0);
    justify-content: center;
  }

  .bar {
    border-width: 0px;
    border-radius: 2px;
    width: 25px;
    height: 3px;
    background-color: #ffffff;
    transition:
      transform 0.3s ease,
      opacity 0.3s ease;
  }

  .triggered .bar:nth-child(1) {
    transform: translate(0px, 6px) rotate(45deg);
  }
  .triggered .bar:nth-child(2) {
    opacity: 0;
  }
  .triggered .bar:nth-child(3) {
    transform: translate(0px, -6px) rotate(-45deg);
  }
</style>
