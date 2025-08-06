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
</script>

<nav>
	<div class="logo-wrap">
		<img src="https://keccables.ifactory.ai/assets/images/solidRsLogo.png" alt="Company logo" class="logo" />
		<span class="company-name">iFactory</span>
	</div>

	<div class="navtabs">
		<div class="nav-item">Dashboard</div>
		<div class="nav-item">Machines</div>
		<div class="nav-item">Production</div>
		<div class="nav-item">Tickets</div>
		<div class="nav-item">Jobs</div>
		<div class="nav-item">Operators</div>
		<div class="nav-item">CBM</div>
		<div class="nav-item">Energy</div>
	</div>
</nav>

<div class="dash">
	<h4>Factory Dashboard</h4>
</div>
<div class="square">
    <div class="stats-cards">
        <div class="stat">
            <strong>Total Production</strong>
            <p>379 m<br />+ 7.54 t</p>
        </div>
        <div class="stat">
            <strong>No. of Breakdowns</strong>
            <p>16 <span style="color: green">↑ 15.8%</span></p>
        </div>
        <div class="stat">
            <strong>Active Runtime</strong>
            <p style="color: red">24%</p>
        </div>
        <div class="stat">
            <strong>Jobs Completed</strong>
            <p style="color: red">1</p>
        </div>
    </div>
    <div class="grid-container">
        {#each topMachines as machine} 
            <div class="machine-card" style="background-color: {getStatusColor(machine.status)}">
                <div class="title"><strong>{machine.name}</strong></div>
                <div class="status-tag">{machine.status}</div>
                <div class="production-info"><p>Total Production</p><h2>{machine.production}</h2></div>
                <div class="oee"><p>OEE</p><h3>{machine.oee}</h3></div>
            </div>
        {/each}
    </div>
    
    
    {#if bottomMachines.length}
        <h4 style="margin-left: 1rem;">Other Machines</h4>
        <div class="grid-container">
            {#each bottomMachines as machine} 
                <div class="machine-card" style="background-color: {getStatusColor(machine.status)}">
                    <div class="title"><strong>{machine.name}</strong></div>
                    <div class="status-tag">{machine.status}</div>
                    <div class="production-info"><p>Total Production</p><h2>{machine.production}</h2></div>
                    <div class="oee"><p>OEE</p><h3>{machine.oee}</h3></div>
                </div>
            {/each}
        </div>
    {/if}
    
    </div>
    


<p>This page is shown only after a protected login</p>
<a href="/login">Logout</a>

<style>
	nav {
		display: flex;
		justify-content: space-between;
		align-items: center;
		background-color: white;
		border-bottom: 1px solid #ddd;
		padding: 0.5rem 1rem;
	}

	.logo {
		width: 50px;
		height: 50px;
	}

	.logo-wrap {
		display: flex;
		align-items: center;
		gap: 0.5rem;
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

	.dash {
		margin: 1.5rem 1rem 0;
		font-size: 1.5rem;
		font-weight: bold;
		color: black;
		font-family: sans-serif;
	}

	.stats-cards {
		display: flex;
		gap: 1rem;
		margin: 1rem;
		
		padding: 1rem;
		flex-wrap: wrap;
	}

	.stat {
		flex: 1;
		border: 1px solid #eee;
		padding: 1rem;
		border-radius: 8px;
		min-width: 200px;
		height: 5rem;
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
	}

	.machine-card:hover {
		transform: scale(1.02);
	}

	.status-tag {
		margin-top: 0.5rem;
		font-weight: bold;
		color: #ff4d4f;
	}

	.production-info,
	.oee {
		margin-top: 1rem;
	}

	.production-info h2,
	.oee h3 {
		color: black;
	}
    .square{
        border: 2px solid rgb(240, 110, 63);
    }
</style>
