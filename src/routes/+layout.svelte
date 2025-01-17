<script>
  /* load style */
  import "$lib/style.css";

  /* load page components */
  import Header from "$lib/page_comp/Header.svelte";

  import constants_json from "$lib/storage/constants.json";

  import star_map from "$lib/images/star_map.svg";

  let Z = constants_json.z;
</script>

<body style="background-image: url({star_map});">
  <nav id="header_container" style="z-index: {Z.HTOP};">
    <Header />
  </nav>
  <slot />
</body>

<style>
  body {
    padding: 0px;
    margin: 0px;
    background-color: black;
    background-size: 100%;
    background-attachment: fixed;
  }

  #header_container {
    width: 100%;
    position: sticky;
    top: 0px;
  }
</style>
