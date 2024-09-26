<script>
  /* load colors */
  import Button from "$lib/page_item/Button.svelte";
  
  import colors_json from "$lib/storage/color_palette.json";
  const COLORS = colors_json;

</script>

<!-- Outermost container which allows overflowing -->
<div style="width: 100$;">
  <!-- Navigation Bar -->
  <div style="width: 100%; margin: 0px">
    <Button color_theme={COLORS.button.type_black}
      text_size="10px"
      text_val="hi"/>
  </div>
  <div class="floating_div">
  </div>
</div>
