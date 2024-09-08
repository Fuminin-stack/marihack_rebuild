<!-- Round corner, 3D, button-->
<script>
  /* Text on the button */
  export let text_val;
  /* Color of the button */
  export let color;
  /* Color of the button when a mouse hovers above*/
  export let color_on_hover;
  /* Color of the outline */
  export let outline_color;
</script>

<button style="font-family: 'GeneralSans-Light;">
  {text_val}
</button>

<style>
  button {
    border-radius: 25px
  }
</style>
