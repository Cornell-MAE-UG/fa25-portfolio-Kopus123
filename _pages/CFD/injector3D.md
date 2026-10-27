---
layout: project
title: 3D Ursa I Injector CFD
permalink: /analysis/Injector3D/
description: "Three-dimensional transient multiphase CFD of LPC's Ursa I injector"
technologies: [Spaceclaim, ANSYS Fluent, ANSYS CFD-Post]
---

<div style="clear: both;"></div>

<div style="position: relative; top: -50px; margin-bottom: -25px;">
  <strong>Objective:</strong> Extend the <a href="{{ '/analysis/Injector2D/' | relative_url }}">2D Ursa I injector simulation</a> to the full 3D geometry, using a multiphase Volume of Fluid (VOF) model to track the liquid jets, how they impinge, and how flow behaves at the orifice entrances.
  <br>
  <br>
  <em>Note: The 2D simulation could not capture the orifice discharge coefficient because a real orifice chokes the flow around its whole circumference. Resolving the orifices in 3D was a main motivation for this simulation.</em>
  <br>
  <em>This page will be updated shortly with more information about the process. Right now a general overview is given.</em>
</div>
<hr>

### 1. Geometry
<ul>
    <li>Fluid volume of the Ursa I injector: a central axial manifold feeding four axial orifices, and four radial feed arms, each feeding an angled orifice</li>
    <li>The angled jets are aimed to impinge on the axial jets just downstream of the faceplate</li>
    <li>Includes a section of the combustion chamber below the faceplate so the jets can develop after impingement</li>
</ul>
<div class="d-flex flex-wrap justify-content-center gap-4 mt-3 mb-5">
  <img src="{{ '/assets/images/Ursa3DCFD/VelVolRndrIso.png' | relative_url }}" class="img-fluid border rounded" style="max-height: 320px; width: auto; cursor: zoom-in;" alt="3D injector geometry with velocity volume rendering">
  <img src="{{ '/assets/images/Ursa3DCFD/JuicyVolFrac.png' | relative_url }}" class="img-fluid border rounded" style="max-height: 320px; width: auto; cursor: zoom-in;" alt="Liquid volume fraction in manifolds and orifices">
</div>

<hr>

### 2. Setup
**Model:** Volume of Fluid (VOF) multiphase, transient
<br>
**Solver:** ANSYS Fluent, post-processed in CFD-Post
<ul>
    <li>Liquid enters through the manifolds and is injected into a gas-filled chamber; the VOF model tracks the liquid–gas interface</li>
    <li>The volume renderings below show liquid volume fraction (red = fully liquid), velocity, and pressure</li>
</ul>

<hr>

### 3. Results
<ul>
  <li><strong>Impingement:</strong> each angled jet meets its paired axial jet just below the faceplate (bright spots in the close-up below). The merged jets then join into a single coherent column along the chamber axis.</li>
  <li><strong>Atomization:</strong> the column stays largely intact for several centimeters before diffusing. That suggests the mesh was too coarse to resolve breakup into droplets, the same limitation seen in my <a href="{{ '/projects/2026-Rocket-Engine/injector/' | relative_url }}">5 kN engine injector</a> VOF-to-DPM run.</li>
  <li><strong>Orifice velocity:</strong> jets reach a peak of about 103 m/s inside the orifices, while the manifolds stay nearly stagnant</li>
</ul>

<div class="row justify-content-center mt-4">
  <div class="col-md-6 mb-3 text-center">
    <img src="{{ '/assets/images/Ursa3DCFD/Fullimpingment.png' | relative_url }}" class="img-fluid border rounded" style="max-height: 500px; width: auto; cursor: zoom-in;" alt="Full impingement, liquid volume fraction">
    <p style="font-size: 0.9rem; margin-top: 10px;">Liquid volume fraction: jets merge into a single column</p>
  </div>
  <div class="col-md-6 mb-3 text-center">
    <img src="{{ '/assets/images/Ursa3DCFD/ImpingementCloseup.png' | relative_url }}" class="img-fluid border rounded" style="max-height: 500px; width: auto; cursor: zoom-in;" alt="Impingement close-up">
    <p style="font-size: 0.9rem; margin-top: 10px;">Close-up of the impingement points</p>
  </div>
  <div class="col-md-6 mb-3 text-center">
    <img src="{{ '/assets/images/Ursa3DCFD/VelVolRndrFront.png' | relative_url }}" class="img-fluid border rounded w-100" style="height: auto; cursor: zoom-in;" alt="Velocity volume rendering">
    <p style="font-size: 0.9rem; margin-top: 10px;">Velocity volume rendering</p>
  </div>
  <div class="col-md-6 mb-3 text-center">
    <img src="{{ '/assets/images/Ursa3DCFD/FullVelStream.png' | relative_url }}" class="img-fluid border rounded w-100" style="height: auto; cursor: zoom-in;" alt="Velocity streamlines">
    <p style="font-size: 0.9rem; margin-top: 10px;">Velocity streamlines</p>
  </div>
</div>

<ul>
  <li><strong>Orifice entrance losses:</strong> the pressure gradient is concentrated at the sharp-edged orifice entrances, strongest at the four axial orifices. The pressure drop across the injector happens almost entirely there.</li>
  <li><strong>Flow separation:</strong> in the angled fuel orifices, the flow separates from one wall at the entrance, leaving a low-velocity region (a vena contracta) along that side. This shrinks the effective flow area, which is why a sharp-edged orifice's discharge coefficient is well below 1.</li>
  <li><strong>Dead-end recirculation:</strong> streamlines in each radial feed arm curl back at the closed end past the orifice, so that end of the arm is a small recirculation pocket</li>
  <li><strong>Negative pressure:</strong> the minimum pressure is about −6.3 MPa at the orifice entrances. A liquid can't sustain that, so in the real injector those regions would likely cavitate. Since this simulation has no cavitation model, the local pressures there aren't physical.</li>
</ul>

<div class="row justify-content-center mt-4">
  <div class="col-md-6 mb-3 text-center">
    <img src="{{ '/assets/images/Ursa3DCFD/PresGrad.png' | relative_url }}" class="img-fluid border rounded w-100" style="height: auto; cursor: zoom-in;" alt="Pressure gradient vectors">
    <p style="font-size: 0.9rem; margin-top: 10px;">Pressure gradient concentrated at the orifice entrances</p>
  </div>
  <div class="col-md-6 mb-3 text-center">
    <img src="{{ '/assets/images/Ursa3DCFD/PresVolRndr.png' | relative_url }}" class="img-fluid border rounded w-100" style="height: auto; cursor: zoom-in;" alt="Pressure volume rendering">
    <p style="font-size: 0.9rem; margin-top: 10px;">Pressure volume rendering</p>
  </div>
  <div class="col-md-6 mb-3 text-center">
    <img src="{{ '/assets/images/Ursa3DCFD/FuelSteam.png' | relative_url }}" class="img-fluid border rounded w-100" style="height: auto; cursor: zoom-in;" alt="Fuel arm streamlines">
    <p style="font-size: 0.9rem; margin-top: 10px;">Fuel arm streamlines: dead-end recirculation and orifice entry</p>
  </div>
  <div class="col-md-6 mb-3 text-center">
    <img src="{{ '/assets/images/Ursa3DCFD/FuelPresDrop.png' | relative_url }}" class="img-fluid border rounded w-100" style="height: auto; cursor: zoom-in;" alt="Fuel orifice entrance">
    <p style="font-size: 0.9rem; margin-top: 10px;">Fuel orifice entrance: separation along one wall</p>
  </div>
</div>

<hr>

### 4. Reflection
<ul>
  <li>Moving to 3D captured effects the 2D simulation couldn't: separation around the full orifice circumference, interaction between jets from different orifices, and the shape of the merged spray column</li>
  <li>A finer mesh near the impingement zone would be needed to resolve jet breakup and atomization</li>
  <li>Adding a cavitation model would make the pressures at the orifice entrances physically meaningful and improve the discharge coefficient prediction</li>
</ul>

<br>
<hr>

<div id="imageModal" class="modal">
  <span class="close-btn">&times;</span>
  <img class="modal-content" id="modalImg" onclick="event.stopPropagation()">
  <div id="caption"></div>
</div>
