<script>
	import Header from './Header.svelte'
	import Gondola from './Gondola.svelte'
	let promise = pegaLojinha()

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
  			return x
		});          
		return result
	}

</script>

<style>
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
		<Header/>
		<Gondola itens={itens}/>
	{:catch error}
		<p style="color: red">{error.message}</p>
	{/await}
</body>