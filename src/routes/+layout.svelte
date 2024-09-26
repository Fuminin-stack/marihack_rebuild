<script>
  /* load style */
  import "$lib/style.css";

  /* load page components */
  import Header from "$lib/page_comp/Header.svelte";

  import star_map from "$lib/images/star_map.svg";
</script>

<body style="
  padding: 0px;
  margin: 0px;
  background-color: black;
  ">
  <div id="header_container">
    <Header />
  </div>
  <div id="background_image_container">
    <img id="star_map" src={star_map} alt="Background Star" />
  </div>
</body>

<style>
#star_map {
  width: 100%;
  height: auto;
}
#background_image_container {
  width: 100%;
  position: fixed;
}
#header_container {
}
</style>
