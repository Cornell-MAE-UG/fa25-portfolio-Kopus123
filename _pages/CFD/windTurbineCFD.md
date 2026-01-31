---
layout: project
title: Wind Turbine CFD
permalink: /analysis/WindTurbineCFD/
description: "Aerodynamic optimization of a wind turbine blade."
technologies: [Spaceclaim, ANSYS Mechanical, ANSYS Fluent, ANSYS CFD-Post]
---

**Objective:** Analyze how air interacts with the blade of a wind turbine, and how that interaction causes the wind turbine to rotate 

<hr>

### 1. Geometry
<div class="text-center mt-3 mb-5">
  <img 
    src="{{ '/assets/images/TurbineGeometry.jpg' | relative_url }}" 
    class="img-fluid border rounded" 
    style="max-height: 400px; width: auto; object-fit: contain;"
    alt="CFD Geometry">
</div>

The geometry isolates a single blade from the three-blade wind turbine to allow for FLUENT to solve the problem faster. The two trapezoidal faces that can be seen are the parts in which the model was split. The model itself contains mostly fluid space, with the small body that can be seen towards the middle right being the single wind turbine blade. Therefore, the whole model has a cone like shape with a flat front and rear end.

<hr>

### 2. Mesh
<div class="row mt-4">
  <div class="col-md-4 mb-3">
    <img 
      src="{{ '/assets/images/TurbineMesh.jpg' | relative_url }}" 
      class="img-fluid border rounded" 
      style="height: 250px; width: 100%; object-fit: cover;"
      alt="Global Mesh">
    <p class="text-muted small text-center mt-2"><i>Full Mesh</i></p>
  </div>

  <div class="col-md-4 mb-3">
    <img 
      src="{{ '/assets/images/TurbineMesh2.jpg' | relative_url }}" 
      class="img-fluid border rounded" 
      style="height: 250px; width: 100%; object-fit: cover;"
      alt="Inflation Layers">
    <p class="text-muted small text-center mt-2"><i>Side View with a Slice</i></p>
  </div>

  <div class="col-md-4 mb-3">
    <img 
      src="{{ '/assets/images/TurbineMesh3.jpg' | relative_url }}" 
      class="img-fluid border rounded" 
      style="height: 250px; width: 100%; object-fit: cover;"
      alt="Trailing Edge Refinement">
    <p class="text-muted small text-center mt-2"><i>Near-Blade Mesh</i></p>
  </div>
</div>

The mesh was made manually. As shown, the mesh is much more refined near the blade, and gets coarser the larger the distance is from the blade. For the area near the blade, a sphere of influence-controlled mesh sizing was used with a sphere of radius 30 m and corresponding element size of 2 m. A face sizing on the blade surface was also used, with an element size of .3 m. To refine the mesh even further around the blade surface, custom inflation was implemented with a growth rate of 1.2 and 5 layers. Finally, a match control was added to the two periodic faces.
<hr>

### 3. Setup
<div class="row mt-4">

  <div class="col-md-6 mb-3">
    <img 
      src="{{ '/assets/images/Inlets.jpg' | relative_url }}" 
      class="img-fluid border rounded" 
      style="height: 300px; width: 100%; object-fit: cover; object-position: center;"
      alt="Inlets">
    <p class="text-muted small text-center mt-2"><i>Inlets</i></p>
  </div>

  <div class="col-md-6 mb-3">
    <img 
      src="{{ '/assets/images/OutletAndPeriodics.jpg' | relative_url }}" 
      class="img-fluid border rounded" 
      style="height: 300px; width: 100%; object-fit: cover; object-position: center;"
      alt="Walls">
    <p class="text-muted small text-center mt-2"><i>Outlet and Periodic Faces</i></p>
  </div>


</div>
**Model:** SST k-omega.
<br>
**Fluid:** Air at standard STP.
<br>
The curved face of the geometry and the smallest face of the geometry were set as inlets, and the larger hemispherical face was set as the outlet. The two remaining faces were set as interfaces, as they are the periodic elements that allowed the system to be duplicated twice to simulate a full wind turbine. The initial velocity was set to -12 m/s in the z-direction for both inlets to simulate normal winds. The outlet was set to have an exit pressure of 1 atm. The two remaining faces were set as periodic interfaces. The blade was treated as a wall.
<hr>

### 4. Results
After the analysis had been completed, I plotted a number of different variables on the blade itself and the air surrounding it.
<br>
I first plotted the pressure contours on the blade surface, and around the blade at different x values. I found that on the front of the blade, the pressure was uniform, but on the backside of the blade there was a pressure drop near the end, which creates a lift force (which I show later), causing the blade to rotate and produce energy.
<br>
As for the pressure on the plane, I found that the pressure on the sides normal to the z-axis have lower pressures, and the pointed side normal to the y-axis has a higher pressure, hence the lift force.
<div class="row mt-4">
  <div class="col-md-4 mb-3">
    <img 
      src="{{ '/assets/images/TurbPresContBack.jpg' | relative_url }}" 
      class="img-fluid border rounded" 
      style="height: 170px; width: 100%; object-fit: cover;"
      alt="Global Mesh">
    <p class="text-muted small text-center mt-2"><i>Turbine rear pressure contour</i></p>
  </div>

  <div class="col-md-4 mb-3">
    <img 
      src="{{ '/assets/images/TurbPresContFront.jpg' | relative_url }}" 
      class="img-fluid border rounded" 
      style="height: 170px; width: 100%; object-fit: cover;"
      alt="Inflation Layers">
    <p class="text-muted small text-center mt-2"><i>Turbine front pressure contour</i></p>
  </div>

  <div class="col-md-4 mb-3">
    <img 
      src="{{ '/assets/images/TurbPresContPlane.jpg' | relative_url }}" 
      class="img-fluid border rounded" 
      style="height: 170px; width: 100%; object-fit: cover;"
      alt="Trailing Edge">
    <p class="text-muted small text-center mt-2"><i>Fluid pressure contour on the plane at x= -10</i></p>
  </div>
</div>
As shown below, I also plotted the velocity vectors and streamlines. On the left hand side image, it can be seen that the fluid slows (blue & green arrows) at higher pressures, and speeds up (red arrows) at lower pressures, which follows Bernoulli's Principle, which acts as a form of validation of the solution.
<br>
On the right hand side image, velocity streamlines are shown, originating from the inlet. These streamlines strongly show that the energy in the fluid decreases dramatically after it comes in contact with the turbine, meaning that the energy is transferred from the fluid into the turbine, causing rotation and therefore energy to be produced from the turbine. Essentially, the turbine is extracting energy from the wind and transforming it into mechanical torque to generate power.

<div class="row mt-4">

  <div class="col-md-6 mb-3">
    <img 
      src="{{ '/assets/images/VelocityContPln1.jpg' | relative_url }}" 
      class="img-fluid border rounded" 
      style="height: 300px; width: 100%; object-fit: cover; object-position: center;"
      alt="Inlets">
    <p class="text-muted small text-center mt-2"><i>Velocity vectors at x = 10</i></p>
  </div>

  <div class="col-md-6 mb-3">
    <img 
      src="{{ '/assets/images/VelStreamlines.jpg' | relative_url }}" 
      class="img-fluid border rounded" 
      style="height: 300px; width: 100%; object-fit: cover; object-position: center;"
      alt="Walls">
    <p class="text-muted small text-center mt-2"><i>Velocity streamlines originating at the inlets</i></p>
  </div>


</div>
<hr>

<div id="imageModal" class="modal">
  <span class="close-btn">&times;</span>
  <img class="modal-content" id="modalImg" onclick="event.stopPropagation()">
  <div id="caption"></div>
</div>

