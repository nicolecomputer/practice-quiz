<script lang="ts">
  import Button from "../Components/Button.svelte";

  const { onBegin, numberOfQuestions } = $props();
</script>

<div id="stage">
  <main>
    <h2>Let's Go!</h2>

    <div id="details">
      <h1>State Capitals Quiz</h1>
      <p>{numberOfQuestions} questions</p>
    </div>
  </main>
  <div id="start">
    <Button label="begin" onclick={onBegin} />
  </div>
</div>

<style>
  #stage {
    min-height: 100vh;
  }

  main {
    margin-top: 80px;
    padding: 0 12px;
    flex: 1;
    min-height: 100%;
    align-items: center;
  }

  h2 {
    text-align: center;
    font-size: 40px;
    color: #ffc700;
    font-weight: 900;
    line-height: 1.3em;
    margin-bottom: 40px;
  }

  #details {
    border: 2px solid #e1e1e1;
    border-radius: 12px;
    width: 100%;
    padding: 0 10px;
  }

  #details h1 {
    border-bottom: 2px solid #e1e1e1;
    padding: 16px 0;
    font-weight: 900;
    font-size: 24px;
    text-align: center;
  }

  #details p {
    margin: 12px 0;
  }

  #start {
    position: sticky;
    bottom: 0;
    padding: 20px 12px 30px 12px;
  }
</style>
