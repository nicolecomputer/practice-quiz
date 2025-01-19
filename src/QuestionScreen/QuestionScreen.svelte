<script lang="ts">
  import Header from "./Header.svelte";
  import Button from "../Components/Button.svelte";
  import Question from "./Question.svelte";
  import Graded from "./Graded.svelte";

  type GradedState = "ungraded" | "graded";

  let selectedIndex = $state<null | number>(null);
  let gradedState = $state<GradedState>("ungraded");

  const { question, totalQuestions, currentQuestion, onNextQuestion } =
    $props();
</script>

<div id="stage">
  <Header {totalQuestions} {currentQuestion} />
  <main>
    <Question
      disabled={gradedState === "graded"}
      prompt={question.prompt}
      choices={question.choices}
      onSelectChoice={(choiceIndex: number) => (selectedIndex = choiceIndex)}
    />
  </main>
  <div id="answer-area">
    {#if gradedState === "ungraded"}
      <div id="check-answer">
        <Button
          label="Check Answer"
          disabled={selectedIndex == null}
          onclick={() => {
            gradedState = "graded";
          }}
        />
      </div>
    {:else}
      <Graded
        isCorrect={selectedIndex == question.correctIndex}
        explanation={question.explanation}
        onNext={() => {
          onNextQuestion(selectedIndex == question.correctIndex);
        }}
      />
    {/if}
  </div>
</div>

<style>
  #stage {
    min-height: 100vh;
  }
  main {
    margin-top: 10px;
    padding: 0 12px;
    flex: 1;
    min-height: 100%;
  }

  #answer-area {
    position: sticky;
    bottom: 0;
  }

  #check-answer {
    padding: 20px 12px 30px 12px;
  }
</style>
