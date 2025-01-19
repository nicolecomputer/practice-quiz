<script lang="ts">
  let { label, disabled = false, onclick, variant = "default" } = $props();
</script>

<button
  class={[`variant-${variant}`, disabled ? "disabled" : "enabled"]}
  {disabled}
  {onclick}
>
  {label}
</button>

<style>
  button {
    border: none;
    border-radius: 14px;
    min-height: 50px;

    color: white;
    font-family: Helvetica, Arial, sans-serif;
    font-size: 16px;
    font-weight: bold;
  }

  .variant-default {
    background-color: #52adf0;
    box-shadow: 0 3px 0 #6a99bc;
    color: white;
  }

  .variant-default.enabled:active {
    background-color: #4486b5;
  }

  .variant-correct {
    background-color: #63e60c;
    box-shadow: 0 3px 0 #5eb903;
    color: white;
  }

  .variant-correct.enabled:active {
    background-color: #4aac09;
  }

  .variant-incorrect {
    background-color: #ff4b4b;
    box-shadow: 0 3px 0 #ea2b2b;
    color: white;
  }

  .variant-incorrect.enabled:active {
    background-color: #ba3939;
  }

  .disabled {
    background-color: #e5e5e5;
    box-shadow: none;
    color: #b2b2b2;
  }
</style>
