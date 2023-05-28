<template>
  <div class="about">
    <transition 
    appear
    name="fadeTitle"
    @before-enter="beforeEnter"
    @enter="enter"
    @after-enter="afterEnter">
      <h1 v-if="showTitle">About</h1>
    </transition>
<div>
  <p>
    In the realm of tasks and goals untold, <br />
    Where dreams and duties brightly unfold,<br />
    A humble tool emerges, standing tall, <br />
    The mighty Todo List, holding them all.
  </p>
  <p>
    With pen in hand or pixels on a screen, <br />
    It captures aspirations, crisp and clean, <br />
    A symphony of checkboxes, neatly arrayed, <br />
    Guiding our steps through each busy crusade.
  </p>
  <p>
    In the morning's embrace, we pen our desires, <br />
    A chorus of items, each with its own fires, <br />
    From the simplest chores to grand ambitions, <br />
    The Todo List nurtures our focused missions.
  </p>
  <p>
    It whispers reminders, a gentle command, <br />
    Calling forth action with a guiding hand, <br />
    A dance with time, it keeps us on track, <br />
    Unveiling order, banishing slack.
  </p>
  <p>
    From dawn till dusk, it faithfully guides, <br />
    Urging us forward, where success resides, <br />
    A silent companion, steadfast and true, <br />
    The Todo List keeps us grounded and grew.
  </p>
  <p>
    Yet amidst the tasks, let's not forget, <br />
    To savor the moments, with no regret, <br />
    For life's beauty lies beyond mere tasks, <br />
    In love, laughter, and nature's intricate masks.
  </p>
  <p>
    So let the Todo List be our loyal aid, <br />
    But also embrace the joy of a serenade, <br />
    Balance the lists with a touch of delight, <br />
    And make each day a radiant light.
  </p>
</div>
  </div>
</template>

<script>
  import { ref } from 'vue'

  export default {
    setup() {
      const showTitle = ref(true)

      const beforeEnter = () => {
        console.log('before enter')
      }
      const enter = () => {
        console.log('enter')
      }
      const afterEnter = () => {
        console.log('after enter')

        setTimeout(() => showTitle.value = false, 2000)
      }

      return {beforeEnter, enter, afterEnter, showTitle}
    }
  }
</script>

<style>
  .about {
    max-width: 600px;
    margin: 20px auto;
  }
</style>
