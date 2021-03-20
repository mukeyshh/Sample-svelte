<script>
	import Table from "./Table.svelte";
	export let items = [];

	// const dataPromise = fetch(
	// 	`https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&sparkline=false`
	// )
	// 	.then((r) => r.json())
	// 	.then((data) => {
	// 		items = data;
	// 		console.log(items);
	// 	});
</script>

<main>
	<Table {items} />
	
</main>
