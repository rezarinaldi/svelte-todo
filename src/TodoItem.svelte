<script>
  import { createEventDispatcher } from "svelte";
  import { fly } from "svelte/transition";

  export let id;
  export let title;
  export let completed;

  const dispatch = createEventDispatcher();

  function deleteTodo() {
    dispatch("deleteTodo", { id: id });
  }

  function toggleCompleted() {
    dispatch("toggleComplete", { id: id });
  }
</script>

<style>

</style>

<label
  class="flex justify-between py-2 my-2 mt-0 text-gray-500 font-bold
  odd:bg-gray-200 even:bg-blue-100"
  transition:fly={{ t: 20, duration: 300 }}>
  <div class="flex items-center">
    <input
      class="flex ml-2 leading-tight"
      type="checkbox"
      bind:checked={completed}
      on:change={toggleCompleted} />
    <span class="pl-2" class:completed>{title}</span>
  </div>
  <div class="text-xl mr-2 hover:text-blue-500" on:click={deleteTodo}>x</div>
</label>
