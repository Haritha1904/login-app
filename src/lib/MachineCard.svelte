<script>
  export let name = '';
  export let status = 'OFFLINE';
  export let production = '0';
  export let oee = '0%';

  const oeeNum = Number(String(oee).replace('%', '')) || 0;
  const oeeAngle = Math.round(oeeNum * 3.6);

  $: bg = status === 'ACTIVE' ? 'bg-green-50'
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
    <h3 class="m-0 text-sm font-bold text-gray-900 leading-tight">{name}</h3>
  </div>

  <!-- Status Strip -->
  <div class={`h-2 rounded-lg relative my-2 ${strip}`}>
    <span class={`absolute -top-3 left-2 px-2 py-0.5 rounded-xl text-white font-bold text-[0.6rem] tracking-wide shadow ${pillBg}`}>
      {status}
    </span>
  </div>

  <!-- Body -->
  <div class="flex justify-between items-center gap-2">
    <div class="flex flex-col items-start">
      <!-- Label + Value -->
      <div class="text-[0.75rem] text-gray-500 mb-0.5">Total Production</div>
      <div class="text-4xl font-extrabold text-gray-900">{production}</div>

      <!-- OEE Donut -->
      <div class="flex items-center justify-center mt-2">
        <div class="relative w-12 h-12">
          <div class="absolute inset-0 rounded-full"
               style="background: conic-gradient(#ff6b6b {oeeAngle}deg, #e5e7eb 0deg)">
          </div>
          <div class="absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 
                      w-6 h-6 rounded-full bg-white flex flex-col items-center justify-center 
                      text-[8px] shadow">
            <div class="flex flex-col items-center">
              <div class="text-[10px] font-bold text-gray-900">OEE</div>
              <div class="text-[0.65rem] text-red-500 mt-0.5">{oeeNum}%</div>
            </div>        
          </div>
        </div>
      </div>   
    </div>
  </div>
</article>
