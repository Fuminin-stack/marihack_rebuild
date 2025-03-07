<script>
  import color from "$lib/storage/color_palette.json";
  import { tweened } from "svelte/motion";

  const COLOR_THEME = color.general_container_style.default;

  export let is_desktop = false;
  const images = import.meta.glob("../../images/carousel/*", {
    eager: true,
    query: "?url",
    import: "default",
  });

  let imageList = Object.values(images);
  let iter_index = 0;
  let iter_index_next = 1;
  $: current_img = imageList[iter_index];
  $: next_img = imageList[iter_index_next];
  let _opacity = tweened(1, {
    duration: 100,
  });
  let stat = 0;
  if (is_desktop) {
    1 + 1;
  }

  function switchPhotoForward() {
    switch (stat) {
      case 0: // opacity 1 to 0
        _opacity.set(0);
        break;
      case 1: // opacity 0, switch current to next image
        iter_index = (iter_index + 1) % imageList.length;
        break;
      case 2: // opacity 0 to 1
        _opacity.set(1);
        break;
      default: // opacity 1, switch next image to next next image
        iter_index_next = (iter_index_next + 1) % imageList.length;
        break;
    }
    stat = (stat + 1) % 4;
  }

  setInterval(switchPhotoForward, 1000);
</script>

<div
  id="item_container"
  style="
  border-color: {COLOR_THEME.b_color};
  border-style: {COLOR_THEME.b_style};
  border-radius: {COLOR_THEME.b_radius};
  border-width: {COLOR_THEME.b_width};
  border-bottom-width: {COLOR_THEME.b_bottom_width};
  border-right-width: {COLOR_THEME.b_right_width};
  "
>
  <div id="current_img">
    <img src={String(next_img)} alt="i" />
  </div>
  <img src={String(current_img)} alt="i" style="opacity: {$_opacity};" />
</div>

<style>
  #item_container {
    overflow: hidden;
    line-height: 0px;
  }
  #current_img {
    height: 0px;
    overflow: visible;
  }
  img {
    width: 100%;
  }
</style>
