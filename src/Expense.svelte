<script>
  import { getContext, createEventDispatcher } from "svelte";
  export let expense;
  let { id, name, amount } = expense;
  let displayAmount = false;

  function toggleDisplayAmount() {
    displayAmount = !displayAmount;
  }

  const removeExpense = getContext("remove");
  const dispatch = createEventDispatcher();
</script>

<article class="single-expense">
  <div class="expense-info">
    <h2>
      {name}
      <button class="amount-btn" on:click={toggleDisplayAmount}>
        <i class="fas fa-caret-down" />
      </button>
    </h2>
    {#if displayAmount}
      <h4>amount:${amount}</h4>
    {/if}
  </div>
  <div class="expense-buttons">
    <button class="expense-btn edit-btn">
      <i class="fas fa-pen" />
    </button>
    <!--button class="expense-btn delete-btn" on:click={() => removeExpense(id)}>
      <i class="fas fa-trash" />
    </button-->
    <button
      class="expense-btn delete-btn"
      on:click={() => dispatch('delete', { id, name: 'test' })}>
      <i class="fas fa-trash" />
    </button>
  </div>
</article>
