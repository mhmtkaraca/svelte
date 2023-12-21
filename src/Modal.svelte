<script>
  export let show;
  export let isForm;
  let isPromo = true;
  
</script>

{#if show}
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <div class="backdrop" class:promo={isPromo} on:click|self>
    <div class="modal">
      <button class="button" on:click>X</button>
      
      {#if isForm}
        <slot name="form"></slot>
        
         
      {/if}
      {#if !isForm}
        <slot name="delete"></slot>
        
         
      {/if}
    </div>
  </div>
{/if}


<style>
  .backdrop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: rgba(0, 0, 0, 0.5);
    z-index: 10;
  }
  .modal {
    flex-direction: column;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    position: fixed;
    top: 10vh;
    min-height: 300px;
    left: 25%;
    width: 50%;
    background: white;
    border-radius: 12px;
    z-index: 100;
    padding: 10px;
  }
  .promo .modal {
    background: yellow;
  }
  .button {
    position: absolute;
    top: 0;
    right: 0;
    background: transparent;
    border: none;
    font-size: 2rem;
    cursor: pointer;
  }
</style>
