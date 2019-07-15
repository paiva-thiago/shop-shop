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
  .item img{width:300px; max-height: 380px;}
  .img-item{width:300px;height: 400px;}
</style>
<div class="item">
  <strong>{nome}</strong>  
  <em>R$ {valor}</em>
  <span class="img-item"><img {src} alt={nome}></span>
  <span>{descricao}</span>

</div>