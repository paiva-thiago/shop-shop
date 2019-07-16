<script>
	import Header from './Header.svelte'
	import Gondola from './Gondola.svelte'
	import Footer from './Footer.svelte'
	let promise = pegaLojinha()
	let sociaLinks = [
						{"social":"facebook",  "url" :   ""},
						{"social":"twitter",   "url" :   "paivocodes"},
						{"social":"github"   , "url" :   "paiva-thiago"},
						{"social":"pinterest", "url" :   ""},
						{"social":"lastfm"   , "url" :   "cheimesears"},
						{"social":"linkedin" , "url" :   "thiagormp"}
					];
	Array.prototype.shuffle = function(){
	return this.map((a) => ({sort: Math.random(), value: a}))
			.sort((a, b) => a.sort - b.sort)
			.map((a) => a.value)
	}
	
	async function pegaLojinha() {
		let ret={}
		const res = await fetch(`resources/data.json`)
		const text = await res.text()
		let result = []
		if (res.ok) {
			result= JSON.parse(text)
		} else {
			throw new Error(text)
			return ret
		}
		ret = result
		ret.gondola = await ret.gondola.map((x)=>{
			x.src='./images/'.concat(x.img).concat('.jpg')
			x.valor= parseFloat(x.valor).toFixed(2).replace('.',','  )
  			return x
		})
		ret.gondola = result.gondola.shuffle()	
		
		return ret
	}

</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Barriecito&display=swap');
@import url('https://fonts.googleapis.com/css?family=Raleway');
@import url('https://weloveiconfonts.com/api/?family=zocial');
* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }
  body{
      height:100vh;      
      background: transparent;      
      font-family: 'Raleway', sans-serif;

  }   
  .sos{color:red;font-size: 18px; font-family: monospace;}
</style>
<svelte:head>
	<title>ShopShop - Sua loja estática!</title>
</svelte:head>

<body>
	{#await promise}
		<p class="sos">aguarde... ou peça socorro!</p>
	{:then retorno}
		<Header title={retorno.tituloLoja} socials={retorno.socials} img={retorno.imgBanner} />
		<Gondola itens={retorno.gondola}/>
	{:catch error}
		<p class="sos">{error.message}</p>
	{/await}
	<Footer/>
</body>