<script>
  /* load colors */
  import colors_json from "$lib/config/color_palette.json";
  const COLORS = colors_json;

  $: outerWidth = 0
</script>

<svelte:window bind:outerWidth />

<!-- Outermost container which premits overflowing -->
<div style="overflow: visible;">
  <!-- Navigation Bar -->
  <div style="width: 100%; height: 20px; background-color: green; margin: 0px">
    hi
  </div>
  <div class="floating_div">
  </div>
</div>
