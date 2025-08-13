<script>
  export let name = '';
  export let status = 'OFFLINE';
  export let production = '0';
  export let oee = '0%';

  const oeeNum = Number(String(oee).replace('%', '')) || 0;
  const oeeAngle = Math.round(oeeNum * 3.6);

  $: bg = status === 'ACTIVE' ? '#eaf9ee' 
       : status === 'BREAKDOWN' ? '#fff6f6' 
       : '#f4f5f6';

  $: strip = status === 'ACTIVE' ? '#34d399' 
       : status === 'BREAKDOWN' ? '#ffb1b1' 
       : '#d1d6da';

  $: pillBg = status === 'ACTIVE' ? '#10b981' 
       : status === 'BREAKDOWN' ? '#ff6b6b' 
       : '#8f9599';
</script>

<article class="card" style="background: {bg}">
  <div class="card-top">
    <h3 class="name">{name}</h3>
  </div>

  <div class="status-strip" style="background: {strip}">
    <span class="status-pill" style="background: {pillBg}">{status}</span>
  </div>

  <div class="card-body">
    <div class="prod-block">
      <div class="prod-label">Total Production</div>
      <div class="prod-value">{production}</div>
      <br>

      <div class="oee-block">
        <div class="donut" style="--angle: {oeeAngle}deg">
          <div class="donut-ring"></div>
          <div class="donut-center">
            <div class="oee-label">OEE</div>
          </div>
        </div>
      </div>
      <br>
      <div class="oee-percent"><h2>{oeeNum}%</h2></div>
    </div>
    </div>

   
</article>

<style>
  .card{
    border-radius: 10px;
    padding: 14px;
    box-shadow: 0 6px 18px rgba(0,0,0,0.04);
    min-height: 180px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    border: 1px solid rgba(0,0,0,0.03);
  }

  .card-top {
    margin-bottom: 6px; 
  }
  .name {
    margin: 0;
    font-size: 1rem;
    font-weight: 700;
    color: #111827;
    line-height: 1.1;
  }

  .status-strip{
    height: 8px;
    border-radius: 8px;
    position: relative;
    margin: 10px 0 14px 0;
  }

  .status-pill{
    position: absolute;
    top: -12px;
    left: 12px;
    padding: 4px 8px;
    border-radius: 12px;
    color: white;
    font-weight: 700;
    font-size: 0.65rem;
    letter-spacing: 0.6px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.06);
    text-transform: uppercase;
  }

  .card-body{
    display:flex;
    justify-content: space-between;
    align-items: center;
    gap: 12px;
  }

  .prod-block{
    display:flex;
    flex-direction: column;
  }

  .prod-label{
    font-size: 0.78rem;
    color: #6b7280;
    margin-bottom: 6px;
  }

  .prod-value{
    font-size: 1.5rem;
    font-weight: 800;
    color: #111827;
  }

  .oee-block {
    display:flex;
    align-items:center;
    justify-content:center;
  }

  .donut{
    width: 64px;
    height: 64px;
    position: relative;
  }

  .donut-ring{
    position:absolute;
    inset: 0;
    border-radius: 50%;
    background: conic-gradient(#ff6b6b var(--angle, 0deg), #e9e9e9 0deg);
    display:block;
  }

  .donut-center{
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 36px;
    height: 36px;
    border-radius: 50%;
    background: white;
    display:flex;
    flex-direction: column;
    align-items:center;
    justify-content:center;
    font-size: 10px;
    box-shadow: 0 2px 6px rgba(0,0,0,0.05);
  }

  .oee-label{
    font-size: 9px;
    color: #0a0a0a;
    font-weight: bold;
  }

  .oee-percent{
    font-weight: 700;
    color: #ff5a5a;
    font-size: 11px;
    line-height: 1;
  }
</style>
