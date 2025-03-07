<script>
  import colors_json from "$lib/storage/color_palette.json";
  let COLOR = colors_json.pages.home.typing_key_board.default;

  export let font_size = 54;
  export let texts = ["Hello", "World"];

  // setting for text cycles
  let _current_text = "";
  let word_no = 0;
  let txt_cycle_cd = 0;
  let txt_cycle_state = -(texts[word_no].length - 1); // initial state
  // <0 for incrasing txt, 0 for halt, >0 for decreasing txt
  function updateText() {
    // Cool Down
    if (txt_cycle_cd > 0) {
      txt_cycle_cd--;
      return;
    }

    if (txt_cycle_state < 0) {
      _current_text = texts[word_no].slice(0, txt_cycle_state);
      txt_cycle_state++;
      return;
    } else if (txt_cycle_state == 0) {
      _current_text = texts[word_no];
      txt_cycle_state++;
      txt_cycle_cd = 10;
      return;
    } else {
      if (txt_cycle_state < texts[word_no].length) {
        _current_text = texts[word_no].slice(0, -txt_cycle_state);
        txt_cycle_state++;
        return;
      }
    }

    // Next Sentence
    word_no++;
    if (texts[word_no] === undefined) {
      word_no = 0;
    }
    _current_text = "";
    txt_cycle_state = -(texts[word_no].length - 1);
  }
  let cursor_state = false;
  let cursor_color = COLOR.cursor_hidden;
  function cursor_effect() {
    if (cursor_state) {
      cursor_color = COLOR.cursor_hidden;
    } else {
      cursor_color = COLOR.cursor_shown;
    }
    cursor_state = cursor_state ? false : true;
  }
  setInterval(cursor_effect, 500);
  setInterval(updateText, 100);
</script>

<div id="item_container" style="justify-self: center;">
  <div id="txt_container">
    <p
      style="font-size: {font_size}px; font-family: {COLOR.font}; --margin: {font_size *
        0.7}px"
    >
      <!-- &#8203 is zero width space -->
      &#8203{_current_text}
    </p>
    <div
      id="cursor"
      style="background-color: {cursor_color}; height: {font_size}px; width: {font_size /
        6}px;"
    ></div>
  </div>
</div>

<style>
  p {
    justify-self: center;
    margin-top: var(--margin);
    margin-bottom: var(--margin);
  }
  #cursor {
    align-self: center;
  }
  #txt_container {
    display: flex;
    justify-content: center;
  }
</style>
