<script>
  export let font_size = 60;
  export let texts = ["Hello", "World"];

  let _current_text = texts[0];
  let i = 0;
  let display_time_out = 0;
  function updateText() {
    if (_current_text !== "") {
      _current_text = _current_text.slice(0, -1);
      return;
    }
    i++;
    if (texts[i] === undefined) {
      i = 0;
    }
    _current_text = texts[i];
  }
  setInterval(updateText, 1000);
</script>

<div id="item_container" style="width: 60%;">
  <div class="hbar" />
  <p style="font-size: {font_size}px;">
    {_current_text}
  </p>
  <div class="hbar" />
</div>

<style>
  .hbar {
    width: 100%;
    background-color: black;
    height: 1px;
  }
  p {
    justify-self: center;
  }
</style>
