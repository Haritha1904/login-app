<script>
	import MachineCard from '$lib/MachineCard.svelte';
	import { onMount } from "svelte";
	import { Chart, registerables } from "chart.js";
	import ChartDataLabels from "chartjs-plugin-datalabels";

	Chart.register(...registerables, ChartDataLabels);

	let chartCanvas;
  
	let machines = [
	  { name: 'RBD Machine1 - Take up 1', status: 'ACTIVE', production: '1.52 t', oee: '29.65%' },
	  { name: 'RST Machine - 1', status: 'BREAKDOWN', production: '377 m', oee: '1.73%' },
	  { name: 'RST Machine - 2', status: 'BREAKDOWN', production: '2 m', oee: '0%' },
	  { name: 'RBD Machine2 - Take up 1', status: 'BREAKDOWN', production: '0.46 t', oee: '4.17%' },
	  { name: 'CCR Machine', status: 'BREAKDOWN', production: '4981.9 kg', oee: '21.35%' },
	  { name: 'RBD Machine2 - Take up 2', status: 'BREAKDOWN', production: '0 t', oee: '0%' },
	  { name: 'RBD Machine2 - Take up 1', status: 'BREAKDOWN', production: '0.58 t', oee: '6.86%' },
	  { name: 'Coiler', status: 'OFFLINE', production: '0 kg', oee: '0%' }
	];
	// helper: convert production strings into numbers (ignores units)
	function parseProduction(p) {
	  return parseFloat(p);
	}

	onMount(() => {
	  new Chart(chartCanvas, {
		type: "bar",
		data: {
		  labels: machines.map(m => m.name),
		  datasets: [
			{
			  label: "Production",
			  data: machines.map(m => parseProduction(m.production)),
			  backgroundColor: "#f97316", // Tailwind orange
			  borderRadius: 6
			}
		  ]
		},
		options: {
		  responsive: true,
		  plugins: {
			legend: { display: false },
			tooltip: {
			  callbacks: {
				label: ctx => `${ctx.raw} units`
			  }
			},
			datalabels: {
			  color: "#374151",
			  anchor: "end",
			  align: "end",
			  formatter: value => value
			}
		  },
		  scales: {
			y: {
			  beginAtZero: true,
			  ticks: { color: "#6b7280" }
			},
			x: {
			  ticks: { color: "#6b7280" }
			}
		  }
		},
		plugins: [ChartDataLabels]
	  });
	});
  
	let currentDateTime = new Date().toLocaleString();
	setInterval(() => {
	  currentDateTime = new Date().toLocaleString();
	}, 1000);

	let machineData = [
    {
      name: "RBD Machine1 - Take up 1",
      breakdowns: 16,
      jobsCompleted: 6,
      runtime: "48.1%",
      runtimeColor: "text-red-500",
      production: "4.4 t"
    },
    {
      name: "RST Machine - 2",
      breakdowns: 15,
      jobsCompleted: 0,
      runtime: "54.7%",
      runtimeColor: "text-red-500",
      production: "7721 m"
    },
    {
      name: "CCR Machine",
      breakdowns: 4,
      jobsCompleted: 0,
      runtime: "89.6%",
      runtimeColor: "text-green-500",
      production: "31,963.17 kg"
    },
    {
      name: "Coiler",
      breakdowns: 0,
      jobsCompleted: 0,
      runtime: "100%",
      runtimeColor: "text-green-500",
      production: "35,133 kg"
    }
  ];

  </script>  
	
	<!-- NAVBAR-->

	<nav class= "bg-white border-b border-gray-200 px-4 py-2 flex justify-between items-center">
		<div class="flex items-center gap-0">
			<img src="https://keccables.ifactory.ai/assets/images/solidRsLogo.png" alt="Company logo" class="logo" />
				<h2 class="text-xl font-semibold font-sans">ifactory</h2>
				<div class="flex gap-6 pl-8 text-gray-600">
					<div class="cursor-pointer hover:text-black">Dashboard</div>
					<div class="cursor-pointer hover:text-black">Machines</div>
					<div class="cursor-pointer hover:text-black">Production</div>
					<div class="cursor-pointer hover:text-black">Tickets</div>
					<!-- <div class="cursor-pointer hover:text-black flex items-center gap-1">
						Jobs <span class="text-sm">▼</span>
					</div> -->
					<button class="flex items-center space-x-2">
						<span>Jobs</span>
						<svg xmlns="http://www.w3.org/2000/svg" 
							 fill="none" 
							 viewBox="0 0 24 24" 
							 strokeWidth={1.5} 
							 stroke="currentColor" 
							 class="w-5 h-5">
						  <path strokeLinecap="round" strokeLinejoin="round" d="m19.5 8.25-7.5 7.5-7.5-7.5" />
						</svg>
					  </button>
					  
					<div class="cursor-pointer hover:text-black">Operators</div>
					<div class="cursor-pointer hover:text-black">CBM</div>
					<div class="cursor-pointer hover:text-black">Energy</div>
				</div>
		</div>
		<img src="https://cdn-icons-png.flaticon.com/512/1144/1144760.png" alt="Profile" class="w-6 h-6 rounded-full" />
	</nav>
  
	<!-- DASHBOARD HEADER -->
	<div class="flex justify-between items-center mt-2 mb-2 px-4">

		<div>
			<h4 class="text-xl font-cold font-sans">Factory Dashboard</h4>
		</div>
		<div class="flex gap-4 items-center">
			
			<button class="flex items-center space-x-2 border px-3 py-1 rounded  border-gray-200">
				<span>Shift</span>
					<svg xmlns="http://www.w3.org/2000/svg" 
						fill="none" 
						viewBox="0 0 24 24" 
						strokeWidth={1.5} 
						stroke="currentColor" 
						class="w-5 h-5">
					<path strokeLinecap="round" strokeLinejoin="round" d="m19.5 8.25-7.5 7.5-7.5-7.5" />
					</svg>
			</button>

		<!-- <div class="flex items-center gap-1 cursor-pointer border px-3 py-1 rounded">
			<span>Shift</span>
			<span class="text-sm text-gray-500">▼</span>
		</div> -->
			<button>
				<div class="flex items-center gap-2 border px-3 py-1 rounded  border-gray-200">
					<span>📅</span>
					<span>{currentDateTime}</span>
				</div>
			</button>
			
			<button >
				<div class="flex items-center  bg-white text-black  cursor-pointer border px-3 py-1 rounded  border-gray-200">
					<span class=" px-1 py-1">Export</span> 
					<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6">
						<path stroke-linecap="round" stroke-linejoin="round"
						 d="M19.5 14.25v-2.625a3.375 3.375 0 0 0-3.375-3.375h-1.5A1.125 1.125 0 0 1 13.5 7.125v-1.5a3.375 3.375 
						 0 0 0-3.375-3.375H8.25m2.25 0H5.625c-.621 0-1.125.504-1.125 1.125v17.25c0 .621.504 1.125 1.125 1.125h12.75c.621 0 
						 1.125-.504 1.125-1.125V11.25a9 9 0 0 0-9-9Z" />
					</svg>			
				</div>
			</button>

		
		</div>
	</div>
  
	<!-- STAT CARD -->

	<div class="flex flex-wrap gap-4 px-4 mt-4">

		<div class="flex-1 min-w-[200px] border rounded-lg border-gray-300 p-4">
			<h2 class=" text-sr font-semibold font-sans flex items-center gap-50 ">Total Production
			
			<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" 
			stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-activity-icon lucide-activity stroke-gray-500">
			<path d="M22 12h-2.48a2 2 0 0 0-1.93 1.46l-2.35 8.36a.25.25 0 0 1-.48 0L9.24 2.18a.25.25 0 0 0-.48 0l-2.35 8.36A2 2 0 0 1 4.49 12H2"/>
			</svg>
			</h2>

			<h3 class="text-3xl font-spacegrotesk font-bold text-sans">379 m<br/>+<br/>7.54 t</h3>
			<span class="text-red-500">↑99.8%</span> <span class="text-gray-500">from last 2 hours 30 mins </span>
		</div>

		<div class="flex-1 min-w-[200px] border rounded-lg border-gray-300 p-4">
			<div class=" flex items-center gap-50">
			<h2 class=" text-sr font-semibold">No. of Breakdowns</h2>
			<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" 
			class="lucide lucide-split-icon lucide-split stroke-gray-500"><path d="M16 3h5v5"/><path d="M8 3H3v5"/><path d="M12 22v-8.3a4 4 0 0 0-1.172-2.872L3 3"/><path d="m15 9 6-6"/></svg>
			</div>
			<h2 class="text-3xl font-bold">16</h2>
			<span class="text-green-500">↑12%</span> <span class="text-gray-500">from last 2 hours 30 mins </span>
		</div>

		<div class="flex-1 min-w-[200px] border rounded-lg border-gray-300 p-4">
			<h2 class=" text-sr font-semibold flex items-center gap-50">Active Runtime
				<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-sparkles-icon lucide-sparkles stroke-gray-500">
					<path d="M11.017 2.814a1 1 0 0 1 1.966 0l1.051 5.558a2 2 0 0 0 1.594 1.594l5.558 1.051a1 1 0 0 1 0 1.966l-5.558 1.051a2 2 0 0 0-1.594 1.594l-1.051 5.558a1 1 0 0 1-1.966 
					0l-1.051-5.558a2 2 0 0 0-1.594-1.594l-5.558-1.051a1 1 0 0 1 0-1.966l5.558-1.051a2 2 0 0 0 1.594-1.594z "/><path d="M20 2v4"/><path d="M22 4h-4"/><circle cx="4" cy="20" r="2"/></svg>
			</h2>
			<h2 class="text-3xl font-bold">24%</h2>
			<span class="text-red-500">↑34.8%</span> <span class="text-gray-500">from last 2 hours 30 mins </span>
		</div>

		<div class="flex-1 min-w-[200px] border rounded-lg border-gray-300 p-4 ">
			<div class="flex items-center gap-50">
			<h2 class=" text-sr font-semibold font-sans flex items-center  "> Jobs Completed</h2>
			<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" 
			stroke-linejoin="round" class="lucide lucide-check-check-icon lucide-check-check stroke-gray-500"><path d="M18 6 7 17l-5-5"/><path d="m22 10-7.5 7.5L13 16"/></svg>
			</div>
			<h2 class="text-3xl font-bold">1</h2>
			<span class="text-red-500">↑9.8%</span> <span class="text-gray-500">from last 2 hours 30 mins </span>
		</div>

	</div>

  <!-- <div class="stats-cards">
	<div class="stat"><strong>Total Production</strong><h3>379 m<br>+ <br> 7.54 t</h3><span style="color: red">↑99.8%</span>  from last 2 hours 30 mins</div>
	<div class="stat"><strong>No. of Breakdowns</strong><h2>16</h2><span style="color: red">↑12%</span>  from last 2 hours 30 mins</div>
	<div class="stat"><strong>Active Runtime</strong><h2>24%</h2><span style="color: red">↑34.8%</span>  from last 2 hours 30 mins</div>
	<div class="stat"><strong>Jobs Completed</strong><h2>1</h2><span style="color: red">↑9.8%</span>  from last 2 hours 30 mins</div>
  </div> -->


  
  
   <!-- MACHINE GRID -->
	<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-5 p-5 items-start">

	{#each machines as machine}
	  <MachineCard {...machine} />	
	{/each}
  </div>

  <!-- FLEX -->
  <div class="flex items-center gap-50 ">
  <!-- BAR GRAPH -->
  <div class="p-2">
  	<div class="bg-white rounded-lg shadow p-4">
    	<h2 class="text-lg font-semibold mb-4">Production Across Machines</h2>

		<div class="w-[500px] h-[300px] p-4 bg-white shadow rounded-xl">
  			<canvas bind:this={chartCanvas}></canvas>
	</div>

  </div>
</div>

	<div class="bg-white rounded-lg shadow p-4 h-[350px] w-[320px] overflow-y-auto">
  		<h2 class="text-lg font-semibold mb-3">Production By Machines</h2>

  			<ul class="space-y-3">
    		{#each machineData as machine}
      			<li class="flex justify-between items-start border-b pb-2">
        <!-- Left Info -->
        	<div>
          	<p class="font-medium text-gray-800">{machine.name}</p>
          	<p class="text-sm text-gray-500">
            Breakdowns : {machine.breakdowns}, Jobs Completed : {machine.jobsCompleted}, Active Runtime : 
            <span class={machine.runtimeColor}>{machine.runtime}</span>
          	</p>
        	</div>

        <!-- Production -->
        	<p class="font-semibold text-gray-900 whitespace-nowrap ml-2">
          	{machine.production}
        	</p>
      			</li>
    		{/each}
  			</ul>
	</div>
	</div>
  
  <a href="/login">Logout</a>
  
  <style lang="postcss">
	/* @import "tailwindcss"; */
	@reference "tailwindcss";

	.logo { width: 50px; height: 50px; display:flex }
/* 	
	nav {
	  background-color: white;
	  border-bottom: 1px solid #ddd;
	  padding: 0.5rem 1rem;
	  display: flex;
	  justify-content: space-between;
	  align-items: center;
	}
	.nav-left { display: flex; align-items: center; gap: 0rem; }
	
	.tit{display: flex; font-family: sans-serif;}
	.dash{font-family: sans-serif;padding-top: -5rem;	}
	.navtabs { display: flex; gap: 23px;padding-left: 2rem; }
	.nav-item { color: grey; cursor: pointer; }
	.profile-icon { width: 25px; height: 25px; border-radius: 20%; }
  
	.com-dash { display: flex; justify-content: space-between; align-items: center; margin-top: -1rem; margin-bottom: -1rem; }
	.dash { font-size: 1.5rem; font-weight: bold; }
	.top-controls { display: flex; gap: 1rem; }
  
	.stats-cards { display: flex; gap: 1rem; margin-top: 1rem; flex-wrap: wrap; }
	.stat { flex: 1; border: 1px solid #eee; padding: 1rem; border-radius: 10px; min-width: 200px; }
   */
	.machine-grid {
	  display: grid;
	  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
	  gap: 18px;
	  padding: 16px;
	  align-items: start;
	}
  </style>
   