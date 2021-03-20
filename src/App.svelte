<script>
	import Home from "./components/Home.svelte";
	import { Router, Link, Route } from "svelte-routing";
	import MainRoute from "./routes/main.svelte";

	export let url = "";

	let items = [];

	const dataPromise = fetch(
		`https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&sparkline=true&price_change_percentage=7d`
	)
		.then((r) => r.json())
		.then((data) => {
			items = data;
			console.log(items);
		});
</script>

<Router {url}>
	<nav class="flex items-center justify-between flex-wrap bg-gray-400 p-1 ">
		<div class="flex items-center flex-shrink-0 mr-6 max-w-xs">
			<img
				class="mr-6"
				src="https://static.coingecko.com/s/coingecko-logo-d13d6bcceddbb003f146b33c2f7e8193d72b93bb343d38e392897c3df3e78bdd.png"
				alt=""
			/>
		</div>

		<div class="w-full block flex-grow  sm:flex sm:items-center sm:w-auto ">
			<div class="text-sm sm:flex-grow">
				<Link
					to="/"
					class="block mt-4 sm:inline-block sm:mt-0  text-xl  text-teal-200 hover:text-white mr-4 "
					>Home</Link
				>
			</div>

			<div>
				<a
					href="/"
					class=" inline-block  px-4 py-2  text-xl leading-none border rounded text-white border-white hover:text-transparent hover:border-transparent hover:text-blue-500 hover:bg-white mt-4 md:mt-0 "
				>
					Login
				</a>
			</div>
		</div>
	</nav>

	<div>
		{#if dataPromise}
			<Route path="/"><Home {items} /></Route>
			{#each items as item}
				<Route path={item.id}>
					<!-- <MainRoute coinName={item.id} /> -->
					<MainRoute coin={item} />
				</Route>
			{/each}
		{/if}
	</div>
</Router>
