<script>
  import Button from "../Components/Button.svelte";

  const { isCorrect, explanation, onNext } = $props();

  const title = isCorrect ? "Nicely Done!" : "Not quite!";
</script>

<div id="graded" class={isCorrect ? "correct" : "incorrect"}>
  <div id="graded-status">
    <h2>{title}</h2>
    <p>{explanation}</p>
  </div>

  <Button
    label="continue"
    disabled={false}
    variant={isCorrect ? "correct" : "incorrect"}
    onclick={onNext}
  />
</div>

<style>
  #graded {
    min-height: 160px;
    gap: 20px;
    padding: 20px 12px 30px 12px;
  }

  #graded.correct {
    background-color: #dcffbe;
  }

  #graded.incorrect {
    background-color: #ffc1c1;
  }

  #graded-status {
    flex: 1;
  }

  #graded-status h2 {
    font-size: 22px;
    margin-bottom: 10px;
  }

  .correct #graded-status h2,
  .correct #graded-status p {
    color: #63ba09;
  }

  .incorrect #graded-status h2,
  .incorrect #graded-status p {
    color: #ea2b2b;
  }
</style>
