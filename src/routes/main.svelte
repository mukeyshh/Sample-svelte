<script>
    export let coin;
   
    import { onMount } from "svelte";
     import Chart from "chart.js";
     onMount(async () => {});
     function renderChart() {
       const ctx = document.getElementById("myChart").getContext("2d");
       const chart = new Chart(ctx, {
         type: "line",
         data: {
           labels: ["Day 1","Day 2","Day 3","Day 4","Day 5","Day 6","Day 7",],
           datasets: [
             {
               label: "Price in usd($)",
               backgroundColor: "rgb(147, 197, 253)",
               borderColor: "rgb(147, 197, 253)",
               data: coin.sparkline_in_7d.price,
             }
           ]
         },
         options: {}
       });
     }
   
     onMount(renderChart);
   </script>
   
   <div class=" flex flex-wrap md:flex-nowrap  min-w-full  bg-blue-100 ">
   
     <div class="  inline p-5 ml-10 sm:p-2  sm:mx-1 mt-5 w-full  ">
       <h1 class="uppercase text-2xl pl-10">
         <strong>{coin.id}({coin.symbol})</strong>
       </h1>
       <!-- {#if coin.id} -->
       <ul class="mt-10 mb-10 pl-10">
         <li class="flex mb-1 ">
           <div class="text-lg text-gray-500 mr-3 ">Market rank</div>
           :
           <div
             class="ml-3 px-2 py-1 rounded shadow-lg text-sm bg-black text-white"
           >
             Rank
             {coin.market_cap_rank}
           </div>
         </li>
   
         <li class="flex mb-1 ">
           <div class="text-lg text-gray-500 mr-3 ">Fully Diluted Valuation</div>
           :
           <div class="ml-3 px-2 py-1 rounded shadow-lg text-sm bg-blue-300">
             {coin.fully_diluted_valuation}
           </div>
         </li>
         <li class="flex mb-1 ">
           <div class="text-lg text-gray-500 mr-3 ">Sparkline</div>
           :
           <div
             class="ml-3 px-2 py-1 rounded shadow-lg text-sm flex-col  bg-blue-300"
           >
             {coin.sparkline_in_7d.price[0]},<br/>{coin.sparkline_in_7d.price[99]}
           </div>
         </li>
         <li class="flex mb-1 ">
           <div class="text-lg text-gray-500 mr-3 ">Atl</div>
           :
           <div class="ml-3 px-2 py-1 rounded shadow-lg text-sm bg-blue-300">
             {coin.atl}
           </div>
         </li>
         <li class="flex mb-1 ">
           <div class="text-lg text-gray-500 mr-3 ">Atl Date</div>
           :
           <div class="ml-3 px-2 py-1 rounded shadow-lg text-sm bg-blue-300">
             {coin.atl_date}
           </div>
         </li>
         <li class="flex mb-1 ">
           <div class="text-lg text-gray-500 mr-3 ">Atl change percentage</div>
           :
           <div class="ml-3 px-2 py-1 rounded shadow-lg text-sm bg-blue-300">
             {coin.atl_change_percentage}
           </div>
         </li>
         <li class="flex mb-1 ">
           <div class="text-lg text-gray-500 mr-3 ">Current Price</div>
           :
           <div class="ml-3 px-2 py-1 rounded shadow-lg text-sm bg-blue-300">
             {coin.current_price}
           </div>
         </li>
   
         <li class="flex mb-1 ">
           <div class="text-lg text-gray-500 mr-3 ">Total Volume</div>
           :
           <div class="ml-3 px-2 py-1 rounded shadow-lg text-sm bg-blue-300">
             {coin.total_volume}
           </div>
         </li>
       </ul>
       <!-- {/if} -->
     </div>
   
   
     
   
     <div class="w-full flex flex-col sm:flex-wrap items-end  mt-8  sm:mx-1 ">
       <h1 class="text-3xl text-right mr-8 pr-10 ">
         <h5>Current Price</h5><br><h2><strong>${coin.current_price}</strong></h2>
       </h1>
   
       <div class="flex  mr-8 text-right mt-20 ">
         <div class="flex-col mr-5  ">
           <div class="flex-col ">
             <strong>Market Cap </strong><br />
             <h4>${coin.market_cap}</h4>
           </div>
           <div class="flex-col">
             <strong>24h Low/24h High</strong><br />
             <h4>${coin.high_24h}/${coin.low_24h}</h4>
           </div>
         </div>
         <div class="flex-col pr-10 ">
           <div>
             <strong>Circulating Supply</strong><br />
             <h4>${coin.circulating_supply}</h4>
           </div>
           <div class="flex-col ">
             <strong>Max Supply</strong><br />
             <h4>${coin.max_supply}</h4>
           </div>
         </div>
       </div>
     </div>
   
   
   </div>
   
   <!-- <button on:click={renderChart}>Load</button> -->
   
   
   <div class="bg-blue-100">
     <h1 class="text-3xl  text-center "> <strong>Price Change in last 7 days</strong></h1>
     <canvas class=" max-w-xl mx-auto" id="myChart"></canvas>
   </div>
   
   
   
   
   