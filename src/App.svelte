<script lang="ts">
  import Button from "./Button.svelte";
</script>

<div>
  <p>This is a paragraph.</p>
  <p>This is a paragraph.</p>
  <p>This is a paragraph.</p>
  <p>This is a paragraph.</p>
  <div id="check-answer">
  <Button label="Check Answer" />
  </div>
</div>

<style>
	p {
    font-family: 'Courier New', Courier, monospace;
    font-size: 14px;
    line-height: 1.2;
  }

  #check-answer {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    padding: 20px 12px;
  }
</style>
