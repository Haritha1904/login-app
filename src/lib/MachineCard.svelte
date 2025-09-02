<script>
  export let name = '';
  export let status = 'OFFLINE';
  export let production = '0';
  export let oee = '0%';

  const oeeNum = Number(String(oee).replace('%', '')) || 0;
  const oeeAngle = Math.round(oeeNum * 3.6);

  $: bg = status === 'ACTIVE' ? 'bg-green-30'
       : status === 'BREAKDOWN' ? 'bg-red-50'
       : 'bg-gray-100';

  $: strip = status === 'ACTIVE' ? 'bg-green-400'
       : status === 'BREAKDOWN' ? 'bg-red-400'
       : 'bg-gray-400';

  $: pillBg = status === 'ACTIVE' ? 'bg-green-600'
       : status === 'BREAKDOWN' ? 'bg-red-500'
       : 'bg-gray-500';
</script>

<article class={`rounded-lg p-0 shadow-md min-h-[200px] flex flex-col justify-between border border-black/5 ${bg} w-5/5 font-spacegrotesk`}>
  <!-- Top -->
  <div class="mb-1">
    <h3 class="m-4  text-2xl font-bold text-gray-900 leading-tight">{name}</h3>
  </div>

  <!-- Status Strip -->
  <div class={`h-2 rounded-lg  m-4 relative my-8 ${strip}`}>
    <span class={`absolute -top-2 left-0 px-2 py-0.5 rounded-xl text-white font-bold text-[0.6rem] tracking-wide shadow ${pillBg}`}>
      {status}
    </span>
  </div>

  <!-- Body -->
  <div class="flex justify-between items-center gap-2 ">
    <div class="flex flex-col items-start">
      <!-- Label + Value -->
      <div class="text-[1rem] font-semibold m-5  text-gray-400 mb-0.5">Total Production</div>
      <div class="text-5xl font-bold m-4 text-gray-500 font-[Manrope]">{production}</div>

      <!-- OEE Donut -->
      <div class="flex items-center gap-2">
        <!-- OEE Circle -->
        <div class="relative w-13 h-13 m-4 mt-0">
          <!-- Progress Circle -->
          <div class="absolute inset-0 rounded-full"
            style="background: conic-gradient(#ef4444 {oeeAngle}deg, #e5e7eb 0deg)">
          </div>
      
          <!-- Inner White Circle -->
          <div class="absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 
                      w-7 h-7 rounded-full bg-white shadow flex items-center justify-center">
            <span class="text-[15px] font-bold text-gray-700">OEE</span>
          </div>
        </div>
      
        <!-- Percentage Text -->
        <div class="text-2xl font-bold text-red-500 mb-5">
          {oeeNum}%
        </div>
      </div>
      


      <!-- <div class="flex items-center justify-center m-4 ">
        <div class="relative w-16 h-16">
          <div class="absolute inset-0 rounded-full  "
               style="background: conic-gradient(#ef4444 {oeeAngle}deg, #e5e7eb 0deg)">
          </div>
          <div class="absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 
                      w-11 h-11 rounded-full bg-white  flex flex-col items-center justify-center 
                      shadow">
            <div class="flex flex-col items-center ">
              <div class="text-[18px] font-bold text-gray-900 mt-4">OEE</div>
              <div class="text-sm font-bold text-red-500">{oeeNum}%</div>
            </div>        
          </div>
        </div>
      </div>    -->


    </div>
  </div>
</article>
