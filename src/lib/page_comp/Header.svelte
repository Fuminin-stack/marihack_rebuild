<script>
  // marihack logo
  import marihack_logo from "$lib/images/marihack_logo_C.png";
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

  import DropListTrigger from "$lib/page_item/DropListTrigger.svelte";

  const COLORS = colors_json;
  const TEXT = header_json;
  const URL = urls_json;
  const CST = constants_json;

  // button parameters
  const BUTTON_PARA = {
    text: "16px",
    text_margin_width: "8px",
    text_margin_height: "5px",
    hitbox_width: "130px",
    hitbox_height: "80px",
    border_radius: "17px",
  };

  const DROP_LIST_BUTTON_PARA = {
    text: "16px",
    text_margin_width: "8px",
    text_margin_height: "5px",
    hitbox_width: "140px",
    hitbox_height: "80px",
    border_radius: "17px",
  };

  let clientWidth = 0;
  let dropListTriggered = false;
</script>

<!-- Outermost container which allows overflowing -->
<div bind:clientWidth id="header_container">
  <!-- Navigation Bar -->
  <div id="nav_bar" style="background-image: url({star_map});">
    <div id="nav_bar_left">
      <img
        id="marihack_logo"
        class="self-centered"
        src={marihack_logo}
        alt="Marihack Logo"
        style={"height: " +
          (clientWidth > CST.sizes.mob_width
            ? "50px"
            : clientWidth / 13 + "px")}
      />

      {#if clientWidth > CST.sizes.mob_width}
        <div id="vertical_line" class="self-centered"></div>
        <div id="nav_button_list_1">
          <Button
            color_theme={COLORS.button.type_black}
            text_val={TEXT.nav_bar.buttons.about}
            size_info={BUTTON_PARA}
            react={() => {
              const anchor = document.getElementById("sec_about");
              if (anchor != null) {
                window.scrollTo({
                  top: anchor.offsetTop,
                  behavior: "smooth",
                });
              } else {
                window.location.assign("/#sec_about");
              }
            }}
          />
          <Button
            color_theme={COLORS.button.type_black}
            text_val={TEXT.nav_bar.buttons.sponsors}
            size_info={BUTTON_PARA}
            react={() => {
              const anchor = document.getElementById("sec_sponsors");
              if (anchor != null) {
                window.scrollTo({
                  top: anchor.offsetTop,
                  behavior: "smooth",
                });
              } else {
                window.location.assign("/#sec_sponsors");
              }
            }}
          />
          <Button
            color_theme={COLORS.button.type_black}
            text_val={TEXT.nav_bar.buttons.FAQ}
            size_info={BUTTON_PARA}
            react={() => {
              const anchor = document.getElementById("sec_FAQ");
              if (anchor != null) {
                window.scrollTo({
                  top: anchor.offsetTop,
                  behavior: "smooth",
                });
              } else {
                window.location.assign("/#sec_FAQ");
              }
            }}
          />
          <Button
            color_theme={COLORS.button.type_black}
            text_val={TEXT.nav_bar.buttons.get_involved}
            size_info={BUTTON_PARA}
            react={() => {
              const anchor = document.getElementById("sec_FAQ");
              if (anchor != null) {
                window.scrollTo({
                  top: anchor.offsetTop,
                  behavior: "smooth",
                });
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
          <Button
            color_theme={COLORS.button.type_blue}
            text_val={TEXT.nav_bar.buttons.register}
            size_info={BUTTON_PARA}
            react={() => {}}
            enable={false}
          />
        </div>
      {/if}

      <div
        id="mtb_container"
        style="
          padding-right: {(clientWidth > CST.sizes.mob_width ? 50 : 0) + 'px'};
      "
      >
        <a
          id="mlh-trust-badge"
          style="
          width: {clientWidth / 14 + 'px'};
        "
          href={URL.page_comp.header.mlh_trust_badge.href}
          target="_blank"
        >
          <img
            src={URL.page_comp.header.mlh_trust_badge.image_src}
            alt="Major League Hacking 2025 Hackathon Season"
            style="width:100%"
          />
        </a>
      </div>

      {#if clientWidth < CST.sizes.mob_width}
        <div
          id="drop_list_trigger_container"
          style="
        padding: {(
            '0px ' +
            (20 * clientWidth) / CST.sizes.mob_width +
            'px '
          ).repeat(2)};
      "
        >
          <DropListTrigger
            triggered={dropListTriggered}
            react={() => {
              dropListTriggered = !dropListTriggered;
            }}
          />
        </div>
      {/if}
    </div>
  </div>

  {#if dropListTriggered && clientWidth < CST.sizes.mob_width}
    <div id="drop_list_container" style="height: 0px;">
      <div id="drop_list" style="justify-items: center;">
        <Button
          color_theme={COLORS.button.type_black}
          text_val={TEXT.nav_bar.buttons.about}
          size_info={DROP_LIST_BUTTON_PARA}
          react={() => {
            const anchor = document.getElementById("sec_about");
            if (anchor != null) {
              window.scrollTo({
                top: anchor.offsetTop,
                behavior: "smooth",
              });
            } else {
              window.location.assign("/#sec_about");
            }
          }}
        />
        <Button
          color_theme={COLORS.button.type_black}
          text_val={TEXT.nav_bar.buttons.sponsors}
          size_info={DROP_LIST_BUTTON_PARA}
          react={() => {
            const anchor = document.getElementById("sec_sponsors");
            if (anchor != null) {
              window.scrollTo({
                top: anchor.offsetTop,
                behavior: "smooth",
              });
            } else {
              window.location.assign("/#sec_sponsors");
            }
          }}
        />
        <Button
          color_theme={COLORS.button.type_black}
          text_val={TEXT.nav_bar.buttons.FAQ}
          size_info={DROP_LIST_BUTTON_PARA}
          react={() => {
            const anchor = document.getElementById("sec_FAQ");
            if (anchor != null) {
              window.scrollTo({
                top: anchor.offsetTop,
                behavior: "smooth",
              });
            } else {
              window.location.assign("/#sec_FAQ");
            }
          }}
        />
        <Button
          color_theme={COLORS.button.type_blue}
          text_val={TEXT.nav_bar.buttons.register}
          size_info={BUTTON_PARA}
          react={() => {}}
          enable={false}
        />
      </div>
    </div>
  {/if}
</div>

<style>
  .self-centered {
    justify-self: center;
    align-self: center;
  }

  #header_container {
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
    padding: 5px 0 5px 0;
    min-height: 40px;
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
    overflow-y: visible;
  }

  #mlh-trust-badge {
    display: block;
    max-width: 150px;
    min-width: 75px;
  }

  #drop_list_trigger_container {
    align-content: center;
    justify-content: center;
  }

  #drop_list {
    display: grid;
    background-color: rgba(0, 0, 0, 0.9);
  }
</style>
