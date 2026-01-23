---
layout: default
title: CFD Projects
permalink: /analysis/cfd/
published: false
---

<div class="container">
  <h1>Computational Fluid Dynamics (CFD)</h1>
  <p>Aerodynamics and fluid flow simulations.</p>
  <hr>

  <div class="d-flex flex-column gap-3">
    <a href="{{ '/analysis/WindTurbineCFD/' | relative_url }}" 
       class="list-group-item list-group-item-action d-flex align-items-center gap-3 p-3 rounded-3 ghost-card">
      <img 
      src="{{ '/assets/images/WindTurbineBladeCFD.jpg' | relative_url }}" 
      alt="Turbine" 
      width="100" 
      height="100" 
      class="rounded-circle flex-shrink-0"
      style="object-fit: cover;">
      <div class="d-flex gap-2 w-100 justify-content-between">
        <div>
          <h5 class="mb-0">Wind Turbine Aerodynamics</h5>
          <p class="mb-0 opacity-75">k-omega SST turbulence modeling and lift/drag optimization.</p>
        </div>
      </div>
    </a>
  </div>

  <br>
  <a href="{{ "/analysis/" | relative_url }}" class="back-arrow">
    <i class="bi bi-arrow-left-circle-fill"></i> Back to Simulations
  </a>
</div>