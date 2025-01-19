<script lang="ts">
  const { totalQuestions, currentQuestion } = $props();

  let progress = ((currentQuestion - 1) / totalQuestions) * 100;
  console.log(progress);
</script>

<header>
  <h1>Capitals Quiz</h1>
  <div id="metadata">
    <div id="progress-background">
      <div id="progress" style="width: {progress}%;"></div>
    </div>
    <p>{currentQuestion}/{totalQuestions}</p>
  </div>
</header>

<style>
  header {
    padding-top: 10px;
    min-height: 80px;
    padding: 18px 12px 12px 12px;
    position: sticky;
    top: 0;
    border-bottom: 2px solid rgb(219, 219, 219);
    margin-bottom: 12px;

    background-color: white;
    position: sticky;
    top: 0;
  }

  h1 {
    font-size: 18px;
    font-weight: bold;
    text-align: center;
    margin-bottom: 12px;
  }

  #metadata {
    flex-direction: row;
    gap: 12px;
  }

  #progress-background {
    background-color: #e4e4e4;
    flex: 1;
    border-radius: 10px;
    position: relative;
    overflow: hidden;
  }

  #progress {
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    background-color: #77c83b;
  }
</style>
