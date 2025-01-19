<script lang="ts">
  import EndOfTaskScreen from "./EndOfTask/EndOfTaskScreen.svelte";
  import QuestionScreen from "./QuestionScreen/QuestionScreen.svelte";
  import StartOfTaskScreen from "./StartOfTask/StartOfTaskScreen.svelte";

  type QuizState = "start-of-task" | "quiz" | "end-of-task";

  const questions = [
    {
      prompt: "What is the capital of Idaho?",
      choices: ["Idaho Falls", "Coeur d'Alene", "Richmond", "Boise"],
      explanation: "Boise is the capital of Idaho",
      correctIndex: 3,
    },
    {
      prompt: "What is the capital of Indiana?",
      choices: ["Bloomington", "Indianapolis", "Frankfort", "Gary"],
      explanation: "Indianapolis is the capital of Indiana",
      correctIndex: 1,
    },
    {
      prompt: "What is the capital of Massachusetts?",
      choices: ["Springfield", "Boston", "Salem", "Cambridge"],
      explanation: "Boston is the capital of Massachusetts",
      correctIndex: 1,
    },
    {
      prompt: "What is the capital of New Mexico?",
      choices: ["Bismarck", "Albuquerque", "Santa Fe", "Las Cruces"],
      explanation: "Santa Fe is the capital of New Mexico",
      correctIndex: 2,
    },
    {
      prompt: "What is the capital of Mississippi?",
      choices: ["Jackson", "Columbia", "Biloxi", "Montgomery"],
      explanation: "Jackson is the capital of Mississippi",
      correctIndex: 0,
    },
    {
      prompt: "What is the capital of Oregon?",
      choices: ["Portland", "Eugene", "Salem", "Bend"],
      explanation: "Salem is the capital of Oregon",
      correctIndex: 2,
    },
    {
      prompt: "What is the capital of Nevada?",
      choices: ["Las Vegas", "Carson City", "Reno", "Henderson"],
      explanation: "Carson City is the capital of Nevada",
      correctIndex: 1,
    },
    {
      prompt: "What is the capital of Connecticut?",
      choices: ["Hartford", "New Haven", "Stamford", "Bridgeport"],
      explanation: "Hartford is the capital of Connecticut",
      correctIndex: 0,
    },
    {
      prompt: "What is the capital of Minnesota?",
      choices: ["Minneapolis", "Rochester", "Duluth", "St. Paul"],
      explanation: "St. Paul is the capital of Minnesota",
      correctIndex: 3,
    },
    {
      prompt: "What is the capital of Maine?",
      choices: ["Portland", "Augusta", "Bangor", "Lewiston"],
      explanation: "Augusta is the capital of Maine",
      correctIndex: 1,
    },
  ];

  let currentQuestionIndex = $state(0);
  let quizState = $state<QuizState>("start-of-task");
  let questionWasCorrect = $state(new Array<boolean>(questions.length));
  let startTime = $state(0);
  let endTime = $state(0);
</script>

{#if quizState === "start-of-task"}
  <StartOfTaskScreen
    numberOfQuestions={questions.length}
    onBegin={() => {
      quizState = "quiz";
      startTime = new Date().getTime();
    }}
  />
{:else if quizState === "quiz"}
  {#key `question-${currentQuestionIndex}`}
    <QuestionScreen
      currentQuestion={currentQuestionIndex + 1}
      totalQuestions={questions.length}
      question={questions[currentQuestionIndex]}
      onNextQuestion={(gradedCorrect: boolean) => {
        questionWasCorrect[currentQuestionIndex] = gradedCorrect;
        currentQuestionIndex += 1;

        if (currentQuestionIndex === questions.length) {
          quizState = "end-of-task";
          endTime = new Date().getTime();
        }
      }}
    />
  {/key}
{:else if quizState === "end-of-task"}
  <EndOfTaskScreen
    score={questionWasCorrect.filter((a) => a === true).length /
      questions.length}
    totalQuestions={questions.length}
    timeSpent={endTime - startTime}
    onContinue={() => {
      alert("there isn't any more");
    }}
  />
{/if}
