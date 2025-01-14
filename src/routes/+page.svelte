<script>
import color_json from "$lib/storage/color_palette.json";
import constants_json from "$lib/storage/constants.json";
import duck_logo_img from "$lib/images/duck_logo.png";
import text_json from "$lib/storage/pages_info/home.json";
import Button from "$lib/page_item/Button.svelte";
const TXT = text_json; 
const COLOR = color_json;
const CST = constants_json;
const duck_logo = duck_logo_img;

let clientWidth = 0;
let title_font_size = 0;
let shadow_size = 0;
$: {
  if (clientWidth > CST.sizes.mob_width) {
    title_font_size = 250 * clientWidth / 1920;
    shadow_size = 8 * clientWidth / 1920;
  } else {
    title_font_size = clientWidth / 4;
    shadow_size = clientWidth / 100;
  }
}
</script>

<svelte:head>
  <title>MariHacks</title>
</svelte:head>

<div id="page_container">
<!-- sec stands for section -->
<div bind:clientWidth={clientWidth}
  id="sec_title"
  style="
    display: {clientWidth > CST.sizes.mob_width ? "flex" : "grid"};
    width: {clientWidth > CST.sizes.mob_width ? 100 : 80 + '%'};
  "
>
  <div id={clientWidth > CST.sizes.mob_width ? "sec_title_left" : "sec_title_left_mob"}>
    <p id={clientWidth > CST.sizes.mob_width ? "title" : "title_mob"}
      style="
      color: {COLOR.pages.home.title.text};
      text-shadow: {shadow_size}px {shadow_size}px 0px {COLOR.pages.home.title.shadow};
      -webkit-text-stroke-width: 2px;
      -webkit-text-stroke-color: {COLOR.pages.home.title.stroke};
      font-family: {COLOR.pages.home.title.font};
      font-size: {title_font_size + 'px'};
      line-height: 0.72;
      margin: 40px;
      margin-left: 0px;
    ">
      MARI<br>HACKS
    </p>
    <Button text_val={TXT.sec_title.on_tune}
      color_theme={COLOR.button.type_yellow_nohover}
      enable={false}
      size_info={{
        text: (clientWidth > CST.sizes.mob_width ? "30px" : "20px"),
        text_margin_width: (clientWidth > CST.sizes.mob_width ? "8px" : "4px"),
        text_margin_height: (clientWidth > CST.sizes.mob_width ? "4px" : "4px"),
        hitbox_width: (clientWidth > CST.sizes.mob_width ? "260px" : "160px"),
        hitbox_height: "40px",
        border_radius: "18px",
      }}
    />
    <hr style="width: 100%; margin-top: 15px;"/>
    <p id={clientWidth > CST.sizes.mob_width ? "secondary_title_main" : "secondary_title_main_mob"}
      style="
      color: {COLOR.pages.home.secondary_title.main_text};
      font-family: {COLOR.pages.home.secondary_title.font};
      font-size: {COLOR.pages.home.secondary_title.main_font};
      margin: 0px;
    ">
      {TXT.sec_title.time_description}
    </p>
    <p id={clientWidth > CST.sizes.mob_width ? "secondary_title_sub" : "secondary_title_sub_mob"}
      style="
      color: {COLOR.pages.home.secondary_title.sub_text};
      font-family: {COLOR.pages.home.secondary_title.font};
      font-size: {COLOR.pages.home.secondary_title.sub_font};
      margin: 0px;
    ">
      {TXT.sec_title.location_description}
    </p>
  </div>

  <div id="sec_title_right">
    <img id="duck_logo" src={duck_logo} alt="MariHacks duck logo" />
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

</div>

<style>
#page_container {
  display: grid;
}

#title_mob {
  text-align: center;
}

#sec_title {
  justify-self: center;
  align-items: center;
}

#sec_title_left {
  display: grid;
  justify-items: left;
}

#sec_title_left_mob {
  display: grid;
  justify-items: center;
}

#duck_logo {
  width: 100%;
}
</style>
