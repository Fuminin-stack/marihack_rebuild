<script>
  /* load style */
  import "$lib/style.css";

  /* load page components */
  import Header from "$lib/page_comp/Header.svelte";
  import Button from "$lib/page_item/Button.svelte";

  /* load color themes */
  import colors_json from "$lib/config/color_palette.json"

  function _react() {
    window.open('https://www.google.com')
  }

  const colors = colors_json;
</script>
<Button
  text_val="Hello World!"
  text_size="20px"
  react={_react}
/>

