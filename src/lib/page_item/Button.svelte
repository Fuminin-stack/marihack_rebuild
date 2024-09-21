<!-- Round corner, 3D, button-->
<script>
  import colors from "$lib/config/color_palette.json"
  import { tweened } from "svelte/motion";

  /* Using color theme to set colors */
  export let color_theme = colors.button.type_blue;
  /* Text on the button */
  export let text_val;
  /* Color of the button in Hex color code*/
  export let color = color_theme.base;
  /* Color of the button when a mouse hovers above*/
  export let color_on_hover = color_theme.hover;
  /* Color of the outline */
  export let outline_color = color_theme.border;
  /* Color of the text */
  export let text_color = color_theme.text;
  /* Size of the button */
  export let text_size;
  /* On click function*/
  export let react = () => {};
  
  let _color = color;
  
  let _border = tweened(4, {
    duration: 100,
  });
</script>

<div>
  <button
    id="upper"
      
    style="
      position: relative;
      font-family: 'GeneralSans-Regular';
      font-size: {text_size};
      background-color: {_color};
      border-radius: 25px;
      border-style: solid;
      border-width: '2px';
      border-color: {outline_color};
      border-right-width: {$_border + 'px'};
      border-bottom-width: {$_border + 'px'};
      right: {$_border + 'px'};
      bottom: {$_border + 'px'};
    "
    
    on:focus={() => {}}
    
    on:click={react}
    
    on:mouseenter={() => {
      _border.set(2);
      _color = color_on_hover;
    }}
    
    on:mouseleave={() => {
      _border.set(4)
      _color = color;
    }}
    >
    
    <p
      style="color: {text_color}"
    >
      {text_val}
    </p>
  
  </button>
</div>

<style>
</style>
