---
layout: project
title: Rocket Engine Integration/Assembly
permalink: /projects/2026-Rocket-Engine/full-assembly/
technologies: [Autodesk Fusion 360, Ansys Fluent, Ansys Fluent Meshing, SpaceClaim, Research Papers (Sp-125, sp8089, etc.), Google Sheets]
image: /assets/images/RocketEngine/Inj&CC.png
---

<div style="text-align: center; padding-bottom: 25px">
  <em>Click to enlarge images</em>
</div>

<style>
  /* Centers the default Jekyll page title */
  h1 { text-align: center; margin-bottom: 25px; }
  
  /* Stops the theme from floating the image and shrinks it */
  img:not([style]) {
    display: block !important;
    float: none !important;
    margin: 0 auto 40px auto !important;
    max-width: 500px !important;
    width: 100% !important;
  }
</style>

<div style="clear: both;"></div>

<div style="margin-bottom: 25px; width: 100%; text-align: center; padding-top: 15px;">
  <h2 style="font-size: 1.8rem; font-weight: 700; margin: 0; color: #111; letter-spacing: 0.5px;">
    Full Systems Integration & Assembly
  </h2>
</div>

<div style="width: 100%; display: block; color: #333; font-size: 1.05rem; line-height: 1.65;">

  <h3 style="color: #000000; font-weight: 800; font-size: 1.5rem; margin-bottom: 15px; padding-bottom: 5px;">
    1. Mechanical Fastening & Sealing Architecture
  </h3>
  <p>
    The integration of the combustion chamber and the injector was designed to safely contain operating inlet pressures exceeding 500 psi while preventing the premature mixing of cryogenic LOX and ambient RP-1.
  </p>
  <ul style="margin-bottom: 30px;">
    <li><strong>Structural Interface:</strong> The injector body mates to the combustion chamber via a primary flanged connection, secured by a 12-bolt M6 circular pattern to ensure even pre-load distribution against the internal pressure.</li>
    <li><strong>Exterior Sealing:</strong> A high-pressure radial O-ring is utilized on the outer manifold boundaries to prevent RP-1 leakage into the ambient environment.</li>
    <li><strong>Pending Design Revision (Manifold Isolation):</strong> During a recent design review of the cross-section, a spatial conflict was identified where insufficient radial clearance exists for an isolation O-ring between the internal LOX and RP-1 manifolds. To eliminate the risk of catastrophic internal propellant mixing, the injector faceplate and manifold walls are currently undergoing a minor geometric revision to accommodate a dedicated inter-propellant seal, if needed.</li>
  </ul>

  <div class="row mt-3 mb-5 justify-content-center">
    <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/RocketEngine/bolts.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Cross Section">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Full Assembly</p>
    </div>
    <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/RocketEngine/exploded.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Exploded View">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Exploded View / Fluid Routing</p>
    </div>
  </div>
  <div class="row mt-3 mb-5 justify-content-center">
    <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/RocketEngine/bolt-cs.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Cross Section">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Top Assembly Cross-Section</p>
    </div>
    <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/RocketEngine/ThrustChamber.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Exploded View">
      <p style="font-size: 0.9rem; margin-top: 10px; margin-bottom: 0;">Full Assembly Cross-Section</p>
    </div>
  </div>

  <h3 style="color: #000000; font-weight: 800; font-size: 1.5rem; margin-bottom: 15px; padding-bottom: 5px;">
    2. Regenerative Fluid Routing
  </h3>
  <p>
    The RP-1 routing eliminates the need for complex external hardlines by leveraging a continuous internal flow path driven by the system's inherent pressure differentials.
  </p>
  <ul style="margin-bottom: 30px;">
    <li><strong>Counter-Flow Path:</strong> The RP-1 is injected at its highest pressure at the end of the converging-diverging nozzle. As it absorbs heat and expands through the counter-flow regenerative channels, the natural pressure gradient forces the fuel upward directly into the injector RP-1 manifold, priming it for entrance into the impingement orifices.</li>
  </ul>

  <h3 style="color: #000000; font-weight: 800; font-size: 1.5rem; margin-bottom: 15px; padding-bottom: 5px;">
    3. Phase II Integration (Ignition & Mounting)
  </h3>
  <p>
    When the primary thermodynamic and fluid routing architectures are completed, the design focus will shift toward the ignition system and test stand integration.
  </p>
  <ul style="margin-bottom: 50px;">
    <li><strong>Ignition method:</strong> An Augmented Spark Igniter (ASI) is currently the leading candidate for engine startup. The ASI will be integrated directly into the center of the injector faceplate once the thermal and spatial clearances are finalized.</li>
    <li><strong>Test Stand Hardpoints & Instrumentation:</strong> The next design will introduce structural revisions to allow for test stand mounting, alongside dedicated instrumentation taps (static pressure transducers and thermocouples) along the chamber walls.</li>
  </ul>

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