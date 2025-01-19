<script lang="ts">
  import Button from "../Components/Button.svelte";

  const { timeSpent, totalQuestions, score, onContinue } = $props();

  const formatDuration = (ms: number) => {
    const seconds = Math.floor(ms / 1000);
    const minutes = Math.floor(seconds / 60);
    const remainingSeconds = seconds % 60;
    return `${minutes.toString().padStart(2, "0")}:${remainingSeconds.toString().padStart(2, "0")}`;
  };

  const derivedScore = `${Math.round(score * 100)}%`;
  const formattedTime = formatDuration(timeSpent);
</script>

<div id="stage">
  <main>
    <h2>Quiz<br />complete!</h2>
    <div id="stats">
      <div class="stat">
        <h3>Total Questions</h3>
        <p>{totalQuestions}</p>
      </div>
      <div class="stat">
        <h3>Time Spent</h3>
        <p>{formattedTime}</p>
      </div>
      <div class="stat">
        <h3>Score</h3>
        <p>{derivedScore}</p>
      </div>
    </div>
  </main>
  <div id="move-on">
    <Button label="continue" onclick={onContinue} disabled={true} />
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

  #stats {
    width: 100%;
    gap: 20px;
  }

  .stat {
    flex-direction: row;
    border: 2px solid #e1e1e1;
    border-radius: 12px;
    padding: 24px 12px;
  }

  .stat h3 {
    flex: 1;
    font-weight: 900;
    font-size: 18px;
  }

  .stat p {
    font-weight: 500;
    font-size: 16px;
  }

  #move-on {
    position: sticky;
    bottom: 0;
    padding: 20px 12px 30px 12px;
  }
</style>
