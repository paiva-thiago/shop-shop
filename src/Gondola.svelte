<script>
    import Item from './Item.svelte'
    export let itens;
</script>
<style>
    .gondola{
      display: grid;
      grid-template-columns: auto auto auto auto auto;
      background-color:transparent;
  }
</style>
<div class="gondola">
	{#each itens as { id, nome,valor,descricao,src }, i}
	    <Item {nome} {valor} {descricao} {src}/>
    {/each}
</div>