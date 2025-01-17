<!--
 Round corner, 3D buttons
-->

<script>
  import colors from "$lib/storage/color_palette.json";
  import { tweened } from "svelte/motion";

  // Text on the button
  export let text_val;
  export let text_wrapping = false;

  // Using color theme to set colors
  export let color_theme = colors.button.type_blue;
  // Color of the button in Hex color code
  export let color = color_theme.base;
  // Color of the button when a mouse hovers above
  export let color_on_hover = color_theme.hover;
  // Color of the outline
  export let outline_color = color_theme.border;
  // Color of the text
  export let text_color = color_theme.text;
  // Font Family
  export let font = color_theme.font;

  // Size info of the button
  export let size_info = {
    // size of the actual button
    text: "16px",
    text_margin_width: "6px",
    text_margin_height: "6px",
    // size of the button to its parent
    hitbox_width: "90px",
    hitbox_height: "90px",
    // radius of the round corner
    border_radius: "20px",
  };

  // If disable
  export let enable = true;

  // On click function
  export let react = () => {};

  let _color = color;
  let _anchor_display = "visible";
  let _opacity = 1;
  let _border = tweened(4, {
    duration: 75,
  });

  if (!enable) {
    _opacity = 0.6;
  }
</script>

<div
  id="hitbox"
  style="
    --hitbox_width: {size_info.hitbox_width};
    --hitbox_height: {size_info.hitbox_height};
  "
>
  <div id="anchor" style="--display_mode: {_anchor_display};">
    <!-- style in <style> can not be updated as a variable -->
    <button
      style="
      --font: {font};
      --text_size: {size_info.text};
      --outline_color: {outline_color};
      --_color: {_color};
      --_border: {$_border + 'px'};
      --_opacity: {_opacity};
      --border_radius: {size_info.border_radius};
    "
      on:focus={() => {}}
      on:click={react}
      on:mouseenter={() => {
        if (!enable) return;
        _border.set(1);
        _color = color_on_hover;
      }}
      on:mouseleave={() => {
        if (!enable) return;
        _border.set(4);
        _color = color;
      }}
    >
      <p
        style="
        --text_color: {text_color};
        --text_margin_width: {size_info.text_margin_width};
        --text_margin_height: {size_info.text_margin_height};
        --text_wrapping: {text_wrapping ? 'wrap' : 'nowrap'};
      "
      >
        {text_val}
      </p>
    </button>
  </div>
</div>

<style>
  #hitbox {
    width: var(--hitbox_width);
    height: var(--hitbox_height);
  }

  #anchor {
    position: relative;
    top: 50%;
    left: 50%;

    width: 1px;
    height: 1px;
    overflow: visible;

    display: grid;
    justify-content: center;
    align-content: center;
  }

  button {
    position: relative;

    font-family: var(--font);
    font-size: var(--text_size);

    background-color: var(--_color);

    border-radius: var(--border_radius);
    border-style: solid;
    border-width: 1px;
    border-color: var(--outline_color);
    border-right-width: var(--_border);
    border-bottom-width: var(--_border);
    right: var(--_border);
    bottom: var(--_border);

    opacity: var(--_opacity);
  }

  p {
    color: var(--text_color);

    text-wrap: var(--text_wrapping);

    margin-top: var(--text_margin_height);
    margin-bottom: var(--text_margin_height);

    margin-left: var(--text_margin_width);
    margin-right: var(--text_margin_width);

    padding-top: var(--text_margin_height);
    padding-bottom: var(--text_margin_height);

    padding-left: var(--text_margin_width);
    padding-right: var(--text_margin_width);
  }
</style>
