<script>
    // Sample machine details (later this will come from backend / params)
    let machine = {
      name: "RST Machine - 1",
      status: "Drum Fixing",
      quantity: "8888.0 m",
      avgSpeed: "27 m/min",
      operator: "Akhilesh",
      job: "AL59 Zebra",
      uptime: "318 mins",
      downtime: "260 mins",
      activeRuntime: "55.02%",
      energy: "303.0320 kWh",
      oee: "49.65%"
    };
  
    // Example chart data (later we’ll fetch real downtime reasons)
    let chartData = [
      { label: "Stopped", value: 17, color: "#2E7D32" },
      { label: "Idle", value: 10, color: "#9E9D24" },
      { label: "Drum Fixing", value: 25, color: "#C62828" },
      { label: "Loading", value: 15, color: "#1565C0" },
      { label: "Mechanical Breakdown", value: 20, color: "#00ACC1" },
      { label: "Quality Testing", value: 8, color: "#43A047" },
      { label: "Wire Break", value: 12, color: "#FB8C00" },
      { label: "Operator Not Available", value: 6, color: "#F4511E" }
    ];
  </script>
  
  <div class="p-6">
    <!-- Header -->
    <h1 class="text-2xl font-bold mb-4">
      Machine Details › {machine.name} › Downtime Report
    </h1>

    <div class="flex flex-1 gap-5 text-gray-400 font-semibold">
      <h1>Performance Report</h1>
      <h1>Production Report</h1>
      <h1>Downtime Report</h1>

    </div>
  
    <!-- Info Grid -->
    <div class="grid grid-cols-2 md:grid-cols-2 lg:grid-cols-5 gap-0  mb-2">
      <div class=" w-70 h-30 m-4 bg-white-900 border rounded-lg border-gray-200 p-2   ">
        <p class="text-black-500 m-3 font-semibold">Status</p>
        <p class="text-red-600 font-bold m-3 text-2xl">{machine.status}</p>
      </div>
      <div class="w-70 h-30 m-4 border rounded-lg border-gray-200 p-2 gap-2">
        <p class="text-black-500 m-3 font-semibold">Quantity</p>
        <p class="font-bold m-3">{machine.quantity}</p>
      </div>
      <div class="w-70 h-30 m-4 border rounded-lg border-gray-200 p-2">
        <p class="text-black-500 m-3 font-semibold">Avg Line Speed</p>
        <p class="font-bold m-3">{machine.avgSpeed}</p>
      </div>
      <div class="w-70 h-30 m-4 border rounded-lg border-gray-200 p-2">
        <p class="text-black-500 flex flex-1 gap-35 m-3 font-semibold">Operator 
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6">
            <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 6a3.75 3.75 0 1 1-7.5 0 3.75 3.75 0 0 1 7.5 0ZM4.501 20.118a7.5 7.5 0 0 1 14.998 0A17.933 17.933 0 0 1 12 21.75c-2.676 0-5.216-.584-7.499-1.632Z" />
          </svg>
        </p>
        <p class="font-bold m-3">{machine.operator}</p>
      </div>
      <div class="w-70 h-30 m-4 border rounded-lg border-gray-200 p-2">
        <p class="text-black-500 m-3 font-semibold">Job Running</p>
        <p class="font-bold m-3">{machine.job}</p>
      </div>
      <div class="w-70 h-30 m-4 border rounded-lg border-gray-200 p-2">
        <p class="text-black-500 m-3  font-semibold">Uptime</p>
        <p class="font-bold m-3">{machine.uptime}</p>
      </div>
      <div class="w-70 h-30 m-4 border rounded-lg border-gray-200 p-2">
        <p class="text-black-500 m-3 font-semibold">Downtime</p>
        <p class="font-bold m-3">{machine.downtime}</p>
      </div>
      <div class="w-70 h-30 m-4 border rounded-lg border-gray-200 p-2">
        <p class="text-black-500 m-3 flex flex-1 gap-25 font-semibold">Active Runtime
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" 
			stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-activity-icon lucide-activity stroke-gray-500">
			<path d="M22 12h-2.48a2 2 0 0 0-1.93 1.46l-2.35 8.36a.25.25 0 0 1-.48 0L9.24 2.18a.25.25 0 0 0-.48 0l-2.35 8.36A2 2 0 0 1 4.49 12H2"/>
			</svg>
        </p>
        <p class="font-bold m-3">{machine.activeRuntime}</p>
      </div>
      <div class="w-70 h-30 m-4 border rounded-lg border-gray-200 p-2">
        <p class="text-black-500 m-3 font-semibold">Energy Consumed</p>
        <p class="font-bold m-3">{machine.energy}</p>
      </div>
      <div class="w-70 h-30 m-4 border rounded-lg border-gray-200 p-2">
        <p class="text-black-500 m-3 font-semibold">OEE</p>
        <p class="font-bold m-3">{machine.oee}</p>
      </div>
    </div>
  
    <!-- Chart -->
    <div class="bg-white p-6 rounded-xl shadow">
      <h2 class="text-lg font-bold mb-4 m-3">Downtime Report for {machine.name}</h2>
      <!-- Later: Replace with Chart.js -->
      <ul>
        {#each chartData as item}
          <li class="flex items-center mb-2">
            <span class="w-4 h-4 mr-2 rounded" style="background-color: {item.color};"></span>
            {item.label}: {item.value}
          </li>
        {/each}
      </ul>
    </div>
  </div>
  