---
layout: project
title: 2D Ursa I Injector CFD
permalink: /analysis/Injector2D/
description: "CFD Analysis of LPC's Ursa I Injector"
technologies: [Spaceclaim, ANSYS Mechanical, ANSYS Fluent, ANSYS CFD-Post]
---

<div style="clear: both;"></div>

<div style="position: relative; top: -50px; margin-bottom: -25px;">
  <strong>Objective:</strong> Analyze and verify the impingement of the Ursa I injector during a water-only cold flow to identify potential recirculation zones.
  <br>
  <br>
  <em>Note: Hand calculations were performed by the injector designer, so this simulation was used to validate the calculations and geometry.</em>
</div>
<hr>

### 1. Geometry
<ul>
    <li>Imprint of the 3D injector CAD model made in Fusion 360 by another team member</li>
    <li>Also includes a rough modeling of the combustion chamber, as well as rough model of the converging section of the nozzle</li>
</ul>
<div class="d-flex flex-wrap justify-content-center gap-4 mt-3 mb-5">
  <img src="{{ '/assets/images/UrsaCFD/2dinjgeo1.png' | relative_url }}" class="img-fluid border rounded" style="max-height: 220px; width: auto;" alt="CFD Geometry 1">
  <img src="{{ '/assets/images/UrsaCFD/2dinjgeo2.png' | relative_url }}" class="img-fluid border rounded" style="max-height: 220px; width: auto;" alt="CFD Geometry 2">
</div>



<hr>

### 2. Mesh
<ul>
    <li>50159 cells with a min, avg, max orthogonal quality of .27, .97, and 1, respectively</li>
    <li>Uses the Quad dominant method for faster computing and better integration into geometry</li>
    <li>As shown, there are boundary layers (inflation) on the inlet manifolds and all orifices, with a first layer height of 1e-5 m (estimated) due to the high velocity and turbulence of the flow</li>
    <li>The mesh is relatively fine due to fast computing power for 2D simulations, and the system proved to be mesh independent (discussed later)</li>
</ul>
<div class="d-flex flex-wrap justify-content-center gap-4 mt-4 mb-4">
  <img src="{{ '/assets/images/UrsaCFD/2dinjmesh1.png' | relative_url }}" class="img-fluid border rounded" style="max-height: 220px; width: auto;" alt="Global Mesh">
  <img src="{{ '/assets/images/UrsaCFD/2dinjmesh2.png' | relative_url }}" class="img-fluid border rounded" style="max-height: 220px; width: auto;" alt="Inflation Layers">
</div>


<hr>

### 3. Setup
**Model:** SST k-omega.
<br>
**Fluid:** Water
  <ul>
    <li>Planar model in 2D space with a depth of 1m (to simplify hand calcualtions)</li>
    <li>Uses the pressure based transient solver due to the initial conditions changing the outcome of the final solution</li>
    <li>Used mass flow inlets scaled with the 1m depth of the Fluent solver in 2D and utilized a pressure outlet at 0 Pa gauge pressure to simulate the ambient enviornment
      <ul>
        <li>A mass flow inlet is used here due to the solver's extrusion of the geometry by 1 meter. A pressure inlet, though more realistic in the real world, would have caused an unreasonably high velocity and mass flow rate for the injector, which it is not designed for. This will be elaborated more on in the results section</li>
      </ul>
    </li><li>Used coupled scheme, and a time step of 1e-5 seconds</li>
  </ul>
<div class="row justify-content-center mt-4">
  <div class="col-md-8 mb-3 text-center">
    <img src="{{ '/assets/images/UrsaCFD/2dinjsetup.png' | relative_url }}" class="img-fluid border rounded" alt="Inlets">
  </div>
</div>

<br>

<hr>

### 4. Results
<ul>
  <li>After .002 seconds of flow time, the flow was mostly developed and ready to analyze, as the strict convergence criteria of 1e-6 for all residuals were consistently met, as shown below</li>
  <li>After some brief analyzing, the injector impingement seemed to have worked well</li>
  <li>Recirculation zones found near the impingement zone (large recirculation) and near the collision of the axial hole's flow with the fuel (angled) flow (likely not good due to its nearness to the orifices)</li>
  <li>Since the inlet pressure is much lower than the intended inlet pressure for the injector, the pressure drop calculated here of ~78 psi is very likely not the actual pressure drop for the injector, even during cold flow
  <ul>
    <li>The hand calculated pressure drop was about 230 psi, which indicates the unreliability of the pressure in this specific simulation</li>
    <li>The pressure in the combustion chamber is less than atmospheric pressure, which also leads to doubt for the accuracy of the pressure drop</li>
  </ul>
  </li><li>Streamlines found some odd behavior of the axial properllant curving back up towards the fuel orifice due to the lower pressure in that region; might affect combustion in a real world flow</li>
</ul>

<br>

<br>
<div class="row justify-content-center mt-4">
  
  <div class="col-md-12 mb-4 text-center">
    <img src="{{ '/assets/images/UrsaCFD/2dinjres.png' | relative_url }}" class="img-fluid border rounded w-100" style="height: auto;" alt="Residuals">
  </div>

  <div class="col-md-6 mb-3">
    <img src="{{ '/assets/images/UrsaCFD/2dinjvelcont.png' | relative_url }}" class="img-fluid border rounded w-100" style="height: auto;" alt="Velocity Contour">
  </div>
  <div class="col-md-6 mb-3">
    <img src="{{ '/assets/images/UrsaCFD/2dinjprescont.png' | relative_url }}" class="img-fluid border rounded w-100" style="height: auto;" alt="Pressure Contour">
  </div>
  <div class="col-md-6 mb-3">
    <img src="{{ '/assets/images/UrsaCFD/2dinjvelvec.png' | relative_url }}" class="img-fluid border rounded w-100" style="height: auto;" alt="Velocity Vectors">
  </div>
  <div class="col-md-6 mb-3">
    <img src="{{ '/assets/images/UrsaCFD/2dinjstream.png' | relative_url }}" class="img-fluid border rounded w-100" style="height: auto;" alt="Streamlines">
  </div>
  
</div>

<hr>
### 5. Reflection
<ul>
  <li>This 2D sim fulfilled two primary objectives: learning and low-cost initial simulation
    <ul>
      <li>This sim served as the first unguided simulation conducted independently, so I gained deep insight on many aspects of basic single-phase transient CFD</li>
      <li>The simulation was also helpful in finding the aspects in the objective while minimizing required computation power and without adding extreme complexity for my first simulation</li>
      <li>In retrospect, optimizations such as increasing the under relaxation factors would have increased the speed of the simulation, but the original numerical setup was still robust and met validation criteria</li>
    </ul>
  </li><li>The simulation also allowed the visualization of the injector impingement which was the primary reason of the simulation</li>
  <li>More complex simulations in the future (such as 3D multiphase) could use this simulation as a reference for its accuracy and setup</li>
  <li>One shortcoming of this simulation is the calculation of the discharge coefficient:
    <ul>
      <li>Using the calculation that the discharge coefficient is actual mass flow divided by theoretical mass flow, and by also using the relationship that mass flow is directly proportional to velocity for incompressible fluids, the coefficient of discharge can be calculated by dividing actual orifice velocity by the calculated free stream velocity.</li>
      <li>The velocity in the orifice was calculated as 39.94 m/s and in fluent as 33.51 m/s, implying a coefficient of discharge of .839. This value significantly exceeds the predicted value of ~.6 for a sharp bend, so I think that the 2d physics for this simulation cannot capture the discharge coefficient properly due to a 3D orifice choking the flow from the entire circumference rather than just a point</li>
</ul>

<br>
<hr>

<div id="imageModal" class="modal">
  <span class="close-btn">&times;</span>
  <img class="modal-content" id="modalImg" onclick="event.stopPropagation()">
  <div id="caption"></div>
</div>

