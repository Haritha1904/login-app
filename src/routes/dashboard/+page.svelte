<script>
	import MachineCard from '$lib/MachineCard.svelte';
  
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
  
	let currentDateTime = new Date().toLocaleString();
	setInterval(() => {
	  currentDateTime = new Date().toLocaleString();
	}, 1000);
  </script>  
	
  <h1 class= "mt-6 text-red-900" >ghdhsdfzfvbdz</h1>
  <nav>
	<div class="nav-left">
	  	<div class="logo-wrap">
		<img src="https://keccables.ifactory.ai/assets/images/solidRsLogo.png" alt="Company logo" class="logo" />
		</div>
		<div class="tit">
			<h2> ifactory</h2>	
		</div>
	  <div class="navtabs">
		<div class="nav-item">Dashboard</div>
		<div class="nav-item">Machines</div>
		<div class="nav-item">Production</div>
		<div class="nav-item">Tickets</div>
		<div class="nav-item dropdown-tab">Jobs <span class="dropdown-arrow">▼</span></div>
		<div class="nav-item">Operators</div>
		<div class="nav-item">CBM</div>
		<div class="nav-item">Energy</div>
	  </div>
	</div>
	<div class="nav-right">
	  <img src="https://cdn-icons-png.flaticon.com/512/1144/1144760.png" alt="Profile" class="profile-icon" />
	</div>
  </nav>
  
  <div class="com-dash">
	<div class="dash-left">
	  <div class="dash"><h4>Factory Dashboard</h4></div>
	</div>
	<div class="top-controls">
	  <div class="control shift">
		<div class="dropdown">
			<span>Shift </span>
			<span class="arrow">▼</span><br>
		</div>
	</div>
	  <div class="control-datetime">
		<div class="datetime-display">
			<span class="calendar-icon">📅</span>
			<span>{currentDateTime}</span><br><br>
		</div>
	</div>
	  <div class="control export">
		<div class="export-button">
			<span class="export-icon">⬇️ Export</span>
		</div>
	</div>
	</div>
  </div>
  
  <div class="stats-cards">
	<div class="stat"><strong>Total Production</strong><h3>379 m<br>+ <br> 7.54 t</h3><span style="color: red">↑99.8%</span>  from last 2 hours 30 mins</div>
	<div class="stat"><strong>No. of Breakdowns</strong><h2>16</h2><span style="color: red">↑12%</span>  from last 2 hours 30 mins</div>
	<div class="stat"><strong>Active Runtime</strong><h2>24%</h2><span style="color: red">↑34.8%</span>  from last 2 hours 30 mins</div>
	<div class="stat"><strong>Jobs Completed</strong><h2>1</h2><span style="color: red">↑9.8%</span>  from last 2 hours 30 mins</div>
  </div>
  
  <div class="machine-grid">
	{#each machines as machine}
	  <MachineCard {...machine} />
	{/each}
  </div>
  
  <a href="/login">Logout</a>
  
  <style lang="postcss">
	/* @import "tailwindcss"; */
	@reference "tailwindcss";
	nav {
	  background-color: white;
	  border-bottom: 1px solid #ddd;
	  padding: 0.5rem 1rem;
	  display: flex;
	  justify-content: space-between;
	  align-items: center;
	}
	.nav-left { display: flex; align-items: center; gap: 0rem; }
	.logo { width: 50px; height: 50px; display:flex }
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
  
	.machine-grid {
	  display: grid;
	  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
	  gap: 18px;
	  padding: 16px;
	  align-items: start;
	}
  </style>
  