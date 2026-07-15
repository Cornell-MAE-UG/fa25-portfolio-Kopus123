---
layout: project
title: CC & Nozzle Thermal
description: Combustion Chamber and Nozzle Design with CHT Analysis
image: /assets/images/RocketEngine/NozzleFull.png
permalink: /projects/2026-Rocket-Engine/cc-nozzle/
technologies: [Autodesk Fusion 360, ANSYS Fluent, SpaceClaim, RPA, NASA CEA]
---
<div style="text-align: center; padding-bottom: 25px">
  <em>Click to enlarge images</em>
</div>

<style>
  /* Centers the default Jekyll page title */
  h1 {
    text-align: center;
    margin-bottom: 25px;
  }
  
  /* Stops the theme from floating the image and shrinks it */
  img:not([style]) {
    display: block !important;
    float: none !important;
    margin: 0 auto 40px auto !important;
    max-width: 200px !important; /* Change this number to shrink/grow the nozzle */
    width: 100% !important;
  }
</style>

<div style="clear: both;"></div>

<div style="margin-bottom: 25px; width: 100%; text-align: center; padding-top: 15px;">
  <h2 style="font-size: 1.8rem; font-weight: 700; margin: 0; color: #111; letter-spacing: 0.5px;">
    Combustion Chamber & Nozzle Architecture
  </h2>
</div>

<div style="width: 100%; display: block; color: #333; font-size: 1.05rem; line-height: 1.65;">

  <h3 style="color: #000000; font-weight: 800; font-size: 1.5rem; margin-bottom: 15px; padding-bottom: 5px;">
    1. Thermodynamic Sizing & Geometry
  </h3>
  <p>
    This combustion chamber and converging-diverging nozzle were sized from scratch as an independent personal engine design. Using RPA and NASA CEA, the geometry was optimized for expansion and specific impulse. Due to the extreme flame temperatures of LOX/RP-1, a combination of counter-flow regenerative cooling and film cooling was implemented to prevent structural degradation of the chamber walls. Currently, the thermal structuring has not been finalized, and is something I am currently working on.
  </p>
  
  <ul style="margin-bottom: 30px;">
    <li><strong>Chamber Pressure (Pc):</strong> 2758000 Pa (400 Psi)</li>
    <li><strong>Characteristic Length (L*):</strong> 1.1 m sized to ensure complete residence time and vaporization for RP-1.</li>
    <li><strong>Expansion Ratio (ε):</strong> 4.9</li>
    <li><strong>Throat Diameter:</strong> 39.4 mm (Area: 12.22 cm²) &nbsp;|&nbsp; <strong>Chamber Diameter:</strong> 73.8 mm &nbsp;|&nbsp; <strong>Total Length:</strong> 406 mm</li>
    <li><strong>Nozzle Contour:</strong> 80% Rao bell nozzle (θn = 23°, θe = 13°), chosen over a full conical nozzle to reduce length and weight while retaining most of the ideal expansion efficiency.</li>
    <li><strong>Cooling Architecture:</strong> Counter-flow regenerative cooling channels utilizing RP-1 as the working fluid, with <strong>60 cooling channels</strong> and a <strong>0.5mm inner wall thickness</strong>, running through the entire chamber and nozzle. 15% of the fuel mass flow is diverted to internal <strong>film cooling</strong> — while a 10% diversion theoretically satisfied thermal margins, 15% was selected both for additional thermal margin and for <strong>Design for Manufacturability (DFM)</strong>, ensuring film cooling orifice diameters remained large enough for reliable, cost-effective machining.</li>
    <li><strong>Material:</strong> The chamber is modeled as a monocoque <strong>CuCrZr (Copper Chromium Zirconium)</strong> structure. This copper alloy was selected to maximize thermal conductivity, allowing rapid heat transfer from the hot-gas side to the regenerative coolant to prevent localized melting, while retaining structural yield strength at elevated operational temperatures.</li>
  </ul>

  <div class="row mt-3 mb-5 justify-content-center">
    <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/RocketEngine/NozzleFull.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Chamber Profile">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Chamber & Nozzle Profile</p>
    </div>
    <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/RocketEngine/Regen-CS.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Cooling Channels">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Regenerative Cooling Channel Cross-Section</p>
    </div>
  </div>


  <h3 style="color: #000000; font-weight: 800; font-size: 1.5rem; margin-bottom: 15px; padding-bottom: 5px;">
    2. Conjugate Heat Transfer (CHT) Simulation
  </h3>
  <p>
    To accurately predict the wall temperatures and validate the cooling architecture, a Conjugate Heat Transfer (CHT) simulation was set up in ANSYS Fluent. This model couples the fluid domains (hot combustion gas and cold RP-1 coolant) with the solid thermal conduction through the CuCrZr walls.
  </p>

  <ul style="margin-bottom: 30px;">
    <li><strong>Fluid mesh: </strong>Quad dominant mesh with a y+=1 at the wall between the fluid and wall. 40 boundary layers were added to transition the near-wall cells to the main domain ones.</li>
    <li><strong>Solid mesh: </strong>The solid was meshed separately from the fluid (Quad dominant), but was linked with a mesh interface in the Fluent solver</li>
    
<div class="row mt-3 mb-5 justify-content-center">
    <div class="col-md-4 col-12 mb-4 text-center">
    <img src="{{ '/assets/images/RocketEngine/cht-mesh.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Mach Contour">
    <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Full Mesh</p>
    </div>
    <div class="col-md-4 col-12 mb-4 text-center">
    <img src="{{ '/assets/images/RocketEngine/cht-mesh-close.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Wall Temp Contour">
    <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Solid Mesh</p>
    </div>
    <div class="col-md-4 col-12 mb-4 text-center">
    <img src="{{ '/assets/images/RocketEngine/cht-mesh-rllyclose.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Heat Flux">
    <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Boundary Layer Mesh (y+=1)</p>
    </div>
</div>


<li><strong>Solver Setup:</strong> Steady State pressure-based solver</li>
<li><strong>Turbulence & Wall Treatment:</strong> The <strong>SST k-omega</strong> model was selected due to its well-documented reliability in resolving near-wall boundary layer gradients and heat flux without incurring extreme computational costs.</li>
<li><strong>Boundary Conditions (Hot Gas):</strong> Gas temperature species transport properties derived from NASA CEA. Modeled as a single fluid with the properties of the combusted gasses.
    <ul><li>For simplicity, the gas was injected through the entire entrance of the chamber, as at the time the geometry for the injector had not been started (elaborated on in the results section).
    </li></ul></li>
<li><strong>Boundary Conditions (Coolant):</strong> Tabulated RP-1 data was used for the coolant flow. The RP-1 enters the regenerative cooling jacket at <strong>298 K</strong> and absorbs heat throughout the counter-flow process, exiting into the injector manifold at approximately <strong>569 K</strong> (validated via RPA fluid tables).</li>
  </ul>

  <div class="row mt-3 mb-5 justify-content-center">
    <div class="col-md-4 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/RocketEngine/cht-vel.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Mach Contour">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Velocity Contour</p>
    </div>
    <div class="col-md-4 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/RocketEngine/cht-temp.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Wall Temp Contour">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Solid Wall Temperature Profile</p>
    </div>
    <div class="col-md-4 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/RocketEngine/cht-heatflux.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Heat Flux">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Wall Heat Flux</p>
    </div>
  </div>


  <h3 style="color: #000000; font-weight: 800; font-size: 1.5rem; margin-bottom: 15px; padding-bottom: 5px;">
    3. Thermal Verdict & Iterative Improvements
  </h3>
  <ul style="margin-bottom: 50px;">
  
  <li><strong>Max Nozzle Temperature:</strong> The simulation accurately predicted a maximum wall temperature in the nozzle expansion section of <strong>1050 K</strong>, which will cause the walls to melt, addressing the need for film cooling.</li>
  
  <li><strong>Coolant Performance:</strong> The RP-1 coolant successfully transitioned from 298 K to 569 K, absorbing the necessary heat flux from the walls prior to injection without crossing the coking limit threshold. 
    <ul>
      <li>According to the heat flux contour, more heat was transferred at the throat, and a more steady heat flux on the chamber walls, all as intended.</li>
    </ul>
  </li>
  
  <li><strong>Model Anomaly (Peak Chamber Temp):</strong> The initial CHT simulation showed a localized peak wall temperature of <strong>2500 K</strong> in the combustion chamber. This anomaly is a known modeling artifact resulting from a simplified boundary condition: the simulation modeled the propellants as pre-combusted hot gas entering the chamber as a single uniform flow, completely neglecting the physical injector orifices. Without resolving the individual propellant streams and the near-wall film cooling boundary layer, the simulation artificially subjected the walls to the core flame temperature.</li>

</ul>
  
  <p style="margin-bottom:25px"><strong>A refined CHT simulation utilizing an updated mesh and precise injector boundary physics is currently underway to accurately model the localized film cooling effects and more accurate gas entry.</strong></p>

</div> <style>
  #modalImg {
    width: auto !important;
    height: auto !important;
    max-width: 90vw !important;
    max-height: 90vh !important;
    object-fit: contain !important;
    margin: auto;
    display: block;
  }
</style>

<div id="imageModal" class="modal">
  <span class="close-btn">&times;</span>
  <img class="modal-content" id="modalImg" onclick="event.stopPropagation()">
  <div id="caption"></div>
</div>