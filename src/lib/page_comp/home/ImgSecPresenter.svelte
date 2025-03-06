<script>
  import color from "$lib/storage/color_palette.json";

  const COLOR_THEME = color.general_container_style.default;

  export let is_desktop = false;
  const images = import.meta.glob("../../images/carousel/*", {
    eager: true,
    query: "?url",
    import: "default",
  });

  let imageList = Object.values(images);
  let iter_index = 0;
  $: current_img = imageList[iter_index];
  if (is_desktop) {
    1 + 1;
  }

  function switchPhotoForward() {
    iter_index = (iter_index + 1) % imageList.length;
  }

  function switchPhotoBackward() {}

  setInterval(switchPhotoForward, 4000);
</script>

<div
  style="
  border-style: {COLOR_THEME.b_style};
  border-radius: {COLOR_THEME.b_radius};
  border-width: {COLOR_THEME.b_width};
  border-bottom-width: {COLOR_THEME.b_bottom_width};
  border-right-width: {COLOR_THEME.b_right_width};
  "
>
  <img src={String(current_img)} alt="i" />
</div>

<style>
  div {
    overflow: hidden;
    line-height: 0px;
  }
  img {
    width: 120%;
  }
</style>
