<script lang="ts">
  import { onDestroy, onMount } from "svelte";

  export let question: string;

  let expanded = false;
  let answerElement: HTMLElement;
  let answerHeight: number = 0;
  let intervalCounter: 5;
  let interval: NodeJS.Timer;

  function toggleExpansion(): void {
    expanded = !expanded;
  }

  onMount(() => {
    answerHeight = answerElement.scrollHeight;
    interval = setInterval(() => {
      const height = answerElement.scrollHeight;
      if (height > answerHeight) {
        answerHeight = height;
      }
      intervalCounter--;
      if (intervalCounter == 0) clearInterval(interval);
    }, 3000);
  });
  onDestroy(() => {
    clearInterval(interval);
  });
</script>

<div class="faq_element_wrapper {expanded ? 'expanded' : ''}">
  <div
    class="faq_question_wrapper hover-cursor"
    on:click={() => toggleExpansion()}
  >
    <p class="faq_question">
      {question}
    </p>
    <div class="faq_question_button"><span /><span class="cross_line" /></div>
  </div>
  <div class="faq_answer_wrapper">
    <p
      class="faq_answer"
      bind:this={answerElement}
      style="--height: {answerHeight}px"
    >
      <slot />
    </p>
  </div>
</div>

<style>
  .faq_element_wrapper {
    border-bottom: 1px solid #fff;
    padding: 20px 0;
  }

  .faq_element_wrapper:first-child {
    border-top: 1px solid #fff;
  }

  .faq_question_wrapper {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .faq_question_wrapper:hover .faq_question_button span {
    background-color: #c0c0c0;
  }

  .faq_question_wrapper:hover .faq_question {
    color: #c0c0c0;
  }

  .faq_question {
    font-size: 1.5rem;
    font-weight: 500;
    line-height: 1.3;
    padding-right: 100px;
    transition: color 0.3s;
  }

  .faq_question_button {
    position: relative;
    margin-right: 25px;
    background: white;
  }

  .faq_question_button span {
    position: absolute;
    top: 50%;
    left: 0;
    width: 20px;
    height: 2px;
    background-color: #fff;
    transition: background-color 0.3s;
  }

  .faq_question_button .cross_line {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 20px;
    height: 2px;
    background: #fff;
    transform: rotate(90deg);
    transition: transform 0.3s;
  }

  .faq_answer {
    font-size: 1.3rem;
    line-height: 1.5;
    font-weight: 200;
    margin: 0;
    color: #bfc0be;
    max-height: 0;
    overflow: hidden;
    transition: all 0.3s;
  }

  .faq_element_wrapper.expanded .faq_question_button .cross_line {
    transform: rotate(0);
  }

  .faq_element_wrapper.expanded .faq_answer {
    max-height: var(--height);
  }

  @media (max-width: 650px) {
    .faq_element_wrapper {
      padding-block: 10px;
    }
    .faq_question {
      padding-right: 20px;
      font-size: 1.3rem;
    }

    .faq_answer {
      font-size: 1.1rem;
    }
  }
</style>
