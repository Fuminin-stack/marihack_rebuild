<script>
  /* load colors */
  import Button from "$lib/page_item/Button.svelte";

  /* load texts */
  import header_json from "$lib/storage/comp_info/header.json";

  import colors_json from "$lib/storage/color_palette.json";
  const COLORS = colors_json;
  const TEXT = header_json;

  const BUTTON_PARA = {
    text: "16px",
    text_margin: "6px",
    hitbox_width: "100px",
    hitbox_height: "40px",
    border_radius: "20px",
  };
</script>

<!-- Outermost container which allows overflowing -->
<div>
  <!-- Navigation Bar -->
  <div id="nav_bar">
    <div id="nav_button_list">
    <div class="nav_button" id="about_button">
      <Button color_theme={COLORS.button.type_black}
        text_val={TEXT.nav_bar.buttons.about}
        size_info={BUTTON_PARA}
      />
    </div>
    <div class="nav_button" id="sponsors_button">
      <Button color_theme={COLORS.button.type_black}
        text_val={TEXT.nav_bar.buttons.sponsors}
        size_info={BUTTON_PARA}
      />
    </div>
    <div class="nav_button" id="faq_button">
      <Button color_theme={COLORS.button.type_black}
        text_val={TEXT.nav_bar.buttons.FAQ}
        size_info={BUTTON_PARA}
      />
    </div>
    </div>
  </div>
  <div class="floating_div">
  </div>
</div>

<style>
div {
  width: 100%;
}

.nav_button {
  margin: 2px;
}

#nav_button_list {
  margin: 10px;
  display: flex;
  flex-direction: row;
}
</style>
