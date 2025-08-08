<script>
	let machines = [
		{ name: 'RBD Machine1 - Take up 1', status: 'ACTIVE', production: '1.52 t', oee: '29.65%' },
		{ name: 'RST Machine - 1', status: 'BREAKDOWN', production: '377 m', oee: '1.73%' },
		{ name: 'RST Machine - 2', status: 'BREAKDOWN', production: '2 m', oee: '0%' },
		{ name: 'RBD Machine2-Take up 1', status: 'BREAKDOWN', production: '0.46 T', oee: '4.17%' },
		{ name: 'CCR Machine', status: 'BREAKDOWN', production: '4981.9 kg', oee: '21.35%' },
		{ name: 'RBD Machine2-Take up 2', status: 'BREAKDOWN', production: '0 t', oee: '0%' },
		{ name: 'RBD Machine2-Take up 1', status: 'BREAKDOWN', production: '0.58 T', oee: '6.86%' },
		{ name: 'Coiler', status: 'OFFLINE', production: '0 kg', oee: '0%' }
	];

    let topMachines = machines.slice(0, 5);
    let bottomMachines = machines.slice(5);

	function getStatusColor(status) {
		if (status === 'ACTIVE') return '#b2f2bb';
		if (status === 'BREAKDOWN') return '#ffe3e3';
		if (status === 'OFFLINE') return '#f1f3f5';
		return 'white';
	}

	let currentDateTime = new Date().toLocaleString();
	setInterval(() => {
  	currentDateTime = new Date().toLocaleString();
	}, 1000);

	let productionByMachines =
	[
		{
			name: 'RBD Machine1 - Take up 1',
			breakdowns: 5,
			jobsCompleted: 0,
			activeRuntime: '50.6%',
			production: '1.52 t'
		},
		{
			name: 'RST Machine - 1',
			breakdowns: 3,
			jobsCompleted: 0,
			activeRuntime: '12.7%',
			production: '377 m'
		},
		{
			name: 'RST Machine - 2',
			breakdowns: 1,
			jobsCompleted: 0,
			activeRuntime: '1.2%',
			production: '2 m'
		},
		{
			name: 'RBD Machine2 - Take up 1',
			breakdowns: 3,
			jobsCompleted: 0,
			activeRuntime: '23.5%',
			production: '0.46 t'
		}

	];


  // Chart appearance & behavior
  let chartOptions = {
    responsive: true,
    plugins: {
      legend: {
        position: 'top'
      },
      title: {
        display: true,
        text: 'Production Overview'
      }
    }
  };
</script>

<nav>
	<div class="nav-left">
		<div class="logo-wrap">
			<img src="https://keccables.ifactory.ai/assets/images/solidRsLogo.png" alt="Company logo" class="logo" />
			<span class="company-name">iFactory</span>
		</div>

		<div class="navtabs">
			<div class="nav-item">Dashboard</div>
			<div class="nav-item">Machines</div>
			<div class="nav-item">Production</div>
			<div class="nav-item">Tickets</div>
			<div class="nav-item dropdown-tab">
				Jobs
				<span class="dropdown-arrow">▼</span>
			</div>
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
		<div class="dash">
			<h4>Factory Dashboard</h4>
		</div>
	</div>
	
	
	<div class="top-controls">
		<!-- Shift Dropdown -->
		<div class="control shift">
		  <!-- <label>Shift</label> -->
		  <div class="dropdown">
			<span>Shift </span>
			<span class="arrow">▼</span>
		  </div>
		</div>
	  
		<!-- Date & Time -->
		<div class="control-datetime">
		  <!-- <label>Date & Time</label> -->
		  <div class="datetime-display">
			<span class="calendar-icon">📅</span>
			<span>{currentDateTime}</span>
		  </div>
		</div>
	  
		<!-- Export -->
		<div class="control export">
		  <!-- <label>Export</label> -->
		  <div class="export-button">
			<span class="export-icon">⬇️ Export</span>
		  </div>
		</div>
	</div>
</div>

  

<div class="square">
    <div class="stats-cards">
        <div class="stat">
            <strong>Total Production</strong>
            <h3>379 m<br>+ <br> 7.54 t <br></h3>
			<span style="color: red">↑99.8%</span> <span style="font-size:small">from last 2 hours, 46 mins</span>
        </div>
        <div class="stat">
            <strong>No. of Breakdowns</strong>
            <strong><h2>16</h2></strong> <span style="color: green">↑ 15.8%</span> <span style="font-size:small">from last 2 hours, 46 mins</span>
        </div>
        <div class="stat">
            <strong>Active Runtime</strong>
            <span style="color: black"><h2>24%</h2></span><span style="color: red">↑ 60.1%</span> <span style="font-size:small"> from last 2 hours, 46 mins</span>
        </div>
        <div class="stat">
            <strong>Jobs Completed</strong>
            <span style="color: black"><br><h2>1</h2></span><span style="color: red">↑ 66.1%</span> <span style="font-size:small"> from last 2 hours, 46 mins</span>
        </div>
    </div>
    <div class="grid-container">
        {#each topMachines as machine} 
            <div class="machine-card" >
                <div class="title"><strong>{machine.name}</strong></div>
                <div class="status-tag {machine.status.toLowerCase()}" >{machine.status}</div>
                <div class="production-info"><p>Total Production</p><h1>{machine.production}</h1></div>
                <div class="oee"><p>OEE</p><h3>{machine.oee}</h3></div>
            </div>
        {/each}
    </div>
    
    
    {#if bottomMachines.length}
        <h4 style="margin-left: 1rem;">Other Machines</h4>
        <div class="grid-container">
            {#each bottomMachines as machine} 
                <div class="machine-card" >
                    <div class="title"><strong>{machine.name}</strong></div>
                    <div class="status-tag {machine.status.toLowerCase()}">{machine.status}</div>
                    <div class="production-info"><p>Total Production</p><h1>{machine.production}</h1></div>
                    <div class="oee"><p>OEE</p><h3>{machine.oee}</h3></div>
                </div>
            {/each}
        </div>
    {/if}

	<div class="prod-right">
		<div class="production-by-machines">
			<h4>Production By Machines</h4>
			{#each productionByMachines as machine}
			<div class="machine-entry">
				<div class="machine-info">
					<strong>{machine.name}</strong>
					<div class="details">
						Breakdowns: <span style="color: red">{machine.breakdowns}</span>, Jobs Completed : {machine.breakdowns},Active Runtime: <span style="color: red">{machine.activeRuntime}</span>
					</div>
				</div>
				<div class="machine-production">
					{machine.production}
				</div>
			</div>
			{/each}
		</div>
	</div>


</div>
    



<a href="/login">Logout</a>

<style>
	
	nav {
	background-color: white;
	border-bottom: 1px solid #ddd;
	padding: 0;
	}

	.nav-left {
	display: flex;
	align-items: center;
	gap: 2rem;
	margin-left: -1rem;
	margin-top: -1rem;
	}

	.nav-right{
		display: flex;
		padding-bottom: -5rem;
		justify-content:flex-end;
		align-items:center;
	}

	.profile-icon{
		width:25px;
		height:25px;
		border-radius: 20%;
		cursor: pointer;
		margin-top: -5rem;
		margin-bottom: -2rem;
		
	}

	.logo {
		width: 50px;
		height: 50px;
		padding: 0;
		margin: 0;
	}

	.logo-wrap {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		padding-left: 0rem;
	}

	.company-name {
		font-size: 1.5rem;
		font-weight: bold;
		font-family: sans-serif;
	}

	.navtabs {
		display: flex;
		gap: 20px;
		align-items: center;
	}

	.nav-item {
		color: grey;
		cursor: pointer;
		font-family: sans-serif;
	}
	.dropdown-tab {
	/* display: flex; */
	/* align-items: center; */
	/* gap: 4px; */
	/* position: relative; */
	cursor: pointer;
    }

	.dropdown-arrow {
	font-size: 0.7rem;
	margin-top: 2px;
	color: #555;
	}


	.dash {
		margin: 0rem ;
		margin-top: -1rem;
		margin-bottom: -1rem;
		font-size: 1.5rem;
		font-weight: bold;
		color: black;
		font-family: sans-serif;
	}

	.dash-left{
		display: flex;
		align-items: center;
		gap: 2rem;
		margin-left: 0rem;
		margin-top: 0rem;
	}

	.com-dash{
		justify-content: space-between;
		display:flex;
		align-items: center;
		gap: 30%;
	}

	.top-controls {
	max-width: 50%;
	display: flex;
	justify-content: space-around;
	align-items: center;
	background-color: #ffffff;
	padding: 10px 20px;
	gap: 5px;
	border-bottom: 1px solid #fff0f0;
    }

	.control {
		display: flex;
		flex-direction: column;
		font-size: 0.9rem;
		color: #333;
	}

	.control label {
		font-weight: 600;
		margin-bottom: px;
	}

	.dropdown, .datetime-display, .export-button {
		display: flex;
		align-items: center;
		gap: 20px;
		background: white;
		padding: 5px 10px;
		border: 1px solid #ccc;
		border-radius: 4px;
		cursor: pointer;
	}
	.control-datetime{
		justify-content: space-between;
		gap:6px;
	}

	.arrow, .calendar-icon, .export-icon {
		font-size: 0.8rem;
		color: #555;
	}
		
	.stats-cards {
		display: flex;
		gap: 1rem;
		margin: 1rem;
		padding: 0rem;
		flex-wrap: wrap;
		font-family: sans-serif;
	}

	.stat {
		flex: 1;
		border: 1px solid #faf3f3;
		padding: 1rem;
		border-radius: 10px;
		min-width: 250px;
		height: 8rem;
	}

	.grid-container {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
		gap: 1rem;
		margin: 2rem 1rem;
	}

	.machine-card {
		border: 1px solid #ddd;
		border-radius: 10px;
		padding: 1rem;
		transition: transform 0.3s;
		font-family: sans-serif;
	}

	.machine-card:hover {
		transform: scale(1.02);
	}

	.status-tag {
		margin-top: 0.5rem;
		font-weight: bold;
	}

	.status-tag.active {
	color: #28a745; 
	}
	.status-tag.active.oee{
	color: #28a745; 
	}

	.status-tag.breakdown {
		color: #dc3545; 
	}

	.status-tag.offline {
		color: #6c757d; 
	}


	.production-info,
	.oee {
		margin-top: 1rem;
	}

	.production-info,h2,
	.oee h3 {
		color: black;
	}
    .square{
        border: 2px solid rgb(240, 110, 63);
    }

	.production-by-machines {
		border: 1px solid #eee;
		padding: 1rem;
		border-radius: 10px;
		max-height: 300px;
		overflow-y: auto;
		font-family: sans-serif;
		background: white;
	}

	.production-by-machines h4 {
		margin-top: 0;
		margin-bottom: 1rem;
		font-weight: bold;
	}

	.machine-entry {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 0.5rem 0;
		border-bottom: 1px solid #ddd;
	}

	.machine-entry:last-child {
		border-bottom: none;
	}

	.machine-info {
		flex: 1;
	}

	.details {
		font-size: 0.85rem;
		color: gray;
	}

	.machine-production {
		font-weight: bold;
		white-space: nowrap;
		margin-left: 1rem;
	}
	.prod-right{
		justify-content: flex-end;
		display: flex;
		padding-bottom: -5rem;
		align-items:center;
	}
	.chart-container {
    width: 100%;
    max-width: 600px;
    margin: auto;
    background: white;
    padding: 1rem;
    border-radius: 0.5rem;
    box-shadow: 0px 2px 8px rgba(0,0,0,0.1);
  }
</style>
