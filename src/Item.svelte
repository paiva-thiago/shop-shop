<script>
    export let nome
    export let valor
    export let descricao
    export let src
</script>
<style>
  .item {
    font-size: 1pc;
    margin:0.1pc;
    padding:1pc;
    background-color:#FFF;
    font-family: 'Raleway', sans-serif;
    text-align: center;      
    cursor: pointer;
    display: grid;
    grid-template-columns: auto;

  }
  .item img{width:150px;}
</style>
<div class="item">
  <strong>{nome}</strong>  
  <em>R$ {parseFloat(valor).toFixed(2).replace('.',','  )}</em>
  <span><img {src} alt={nome}></span>
  <span>{descricao}</span>

</div>