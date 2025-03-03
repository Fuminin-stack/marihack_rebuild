<script>
  // Color and Constant
  import color_json from "$lib/storage/color_palette.json";
  import constants_json from "$lib/storage/constants.json";

  // Images
  import duck_logo_img from "$lib/images/duck_logo.png";
  import wave_1 from "$lib/images/waves/L1.svg";
  import wave_2 from "$lib/images/waves/L2.svg";
  import wave_3 from "$lib/images/waves/L3.svg";

  // svelte component
  import { onMount } from "svelte";
  import Button from "$lib/page_item/Button.svelte";
  import TypingText from "$lib/page_item/TypingText.svelte";
  import GeneralContainer from "$lib/page_item/GeneralContainer.svelte";

  // Texts
  import RichTxtSecAbout from "$lib/storage/pages_info/home/sec_about.svelte";
  import text_json from "$lib/storage/pages_info/home/home.json";

  const TXT = text_json;
  const COLOR = color_json;
  const CST = constants_json;
  const duck_logo = duck_logo_img;

  let clientWidth = 0;
  let title_font_size = 0;
  let shadow_size = 0;
  $: is_desktop = clientWidth > CST.sizes.mob_width;

  $: {
    // for the title
    if (is_desktop) {
      title_font_size = (250 * clientWidth) / 1920;
      shadow_size = (8 * clientWidth) / 1920;
    } else {
      title_font_size = clientWidth / 4;
      shadow_size = clientWidth / 100;
    }
  }
  // for wave effect
  function waveEffect() {
    let scrollTop = window.scrollY;
    let wd2 = clientWidth * (CST.wave_effect.layer1 - CST.wave_effect.layer2);
    let wd3 = clientWidth * (CST.wave_effect.layer1 - CST.wave_effect.layer3);
    let w2 = document.getElementById("wave_layer_2");
    let w3 = document.getElementById("wave_layer_3");
    if (w2 != null) {
      let scroll = -scrollTop * 0.06;
      scroll = scroll < -wd2 ? -wd2 : scroll;
      w2.style.transform = "translateY(" + scroll + "px)";
    }
    if (w3 != null) {
      let scroll = -scrollTop * 0.1;
      scroll = scroll < -wd3 ? -wd3 : scroll;
      w3.style.transform = "translateY(" + scroll + "px)";
    }
  }
  onMount(() => {
    window.addEventListener("scroll", waveEffect);

    // Clean up the event listener when the component is destroyed
    return () => {
      window.removeEventListener("scroll", waveEffect);
    };
  });
</script>

<svelte:head>
  <title>MariHacks</title>
</svelte:head>

<div id="page_container">
  <!-- sec stands for section -->
  <div
    bind:clientWidth
    id="sec_title"
    style="
    display: {is_desktop ? 'flex' : 'grid'};
    width: {is_desktop ? 100 : 80 + '%'};
  "
  >
    <div id={is_desktop ? "sec_title_left" : "sec_title_left_mob"}>
      <p
        id={is_desktop ? "title" : "title_mob"}
        style="
      color: {COLOR.pages.home.title.text};
      text-shadow: {shadow_size}px {shadow_size}px 0px {COLOR.pages.home.title
          .shadow};
      -webkit-text-stroke-width: 2px;
      -webkit-text-stroke-color: {COLOR.pages.home.title.stroke};
      font-family: {COLOR.pages.home.title.font};
      font-size: {title_font_size + 'px'};
      line-height: 0.72;
      margin: 40px;
      margin-left: 0px;
      margin-right: 0px;
    "
      >
        MARI<br />HACKS
      </p>
      <Button
        text_val={TXT.sec_title.on_tune}
        color_theme={COLOR.button.type_yellow_nohover}
        enable={false}
        size_info={{
          text: is_desktop ? "30px" : "20px",
          text_margin_width: is_desktop ? "8px" : "4px",
          text_margin_height: is_desktop ? "4px" : "4px",
          hitbox_width: is_desktop ? "260px" : "160px",
          hitbox_height: "40px",
          border_radius: "18px",
        }}
      />
      <hr style="width: 100%; margin-top: 15px;" />
      <p
        id={is_desktop ? "secondary_title_main" : "secondary_title_main_mob"}
        style="
      color: {COLOR.pages.home.secondary_title.main_text};
      font-family: {COLOR.pages.home.secondary_title.font};
      font-size: 18px;
      margin: 0px;
    "
      >
        {TXT.sec_title.time_description}
      </p>
      <p
        id={is_desktop ? "secondary_title_sub" : "secondary_title_sub_mob"}
        style="
      color: {COLOR.pages.home.secondary_title.sub_text};
      font-family: {COLOR.pages.home.secondary_title.font};
      font-size: {(clientWidth < 360
          ? (clientWidth / CST.sizes.mob_width) * 40
          : 16) + 'px'};
      margin: 0px;
    "
      >
        {TXT.sec_title.location_description}
      </p>
    </div>

    <div id="sec_title_right">
      <img id="duck_logo" src={duck_logo} alt="MariHacks duck logo" />
    </div>
  </div>

  <div
    id="wave_layers"
    style="
      height: {clientWidth * CST.wave_effect.layer1}px;
    "
  >
    <div
      id="wave_layer_1"
      class="wave_layer"
      style="bottom: {clientWidth * CST.wave_effect.layer1}px;"
    >
      <img id="wave_layer_1_svg" src={wave_1} alt="First Layer of Wave" />
    </div>
    <div
      id="wave_layer_2"
      class="wave_layer"
      style="bottom: {clientWidth * CST.wave_effect.layer2}px;"
    >
      <img id="wave_layer_2_svg" src={wave_2} alt="Second Layer of Wave" />
    </div>
    <div
      id="wave_layer_3"
      class="wave_layer"
      style="bottom: {clientWidth * CST.wave_effect.layer3}px;"
    >
      <img id="wave_layer_3_svg" src={wave_3} alt="Third Layer of Wave" />
    </div>
  </div>
  <div
    id="grouped_section"
    style="background-color: {COLOR.pages.home.grouped_section.bg_color};"
  >
    <div id="sec_about">
      <div id="typing_effect_text">
        <!--
          margin: 0 auto is required
          without it, there will be display bug on ios devices
          f**k ios
        -->
        <div class="tet_hbar" style="margin: 0 auto;" />
        <TypingText font_size={is_desktop ? 54 : 18} texts={TXT.typing_text} />
        <div class="tet_hbar" style="margin: 0 auto;" />
      </div>
      <div
        id="marihacks_presentation"
        style="margin: 0 auto; {is_desktop ? '' : 'flex-direction: column;'}"
      >
        <GeneralContainer>
          <RichTxtSecAbout {is_desktop} />
        </GeneralContainer>
        <GeneralContainer></GeneralContainer>
      </div>
    </div>
    <div id="sec_sponsors"></div>
    <h1>SPONSORS</h1>
    <div id="sec_FAQ"></div>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
    <h1>FAQ</h1>
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

  #wave_layers {
    position: relative;
    margin: 0px;
    padding: 0px;
    overflow: hidden;
    width: 100%;
  }

  .wave_layer {
    position: absolute;
    margin: 0px;
    padding: 0px;
    width: 100%;
    height: 0px;
    overflow: visible;
    line-height: 0px;
  }

  #wave_layer_1_svg {
    margin: 0px;
    padding: 0px;
    width: 100%;
  }

  #wave_layer_2_svg {
    margin: 0px;
    padding: 0px;
    width: 100%;
  }

  #wave_layer_3_svg {
    margin: 0px;
    padding: 0px;
    width: 100%;
  }
  .tet_hbar {
    width: 80%;
    justify-self: center;
    background-color: black;
    height: 2px;
  }

  #marihacks_presentation {
    padding: 20px;
    width: 85%;
    justify-self: center;
    display: flex;
  }
</style>
