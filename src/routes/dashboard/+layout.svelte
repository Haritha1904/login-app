<script>
    // Dynamic date/time for dashboard
    let currentDateTime = new Date().toLocaleString();
    const interval = setInterval(() => {
      currentDateTime = new Date().toLocaleString();
    }, 1000);
  
    // Cleanup interval on destroy
    import { onDestroy } from 'svelte';
    onDestroy(() => clearInterval(interval));
  </script>
  
  <!-- NAVBAR -->
  <nav class="fixed top-0 left-0 w-full 
  bg-white border-b border-gray-200 px-4 py-2 flex justify-between items-center z-50">
    <div class="flex items-center gap-0">
      <img src="https://keccables.ifactory.ai/assets/images/solidRsLogo.png" alt="Company logo" class="logo" />
      <h2 class="text-xl md:text-2xl font-bold font-[Manrope] ml-2">iFactory</h2>
  <!-- NAVTABS -->
      <div class="hidden md:flex gap-6 pl-8 text-gray-600">
        <a href="/dashboard" class="hover:text-black">Dashboard</a>
        <a href="/dashboard/machines" class="hover:text-black">Machines</a>
        <a href="/dashboard/production" class="hover:text-black">Production</a>
        <a href="/dashboard/tickets" class="hover:text-black">Tickets</a>
  
        <button class="flex items-center space-x-1">
          <span>Jobs</span>
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5">
            <path stroke-linecap="round" stroke-linejoin="round" d="m19.5 8.25-7.5 7.5-7.5-7.5" />
          </svg>
        </button>
  
        <div class="hover:text-black cursor-pointer">Operators</div>
        <div class="hover:text-black cursor-pointer">CBM</div>
        <div class="hover:text-black cursor-pointer">Energy</div>
      </div>
    </div>
  
    <!-- USER ICON -->
    <img src="https://cdn-icons-png.flaticon.com/512/1144/1144760.png" alt="Profile" class="w-6 h-6 rounded-full" />


    <!-- Mobile hamburger -->
      <button class="md:hidden">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7" />
        </svg>
      </button>


  </nav>
  
  <!-- DASHBOARD HEADER -->
  <div class="flex flex-col md:flex-row md:justify-between md:items-center mt-16 mb-2 px-4 gap-4">
    <h4 class="text-xl md:text-2xl font-semibold  m-2 mt-4 font-sans">Factory Dashboard</h4>
  
    <div class="flex  flex-wrap gap-2 md:gap-4 items-center">
      <button class="flex items-center gap-2 border px-3 py-1 rounded border-gray-200">
        Shift
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5">
          <path stroke-linecap="round" stroke-linejoin="round" d="m19.5 8.25-7.5 7.5-7.5-7.5" />
        </svg>
      </button>
  
      <div class="flex items-center gap-2 border px-3 py-1 rounded border-gray-200">
        📅 {currentDateTime}
      </div>
  
      <button class="flex items-center bg-white text-black border px-3 py-1 rounded border-gray-200">
        Export
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5">
          <path stroke-linecap="round" stroke-linejoin="round"
            d="M19.5 14.25v-2.625a3.375 3.375 0 0 0-3.375-3.375h-1.5A1.125 1.125 0 0 1 13.5 7.125v-1.5a3.375 3.375 
               0 0 0-3.375-3.375H8.25m2.25 0H5.625c-.621 0-1.125.504-1.125 1.125v17.25c0 .621.504 1.125 1.125 1.125h12.75c.621 0 
               1.125-.504 1.125-1.125V11.25a9 9 0 0 0-9-9Z" />
        </svg>
      </button>
    </div>
  </div>
  <slot/>

  <!-- PAGE CONTENT SLOT -->
     
  <style>
    .logo {
      width: 50px;
      height: 50px;
      display: flex;
    }
  </style>
  