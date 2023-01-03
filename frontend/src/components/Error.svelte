<script>
  export let error;
</script>

{#if typeof error.detail === "string"}
  <div class="alert alert-danger" role="alert">
    <div>
      {error.detail}
    </div>
  </div>
{:else if typeof error.detail === "object" && error.detail.length > 0}
  <div class="alert alert-danger" role="alertdialog">
    {#each error.detail as err, i}
      <li>
        <strong>{err.loc[1]}</strong> : {err.msg}
      </li>
    {/each}
  </div>
{/if}
