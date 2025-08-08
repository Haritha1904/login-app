<script>
    export let name;
    export let status;
    export let production;
    export let oee;
  
    // Map status to icon + color
    const statusMap = {
      ACTIVE: {
        color: "#4CAF50", // green
        icon: "✔️" // You can replace with an actual SVG if needed
      },
      BREAKDOWN: {
        color: "#F44336", // red
        icon: "⚠️"
      },
      OFFLINE: {
        color: "#9E9E9E", // gray
        icon: "⏸️"
      }
    };
  </script>
  
  <div class="machine-card" style="border-left: 6px solid {statusMap[status].color}">
    <div class="status-icon" style="color: {statusMap[status].color}">
      {statusMap[status].icon}
    </div>
    <div class="machine-info">
      <h3>{name}</h3>
      <p class="status" style="color: {statusMap[status].color}">{status}</p>
      <p>Production: <strong>{production}</strong></p>
      <p>OEE: <strong>{oee}</strong></p>
    </div>
  </div>
  
  <style>
    .machine-card {
      display: flex;
      align-items: center;
      background: white;
      border-radius: 10px;
      padding: 12px 16px;
      margin: 8px 0;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
      transition: transform 0.2s ease;
    }
  
    .machine-card:hover {
      transform: translateY(-3px);
    }
  
    .status-icon {
      font-size: 1.8rem;
      margin-right: 12px;
    }
  
    .machine-info {
      display: flex;
      flex-direction: column;
    }
  
    .machine-info h3 {
      margin: 0;
      font-size: 1rem;
      font-weight: 600;
    }
  
    .status {
      font-weight: bold;
      margin: 2px 0;
    }
  
    p {
      margin: 2px 0;
      font-size: 0.9rem;
    }
  </style>
  