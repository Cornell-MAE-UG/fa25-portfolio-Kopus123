---
layout: default
title: Simulations
permalink: /analysis/
---

<div class="container text-center">
  <h1 class="display-4 fw-bold mb-3">Technical Simulations</h1>
  <p class="lead mb-5 text-secondary">Select a domain to view analyses</p>

  <div class="row justify-content-center">
    <div class="col-md-5 mb-5">
      <a href="{{ '/analysis/fea/' | relative_url }}" class="text-decoration-none text-dark">
        <div class="simulation-card p-3">
          <img 
          src="{{ '/assets/images/SimplifiedRocketNozzle.jpg'| relative_url }}" 
          class="img-fluid mb-4" 
          alt="FEA"
          style="object-fit: cover; object-position: 52% center;">
          <h2 class="fw-bold">FEA & Structural</h2>
          <p class="text-muted">Finite Element Analysis using ANSYS Mechanical.</p>
          <span class="arrow-link">View Projects <i class="bi bi-arrow-right"></i></span>
        </div>
      </a>
    </div>
    {% comment %}
    <div class="col-md-5 mb-5">
      <a href="{{ '/analysis/cfd/' | relative_url }}" class="text-decoration-none text-dark">
        <div class="simulation-card p-3">
          <img 
          src="{{ '/assets/images/WindTurbineBladeCFD.jpg'| relative_url }}" 
          class="img-fluid mb-4" 
          alt="CFD"
          style="object-fit: cover; object-position: 60% center;">
          <h2 class="fw-bold">CFD & Fluids</h2>
          <p class="text-muted">Fluid dynamics and flow verification using Fluent.</p>
          <span class="arrow-link">View Projects <i class="bi bi-arrow-right"></i></span>
        </div>
      </a>
    </div>
    {% endcomment %}
  </div>
</div>