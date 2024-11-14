<script>
// color palette
import color_json from "$lib/storage/color_palette.json";
import constants_json from "$lib/storage/constants.json";
import duck_logo_img from "$lib/images/duck_logo.png";
const CST = constants_json;
let clientWidth = 0;
let title_font_size = 0;
let shadow_size = 0;
let duck_logo = duck_logo_img;
$: {
  if (clientWidth > CST.sizes.mob_width) {}
  title_font_size = 140 * clientWidth / 1920;
  shadow_size = 4 * clientWidth / 1920;
}
const COLOR = color_json;
</script>

<svelte:head>
  <title>MariHacks</title>
</svelte:head>

<!-- sec stands for section -->
<div bind:clientWidth={clientWidth}
  id="sec_title"
  style="
    width: {clientWidth > CST.sizes.mob_width ? 100 : 80 + '%'};
  "
>
  <div id="sec_title_left">
    <p style="
      color: {COLOR.pages.home.title.text};
      text-shadow: {shadow_size}px {shadow_size}px 0px {COLOR.pages.home.title.shadow};
      -webkit-text-stroke-width: 2px;
      -webkit-text-stroke-color: {COLOR.pages.home.title.stroke};
      font-family: {COLOR.pages.home.title.font};
      font-size: {title_font_size + 'px'};
      line-height: 0.72;
    ">
      MARI<br>HACKS
    </p>
  </div>

  <div id="sec_title_right">
    <img src={duck_logo} alt="MariHacks duck logo" />
  </div>

</div>

<div id="sec_about">
  <p style="color: white; font-size: 100px">
    ABOUT<br>
    ABOUT<br>
    ABOUT<br>
    ABOUT<br>
    ABOUT<br>
    ABOUT<br>
    ABOUT<br>
  </p>
</div>

<div id="sec_sponsors">

</div>

<div id="sec_FAQ">

</div>

<style>
#sec_title {
  display: flex;
  justify-self: center;
}
</style>
