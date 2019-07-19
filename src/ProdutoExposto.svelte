<script>
    export let produto
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
</style>
	<div class="area_produto">
		<div class="container">
			<div class="row s_product_inner">
				<div class="col-lg-6">
					<div class="s_product_img">
						<div id="carouselExampleIndicators" class="carousel slide" data-ride="carousel">							
							<div class="carousel-inner">
								<div class="carousel-item active">
									<img class="d-block w-100" id="imagem" src="{produto.url}" alt="{produto.descricao}">
								</div>								
							</div>
						</div>
					</div>
				</div>
				<div class="col-lg-5 offset-lg-1">
					<div class="s_product_text">
						<h3>{produto.nome}</h3>
						<h2>{produto.valor}</h2>
						
						<p id="descricao"></p>						
						<div class="card_area">
							<!-- INICIO FORMULARIO BOTAO PAGSEGURO -->
							<form target="_blank" action="https://pagseguro.uol.com.br/checkout/v2/cart.html?action=add" method="post">
								<!-- NÃO EDITE OS COMANDOS DAS LINHAS ABAIXO -->
								<input type="hidden" name="itemCode" value="{produto.pagseg}" />
								<input type="hidden" name="iot" value="button" />
								<input alt="Pague com PagSeguro - é rápido, grátis e seguro!" aria-label="Pague com PagSeguro - é rápido, grátis e seguro!" type="image" src="https://stc.pagseguro.uol.com.br/public/img/botoes/pagamentos/120x53-comprar-preto.gif" name="submit"  />																
							</form>
							<a class="genric-btn info circle " href="javascript:history.back()">Voltar</a>							
								<!-- FINAL FORMULARIO BOTAO PAGSEGURO -->															
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>