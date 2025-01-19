<script lang="ts">
  const { prompt, choices, onSelectChoice, disabled } = $props();
  let selectedIndex = $state<number | null>(null);
</script>

<div>
  <h2>{prompt}</h2>

  <div>
    <fieldset id="choices">
      {#each choices as choice, i}
        <div
          class="choice"
          onclick={() => {
            if (disabled) {
              return;
            }
            selectedIndex = i;
            onSelectChoice(i);
          }}
        >
          <input
            type="radio"
            id="choice-{i}"
            name="question"
            checked={i == selectedIndex}
            {disabled}
          />
          <label for="choice-{i}">{choice}</label>
        </div>
      {/each}
    </fieldset>
  </div>
</div>

<style>
  h2 {
    margin-bottom: 24px;
  }

  #choices {
    cursor: pointer;

    border: 2px solid #e1e1e1;
    border-radius: 12px;
    overflow: hidden;

    -webkit-tap-highlight-color: transparent;
  }

  .choice {
    flex-direction: row;
    align-items: center;
    border-bottom: 2px solid #e1e1e1;
    height: 80px;
    gap: 12px;

    padding: 0 10px;
  }

  .choice:has(input[type="radio"]:checked) {
    background-color: #fdf5d6;
  }

  .choice label {
    flex: 1;
  }

  .choice:last-child {
    border-bottom: none;
  }

  /*
  Custom radio select
  */
  .choice input[type="radio"] {
    appearance: none;
    width: 22px;
    height: 22px;
    border: 2px solid #999;
    border-radius: 50%;
  }

  .choice input[type="radio"] {
    background-color: white;
  }

  .choice input[type="radio"]:checked {
    border-color: #52adf0;
    background-color: #52adf0;
    background-clip: content-box;
    padding: 3px;
  }
</style>
