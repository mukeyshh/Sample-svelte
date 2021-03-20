<script>
	import TableSort from "./TableSort.svelte";
	import { Link } from "svelte-routing";

	export let items = [];
</script>

<main>
	<div class="container mx-auto px-4 sm:px-8">
		<div class="py-8">
			<div>
				<h2 class="text-4xl font-semibold leading-tight text-center ">
					Crypto Data
				</h2>
			</div>
			<div class="-mx-4 sm:-mx-8 px-4 sm:px-8 py-4 overflow-x-auto">
				<div class="inline-block min-w-full shadow rounded overflow-hidden">
					<TableSort {items} class="min-w-full leading-normal">
						<tr
							slot="thead"
							class="px-3 py-2 my-4  bg-gray-500 text-center text-xl cursor-pointer font-semibold text-gray ">
						<th data-sort="market_cap_rank" data-sort-initial="ascending"
						>Market Cap Rank</th>
							<th data-sort="id">Id</th>
							<th data-sort="symbol">Symbol</th>
							<th data-sort="name">Name</th>
							<th data-sort="atl" data-sort-initial="ascending">Atl</th>
							<th data-sort="atl_date" data-sort-initial="ascending"
								>Atl Date</th
							>
							<th
								data-sort="atl_change_percentage"
								data-sort-initial="ascending">Atl change(%)</th
							>
							
							
							<th data-sort="current_price" data-sort-initial="ascending"
								>Current Price($)</th
							>
							
						
							<th data-sort="total_volume" data-sort-initial="ascending"
								>Total Volume</th
							>
							
							
							<th data-sort="last_updated">Last Updated</th>
						</tr>

						<tr
							slot="tbody"
							let:item
							class="px-3 py-2 border-2 border-gray-200 bg-gray-100 text-center text-sm font-semibold text-gray "
						>
						<td>{item.market_cap_rank}</td>
							<!-- <td ><a href={item.id}>{item.id}</a></td> -->
							<td><Link to={item.id}>{item.id}</Link></td>
							<!-- <Route path="{item.id}" component={item.id} /> -->
							<td>{item.symbol}</td>
							<td>{item.name}</td>
							<td>{item.atl}</td>
							<td>{item.atl_date}</td>
							<td>{item.atl_change_percentage}</td>
							
							<td>{item.current_price}</td>
							
							
							<td>{item.total_volume}</td>
							
							<td>{item.last_updated}</td>
						</tr>
					</TableSort>
				</div>
			</div>
		</div>
	</div>
</main>
