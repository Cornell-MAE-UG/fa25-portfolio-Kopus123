---
layout: project
title: Wind Turbine FEA
permalink: /analysis/WindTurbineFEA/
description: "Structural analysis of turbine blade loads."
technologies: [ANSYS Mechanical]
---

<div style="clear: both;"></div>

<div style="position: relative; top: -50px; margin-bottom: -25px;">
  <strong>Objective:</strong> To validate the structural integrity the wind turbine using the results obtained from the <a href="{{ '/analysis/WindTurbineCFD/' | relative_url }}">wind turbine CFD analysis</a>
</div>

### 1. Engineering Data
**Materials:** A custom named material (named homogenous orthotropic; custom inputted youngs modulus and shear modulus) that represents the real material for a wind turbine blade.

<hr>

### 2. Geometry
The geometry is the wind turbine blade itself, and does not contain the fluid that surrounds the blade like the CFD analysis did.

<div style="text-align: center; margin: 25px 0;">
<img src="{{ '/assets/images/BladeGeom.jpg' | relative_url }}" 
     style="width: 65%; max-width: 500px; border-radius: 6px; border: 1px solid #ddd; box-shadow: 0 2px 10px rgba(0,0,0,0.05);">
<p style="margin-top: 8px; font-size: 0.85rem; opacity: 0.8;">
    <i></i>
</p>
</div>

<hr>

### 3. Model & Mesh
This mesh, due to the shape of the blade, was able to be made much more uniform with the majority of the elements conforming to a skewness of less than 10%. In order to obtain such a uniform mesh, a face meshing was utilized on the blade surface, as well as a custom mesh size of .2 m.
<div style="text-align: center; margin: 25px 0;">
<img src="{{ '/assets/images/BladeMesh.jpg' | relative_url }}" 
     style="width: 65%; max-width: 500px; border-radius: 6px; border: 1px solid #ddd; box-shadow: 0 2px 10px rgba(0,0,0,0.05);">
<p style="margin-top: 8px; font-size: 0.85rem; opacity: 0.8;">
    <i></i>
</p>
</div>

<hr>

### 4. Results
I uses ANSYS to solve the mathematical model to find the deformation and stress in the wind turbine as a result of the pressures and forces as a result of the fluid the blade encounters. I found that the deformation was in the proper direction, so the FEA served as a confirmation that my CFD analysis was correct. Below, the results for the deformation and the Von-Mises Stress are shown. As illustrated, the maximum deformation occurs at the end of the blade (~.4 m) and the highest area of stress occurs at roughly 1/4 and 3/4 of the length of the blade.
<div class="row mt-4">

  <div class="col-md-6 mb-3">
    <img 
      src="{{ '/assets/images/WTDef.jpg' | relative_url }}" 
      class="img-fluid border rounded" 
      style="aspect-ratio: 16/9; width: 100%; object-fit: cover; object-position: center;"
      alt="Inlets">
    <p class="text-muted small text-center mt-2"><i>Deformation</i></p>
  </div>

  <div class="col-md-6 mb-3">
    <img 
      src="{{ '/assets/images/WTDefProbe.jpg' | relative_url }}" 
      class="img-fluid border rounded" 
      style="aspect-ratio: 16/9; width: 100%; object-fit: cover; object-position: center;"
      alt="Walls">
    <p class="text-muted small text-center mt-2"><i>Deformation with probed values</i></p>
  </div>

<div class="row mt-4">
</div>
  <div class="col-md-6 mb-3">
    <img 
      src="{{ '/assets/images/WTStress.jpg' | relative_url }}" 
      class="img-fluid border rounded" 
      style="aspect-ratio: 16/9; width: 100%; object-fit: cover; object-position: center;"
      alt="Inlets">
    <p class="text-muted small text-center mt-2"><i>Von-Mises stress</i></p>
  </div>

  <div class="col-md-6 mb-3">
    <img 
      src="{{ '/assets/images/WTStressProbe.jpg' | relative_url }}" 
      class="img-fluid border rounded" 
      style="aspect-ratio: 16/9; width: 100%; object-fit: cover; object-position: center;"
      alt="Walls">
    <p class="text-muted small text-center mt-2"><i>Von-Mises Stress with probed values</i></p>
  </div>




{% comment %}
image stuff below
{% endcomment %}
<div id="imageModal" class="modal">
  <span class="close-btn">&times;</span>
  <img class="modal-content" id="modalImg" onclick="event.stopPropagation()">
  <div id="caption"></div>
</div>

<hr>

