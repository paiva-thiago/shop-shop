<script>
	import Header from './Header.svelte'
	import Gondola from './Gondola.svelte'
	import Footer from './Footer.svelte'
	let promise = pegaLojinha()

	Array.prototype.shuffle = function(){
	return this.map((a) => ({sort: Math.random(), value: a}))
			.sort((a, b) => a.sort - b.sort)
			.map((a) => a.value)
	}

	async function pegaLojinha() {
		const res = await fetch(`resources/stock.json`)
		const text = await res.text()
		let result = []
		if (res.ok) {
			result= JSON.parse(text)
		} else {
			throw new Error(text)
			return result
		}
		result = await result.map((x)=>{
			x.src='./images/'.concat(x.img).concat('.jpg')
			x.valor= parseFloat(x.valor).toFixed(2).replace('.',','  )
  			return x
		})
		return result.shuffle()
	}

</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Barriecito&display=swap');
@import url('https://fonts.googleapis.com/css?family=Raleway');
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
    
</style>

<body>
	{#await promise}
		<p>...waiting</p>
	{:then itens}
		<Header title="Loja ©"/>
		<Gondola itens={itens}/>
	{:catch error}
		<p style="color: red">{error.message}</p>
	{/await}
	<Footer/>
</body>