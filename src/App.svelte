<script>
	let promise = pegaLojinha();

	async function pegaLojinha() {
		const res = await fetch(`resources/stock.json`);
		const text = await res.text();

		if (res.ok) {
			return JSON.parse(text);
		} else {
			throw new Error(text);
		}
	}

</script>


{#await promise}
	<p>...waiting</p>
{:then lujinha}
	<ol>
		{#each lujinha as { id, nome,valor,descricao }, i}
		<li>{nome} {valor}</li>
		<details>{descricao}</details>

	{/each}
	</ol>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}