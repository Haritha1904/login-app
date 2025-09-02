<script>
    export let machines = [
        { name: 'RBD Machine1 - Take up 1', job: 'AL59 Zebra', status: 'Stopped', uptime: 113, downtime: 170, operator: 'Akhilesh', production: '2694.00m', oee: '22.65%' },
        { name: 'RBD Machine2 - Take up 2', job: 'AL60 Zebra', status: 'Production', uptime: 320, downtime: 45, operator: 'Ramesh', production: '5120.00m', oee: '85.40%' },
        { name: 'RST Machine - 1', job: 'BL20 Omega', status: 'Coil Change', uptime: 50, downtime: 120, operator: 'Suresh', production: '700.00m', oee: '10.25%' },
        { name: 'RST Machine - 2', job: 'BL21 Omega', status: 'HouseKeeping', uptime: 80, downtime: 60, operator: 'Manoj', production: '1200.00m', oee: '25.50%' },
        { name: 'RBD Machine3 - Take up 3', job: 'AL61 Zebra', status: 'Production', uptime: 400, downtime: 30, operator: 'Akhilesh', production: '6780.00m', oee: '92.10%' },
        { name: 'RST Machine - 3', job: 'BL22 Omega', status: 'Mechanical Breakdown', uptime: 20, downtime: 200, operator: 'Ramesh', production: '150.00m', oee: '5.00%' },
        { name: 'RBD Machine4 - Take up 4', job: 'AL62 Zebra', status: 'Production', uptime: 360, downtime: 25, operator: 'Suresh', production: '5900.00m', oee: '88.00%' },
        { name: 'RBD Machine5 - Take up 5', job: 'AL63 Zebra', status: 'Stopped', uptime: 90, downtime: 100, operator: 'Manoj', production: '2100.00m', oee: '30.00%' }
    ];

// Optional: status badge colors
    const statusColors = {
    Production: 'bg-green-400 text-white',
    Stopped: 'bg-red-500 text-white',
    'Coil Change': 'bg-orange-400 text-white',
    HouseKeeping: 'bg-orange-400 text-white',
    Offline: 'bg-gray-300 text-white',
    'Mechanical Breakdown': 'bg-orange-400 text-white'
    };
</script>

<h1 class="font-sans m-4 text-3xl">Machines Dashboard</h1>
<div class=" flex flex-1">

    <div class="flex w-60 m-4 border rounded-lg border-gray-300 p-2">
        <div class="   w-30 h-19 m-4">
        <h2 class=" text-xl w-300 font-bold ">Total Production</h2>
        <h4 class=" text-sans text-4xl font-bold text-orange-500">8</h4>
        </div>
    </div>
    
    <div class="flex w-60 m-4 border rounded-lg border-gray-300 p-2">
        <div class="   w-30 h-19 m-4">
            <h2 class=" text-xl w-300 font-bold ">Active Machines</h2>
            <h4 class=" text-sans text-4xl font-bold text-orange-500">7</h4>
        </div>
    </div>
    
    <div class="flex w-60 m-4 border rounded-lg border-gray-300 p-2">
        <div class="   w-30 h-19 m-4">
            <h2 class=" text-xl w-300 font-bold ">InActive Machines</h2>
            <h4 class=" text-sans text-4xl font-bold text-orange-500">1</h4>
        </div>
    </div>
</div>


<div class=" p-2 border rounded-lg bg-gray-100">
    <div class="flex items-center justify-between m-4">
        <div class="relative w-80">
          <input
            type="text"
            placeholder="Search machines..."
            class="w-full pl-10 pr-4 py-2 rounded-lg border border-gray-300 focus:outline-none focus:ring-2 focus:ring-orange-400 focus:border-orange-400 text-gray-700"
          />
          <svg
            class="w-5 h-5 text-gray-400 absolute left-3 top-1/2 transform -translate-y-1/2"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-4.35-4.35M17 11a6 6 0 11-12 0 6 6 0 0112 0z"></path>
          </svg>
        </div>
        
        <div class="flex w-30 m-4 border rounded-lg border-gray-300 p-3 gap-3">
            <h1>Columns</h1>
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5">
                <path stroke-linecap="round" stroke-linejoin="round" d="m19.5 8.25-7.5 7.5-7.5-7.5" />
            </svg>
    
        </div>
      </div>
        
        <div class="overflow-x-auto bg-white-200 rounded-lg">
            <table class="min-w-full divide-y divide-gray-200">
              <thead class="bg-gray-50">
                <tr>
                  <th class="px-4 py-4text-left text-xs font-medium text-gray-500 uppercase">#</th>
                  <th class="px-4 py-4 text-left text-xs font-medium text-gray-500 uppercase">Machine Name</th>
                  <th class="px-4 py-4 text-left text-xs font-medium text-gray-500 uppercase">Job</th>
                  <th class="px-4 py-4 text-left text-xs font-medium text-gray-500 uppercase">Status</th>
                  <th class="px-4 py-4 text-left text-xs font-medium text-gray-500 uppercase">Uptime</th>
                  <th class="px-4 py-4 text-left text-xs font-medium text-gray-500 uppercase">Downtime</th>
                  <th class="px-4 py-4 text-left text-xs font-medium text-gray-500 uppercase">Operator</th>
                  <th class="px-4 py-4 text-left text-xs font-medium text-gray-500 uppercase">Production Qty</th>
                  <th class="px-4 py-4 text-left text-xs font-medium text-gray-500 uppercase">OEE</th>
                </tr>
              </thead>
              <tbody class="divide-y divide-gray-200">


                {#each machines as machine, i}
                  <tr class="hover:bg-gray-50">
                    <td class="px-4 py-2 text-sm text-black-700 font-semibold">{i + 1}</td>
                    <td class="px-4 py-4 text-sm text-black-800 font-semibold">{machine.name}</td>
                    <td class="px-4 py-4 text-sm text-black-700 font-semibold">{machine.job || 'N/A'}</td>
                    <td class="px-4 py-2 ">
                      <span class={`px-2 inline-flex text-xs font-semibold rounded-full ${statusColors[machine.status] || 'bg-gray-100 text-gray-700'}`}>
                        {machine.status}
                      </span>
                    </td>
                    <td class="px-4 py-2 text-sm text-black-700 font-semibold">{machine.uptime || '⏳'}</td>
                    <td class="px-4 py-2 text-sm text-gray-700 font-semibold">{machine.downtime || '⏳'}</td>
                    <td class="px-4 py-2 text-sm text-gray-700 font-semibold">{machine.operator || 'N/A'}</td>
                    <td class="px-4 py-2 text-sm text-gray-700 font-semibold">{machine.production || '⏳'}</td>
                    <td class="px-4 py-2 text-sm text-gray-700 font-semibold">{machine.oee || '⏳'}</td>
                  </tr>
                {/each}

                
              </tbody>
            </table>
            </div>
</div>
    
