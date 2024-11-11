<script>
  // marihack logo
  import marihack_logo from "$lib/images/marihack_logo.png";
  // background
  import star_map from "$lib/images/star_map.svg";

  // load colors
  import Button from "$lib/page_item/Button.svelte";

  // load urls
  import urls_json from "$lib/storage/url_info.json";

  // load texts
  import header_json from "$lib/storage/comp_info/header.json";

  import constants_json from "$lib/storage/constants.json";

  import colors_json from "$lib/storage/color_palette.json";
  const COLORS = colors_json;
  const TEXT = header_json;
  const URL = urls_json;
  const CST = constants_json;

  // button parameters
  const BUTTON_PARA = {
    text: "16px",
    text_margin_width: "8px",
    text_margin_height: "5px",
    hitbox_width: "140px",
    hitbox_height: "80px",
    border_radius: "17px",
  };

  let clientWidth = 0;
</script>

<!-- Outermost container which allows overflowing -->
<div bind:clientWidth={clientWidth} id="outer_container">
  <!-- Navigation Bar -->
  <div id="nav_bar" style="background-image: url({star_map});">

  <div id="nav_bar_left">
    <img id="marihack_logo" class="self-centered" src={marihack_logo} alt="Marihack Logo"/>

    {#if clientWidth > CST.sizes.mob_width}
    <div id="vertical_line" class="self-centered"></div>
    <div id="nav_button_list_1">
      <Button color_theme={COLORS.button.type_black}
        text_val={TEXT.nav_bar.buttons.about}
        size_info={BUTTON_PARA}
        react={() => {
          const anchor = document.getElementById("sec_about");
          if (anchor != null) {
            window.scrollTo({
              top: anchor.offsetTop,
			        behavior: 'smooth'});
          } else {
            window.location.assign("/#sec_about");
          }
        }}
      />
      <Button color_theme={COLORS.button.type_black}
        text_val={TEXT.nav_bar.buttons.sponsors}
        size_info={BUTTON_PARA}
        react={() => {
          const anchor = document.getElementById("sec_sponsors");
          if (anchor != null) {
            window.scrollTo({
              top: anchor.offsetTop,
			        behavior: 'smooth'});
          } else {
            window.location.assign("/#sec_sponsors");
          }
        }}
      />
      <Button color_theme={COLORS.button.type_black}
        text_val={TEXT.nav_bar.buttons.FAQ}
        size_info={BUTTON_PARA}
        react={() => {
          const anchor = document.getElementById("sec_FAQ");
          if (anchor != null) {
            window.scrollTo({
              top: anchor.offsetTop,
			        behavior: 'smooth'});
          } else {
            window.location.assign("/#sec_FAQ");
          }
        }}
      />
    </div>
    {/if}
  </div>

  <div id="nav_bar_right">
    {#if clientWidth > CST.sizes.mob_width}
    <div id="nav_button_list_2">
      <Button color_theme={COLORS.button.type_blue}
        text_val={TEXT.nav_bar.buttons.register}
        size_info={BUTTON_PARA}
        react={() => {
        }}
        enable={false}
      />
    </div>
    {/if}
    <div id="mtb_container">
      <a id="mlh-trust-badge"
        style="width: {0.075 * clientWidth + 'px'};"
        href={URL.page_comp.header.mlh_trust_badge.href}
        target="_blank"
      >
        <img src={URL.page_comp.header.mlh_trust_badge.image_src}
          alt="Major League Hacking 2025 Hackathon Season"
          style="width:100%"
        >
      </a>
    </div>
    {#if clientWidth < CST.sizes.mob_width}
    <div id="drop_list_container">
    </div>
    {/if}
  </div>

  </div>
</div>

<style>
.self-centered {
  justify-self: center;
  align-self: center;
}

#outer_container {
  width: 100%;
}

#nav_bar {
  background-color: black;
  background-size: 100%;
  width: 100%;
  display: grid;
  grid-template-columns: auto auto;
  justify-content: space-between;
  margin: 0px;
  padding: 0px;
}

#nav_bar_left {
  display: flex;
  margin-left: 20px;
}

#nav_bar_right {
  height: 100%;
  align-self: center;
  display: flex;
}

#vertical_line {
  margin-left: 12px;
  margin-right: 20px;
  height: 60px;
  width: 1px;
  background-color: white;
}

#marihack_logo {
  height: 100px;
  width: auto;
  padding: 4px;
}

#nav_button_list_1 {
  display: flex;
  flex-direction: row;
  
  gap: 5px;

  justify-self: left;
  align-self: center;
}

#nav_button_list_2 {
  justify-self: right;
  align-self: center;
}

#mtb_container {
  height: 0px;
  vertical-align: top;
  padding-right: 50px;
  padding-left: 20px;
  overflow-y: visible;
}

#mlh-trust-badge {
  display: block;
  max-width: 150px;
  min-width: 60px;
}
</style>
