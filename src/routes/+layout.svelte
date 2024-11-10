<script>
  /* load style */
  import "$lib/style.css";

  /* load page components */
  import Header from "$lib/page_comp/Header.svelte";

  import star_map from "$lib/images/star_map.svg";

</script>

<body style="background-image: url({star_map});">
  <nav id="header_container">
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
}

#header_container {
  width: 100%;
  position: sticky;
}
</style>
