<script>
  import color from "$lib/storage/color_palette.json";

  const COLOR_THEME = color.general_container_style;
  export let color_theme = COLOR_THEME.default;
</script>

<div
  id="item_container"
  style="
    background-color: {color_theme.color};
    border-radius: {color_theme.b_radius};
    border-style: {color_theme.b_style};
    border-width: {color_theme.b_width};
    border-color: {color_theme.b_color};
    border-right-width: {color_theme.b_right_width};
    border-bottom-width: {color_theme.b_bottom_width};
    padding: {color_theme.padding};
  "
>
  <slot />
</div>

<style>
  #item_container {
    display: flex;
    align-items: center;
  }
</style>
