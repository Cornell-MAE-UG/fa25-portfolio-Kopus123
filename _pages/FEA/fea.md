---
layout: default
title: FEA Projects
permalink: /analysis/fea/
---

<div class="container">
  <h1>Finite Element Analysis (FEA)</h1>
  <p>Structural and thermal analysis projects.</p>
  <hr>

  <div class="d-flex flex-column gap-3">
    <a href="{{ '/analysis/RocketNozzleFEA/' | relative_url }}" 
    class="list-group-item list-group-item-action d-flex align-items-center gap-3 p-3 rounded-3 ghost-card rounded-3">
      <img 
      src="{{ '/assets/images/SimplifiedRocketNozzle.jpg' | relative_url }}" 
      alt="Nozzle" 
      width="100" 
      height="100" 
      style="object-fit: cover; object-position: 55% center;" 
      class="rounded-circle flex-shrink-0">
      <div class="d-flex gap-2 w-100 justify-content-between">
        <div>
          <h5 class="mb-0">Rocket Nozzle Thermal-Structural Analysis</h5>
          <p class="mb-0 opacity-75">Coupled steady-state thermal and static structural validation.</p>
        </div>
      </div>
    </a>
    <a href="{{ '/analysis/WindTurbineFEA/' | relative_url }}" 
    class="list-group-item list-group-item-action d-flex align-items-center gap-3 p-3  rounded-3 ghost-card rounded-3">
      <img src="{{ '/assets/images/TurbineFEACover.jpg' | relative_url }}" alt="Turbine Struct" width="100" height="100" class="rounded-circle flex-shrink-0" style="object-fit: cover;">
      <div class="d-flex gap-2 w-100 justify-content-between">
        <div>
          <h5 class="mb-0">Wind Turbine FEA</h5>
          <p class="mb-0 opacity-75">Structural validation of the blade design.</p>
        </div>
      </div>
    </a>
    

  <br>
  <a href="{{ "/analysis/" | relative_url }}" class="back-arrow">
    <i class="bi bi-arrow-left-circle-fill"></i> Back to Simulations
  </a>
</div>