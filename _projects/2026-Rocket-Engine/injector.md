---
layout: project
title: Rocket Engine Injector
description: Injector
image: /assets/images/RocketEngine/inj-render.png
permalink: /projects/2026-Rocket-Engine/injector/
technologies: [Autodesk Fusion 360, Ansys Fluent, Ansys Fluent Meshing, SpaceClaim, Research Papers (Sp-125, sp8089, etc.), Google Sheets]
---
<div style= "text-align: center; padding-bottom: 25px">
  <em>Click to enlarge images</em>
</div>
<style>
  /* Centers the default Jekyll page title */
  h1 {
    text-align: center;
    margin-bottom: 25px;
  }

  /* Centers the auto-injected layout image without breaking our custom grid */
  img:not([style]) {
    display: block;
    margin: 0 auto 40px auto;
    max-width: 600px;
    width: 100%;
  }
</style>
<div style="margin-bottom: 25px; width: 100%; text-align: center;">
  <h2 style="font-size: 1.8rem; font-weight: 700; margin: 0; color: #111; letter-spacing: 0.5px;">
    Impinging Injector Architecture
  </h2>
</div>

<div style="width: 100%; display: block; color: #333; font-size: 1.05rem; line-height: 1.65;">

  <h3 style="color: #000000; font-weight: 800; font-size: 1.5rem; margin-bottom: 15px; padding-bottom: 5px;">
    1. System Sizing & Geometry
  </h3>
  <p>
    The injector was designed from scratch for a thrust chamber using LOX/RP-1. The primary objective of the design is to learn the design of thrust chambers and injectors. The injector-specific objectives are as follows: ensure proper impingement and mixing of propellants, keep the injector thermally stable, and satisfy my design parameters (listed below).
  </p>
  
  <ul style="margin-bottom: 30px;">
    <li><strong>Propellants:</strong> LOX/RP-1</li>
    <li><strong>Target O/F Ratio:</strong>2.4</li>
    <li><strong>Total Mass Flow:</strong>1.884 kg/s (LOX: 1.33 kg/s, RP-1: .554 kg/s (15% to film cooling))</li>
    <li><strong>Element Type:</strong> Unlike Triplets</li>
    <li><strong>Impingement Angle:</strong> 45 degrees designed to optimize the momentum ratio and distance from injector faceplate; -5 degree beta angle (towards the combustion chamber axis) to keep impingement far from chamber walls</li>
    <li><strong>Pressure Drop (ΔP):</strong> Designed for a 689476 Pa pressure drop (25% of chamber pressure) across the injector face to guarantee sufficient velocities through orifices</li>
  </ul>

  <h4>i. Injector features</h4>
  <ul style = "margin-bottom: 50px;">
    <li>3 sections that are joined by screws to allow for assembly to be reasonable/possible</li>
    <li>18 <strong>unlike triplet elements</strong> to allow for proper mixing and reasonable orifice diameters
      <ul><li>Chosen over doublets for safer impingement behavior (product travels downstream rather than requiring precise momentum balancing)</li>
      <li>Chosen over quads/pentads to keep orifice diameters ≥1mm for manufacturability</li>
      <li><strong>Beta angle of -5 degrees</strong> to accommodate for the cryogenic propellant LOX spray after entering combustion chamber</li>
      </ul></li>
    <li><strong>Film cooling holes</strong> (RP-1) near chamber walls allows for proper cooling
      <ul><li>RPA analysis and conjugate heat transfer (CHT) CFD analysis confirmed that regenerative cooling alone will likely not be enough to keep the chamber from melting (temps exceeding 1000K throughout the chamber and nozzle)</li>
      </ul></li>
    <li><strong>Regen cooling</strong> entrances from chamber (RP-1) to keep chamber from melting (counterflow to allow for better heat pickup into the coolant)</li>
    <li>RP-1 manifold near the faceplate (inlet through regen cooling channels) with O-ring groove to prevent leakage</li>
    <li>LOX <strong>dome manifold</strong> near the top
      <ul>
        <li>Distribution plate (which look like rectangular bars in the dome manifold cross section) to allow for more even flow through all orifices, as per suggestion from NASA SP8089</li>
        <li>Upstream to prevent heat transfer from the hotter RP-1 entering after cooling the chamber and nozzle (which would cause phase change), and to prevent any mixing with the RP-1, which might cause unwanted combustion</li>
      </ul></li>
    <li>Made with <strong>Inconel 718</strong> due to its exceptional aerospace applications and thermal resistance</li>
  </ul>

  <div style="display: flex; gap: 20px; margin-bottom: 40px; flex-wrap: wrap; justify-content: center;">
    <div style="flex: 1; min-width: 300px; border: 1px solid #ddd; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0,0,0,0.05);">
      <img src="{{ '/assets/images/RocketEngine/inj-render.png' | relative_url }}" alt="Injector Render" style="width: 100%; display: block;" />
      <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Full Injector Render</p>
    </div>
    <div style="flex: 1; min-width: 300px; border: 1px solid #ddd; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0,0,0,0.05);">
      <img src="{{ '/assets/images/RocketEngine/inj-faceplate.png' | relative_url }}" alt="Injector Faceplate" style="width: 100%; display: block;" />
      <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Injector Faceplate</p>
    </div>
    <div style="flex: 1; min-width: 300px; border: 1px solid #ddd; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0,0,0,0.05);">
      <img src="{{ '/assets/images/RocketEngine/inj-cross-sec.png' | relative_url }}" alt="Injector Cross Section" style="width: 100%; display: block;" />
      <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Injector Cross Section</p>
    </div>
  </div>


  <h3 style="color: #000000; font-weight: 800; font-size: 1.5rem; margin-bottom: 15px; padding-bottom: 5px;">
    2. Transient Multi-Phase CFD (ANSYS Fluent)
  </h3>
  <p>
    To validate the impingement, a transient cold-flow simulation was executed.
  </p>

  <h4>i. Mesh</h4>
    <ul>
      <li>Due to lack of computational power (no supercomputers available) a relatively coarse mesh with boundary layers in the orifices were used</li>
      <li>Automatic mesh adaption (AMR) was not used due to its unreliable integration with periodic boundaries in ANSYS Fluent
        <ul><li>AMR usually causes left-handed faced cells and cells with negative volume if ran with periodic boundaries, so I am currently working on a full injector model to utilize AMR</li></ul></li>
      <li>A polyhedral mesh was used in this run, but for future runs I will utilize a poly-hexcore mesh</li>
    </ul>

  <div class="d-flex flex-wrap justify-content-center gap-4 mt-3 mb-5">
    <div style="width: 28%; min-width: 220px; text-align: center;">
      <img src="{{ '/assets/images/RocketEngine/full-mesh.png' | relative_url }}" class="img-fluid border rounded" style="height: 220px; width: 100%; object-fit: cover;" alt="Periodic Injector Mesh">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Injector Mesh</p>
    </div>
    
    <div style="width: 28%; min-width: 220px; text-align: center;">
      <img src="{{ '/assets/images/RocketEngine/lox-bls.png' | relative_url }}" class="img-fluid border rounded" style="height: 220px; width: 100%; object-fit: cover;" alt="LOX Orifice Boundary Layers">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">LOX Orifice Boundary Layers</p>
    </div>
    
    <div style="width: 28%; min-width: 220px; text-align: center;">
      <img src="{{ '/assets/images/RocketEngine/rp1-bls.png' | relative_url }}" class="img-fluid border rounded" style="height: 220px; width: 100%; object-fit: cover;" alt="RP-1 Orifice Boundary Layers">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">RP-1 Orifice Boundary Layers</p>
    </div>
  </div>

<h4>ii. Setup</h4>
  <ul style="margin-bottom: 30px;">
    <li><strong>Model:</strong> VOF-to-DPM (Volume of Fluid to Discrete Phase Model) transition to accurately capture primary jet breakup and secondary droplet atomization while lowering computational costs.</li>
    <li><strong>Turbulence Model:</strong> SST k-omega chosen for good overall turbulence modeling without high computational costs</li>
    <li><strong>Inlets:</strong> The tops of all the orifices were pressure inlets set at ~3.3e6 Pa (480 psi) to account for pressure loss in the manifolds (elaborated later)</li>
    <li><strong>Outlet: </strong>The outlet was in the chamber, so it was set to a 400 psi pressure outlet</li>
  </ul>

  <div class="row mt-3 mb-5">
    
    <div class="col-6 mb-4 text-center">
      <img src="{{ '/assets/images/RocketEngine/inj-vol-frac.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Volume Fraction">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">VOF Phase Tracking</p>
    </div>
    
    <div class="col-6 mb-4 text-center">
      <img src="{{ '/assets/images/RocketEngine/inj-vel-vol-rndr.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Velocity Volume Render">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Velocity Magnitude</p>
    </div>

    <div class="col-6 mb-4 text-center">
      <img src="{{ '/assets/images/RocketEngine/inj-vel-vec.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Velocity Vectors">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Velocity Vectors & Recirculation</p>
    </div>
    
    <div class="col-6 mb-4 text-center">
      <img src="{{ '/assets/images/RocketEngine/inj-pres-vol-rndr.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Pressure Volume Render">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Manifold Pressure Distribution</p>
    </div>

  </div>


  <h4>
    iii. Performance Verdict
  </h4>
  <ul style="margin-bottom: 25px;">
    <li>This was my first VOF-to-DPM simulation that I have ran, and it was more to figure out the mechanics of the setup. Therefore, there are some improvements necessary.</li>
    <li><strong>Atomization Quality:</strong> The VOF-to-DPM simulation did characterize impingement going along the axis of the chamber, but due to the coarse mesh, none of it was converted into particles for the DPM. This did not produce incorrect results for the impingement, but the coarse mesh likely reduced accuracy but increased computation time.</li>
    <li><strong>Velocities:</strong> Velocity volume renderings and vectors show that the speed inside the orifices were faster than normal (around 50 m/s in the orifices compared to the calculated ~30 m/s), which I think could be a result of 1) no AMR and 2) a high gradient between the air and propellant phases (causes a large velocity artifact for the air phase, which in turn causes a higher mass flow and velocity for propellant phases)
      <ul>
      <li>I have seen in previous simulations air artifact velocity being extraordinarily high (1200+ m/s), causing propellants in the orifices to reach speeds of over 100 m/s, but I presume, due to my boundary layers with an estimate of y+ = 30, the solver was able to capture more of the physics accurately and did not produce absurdly large velocity artifacts, though there is room for improvement in this simulation</li></ul></li>
    <li><strong>Pressure:</strong> The pressure volume render shows an odd distribution of pressure, with a large pressure gradient at the inlet and virtually no pressure gradient elsewhere, leaving no pressure drop across the orifices. This is undoubtedly caused by the lack of manifolds in the geometry, and in my next simulation I will model the volume of the manifolds as well to acquire an accurate simulation.</li>
  </ul>
  <p style = "margin-bottom:25px"><strong>A new simulation simulating the entire injector geometry (not just the faceplate, and not periodic) is coming soon to properly validate the design of the injector</strong></p>

</div>

<style>
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