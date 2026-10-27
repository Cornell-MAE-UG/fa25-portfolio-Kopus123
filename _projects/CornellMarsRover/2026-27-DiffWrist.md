---
layout: project
title: Roller-Crown Differential Wrist
description: Zero-backlash conical roller-pin bevel differential for the Cornell Mars Rover arm wrist.
permalink: /projects/cmr-diff-wrist/
status: current
image: /assets/images/DiffWrist/prototype.jpg
technologies: [Autodesk Fusion 360, OpenSCAD, Python (manifold3d, CadQuery/OpenCascade, Shapely), 3D Printing (Bambu Lab Studio), moteus motor controllers]
current: true
---

<div style="clear: both;"></div>

<style>
  /* Center title */
  h1 {
    text-align: center;
    margin-bottom: 25px;
  }

  /* Scope main content images specifically so modals are never touched */
  .container img:not(.modal-content),
  .post-content img:not(#modalImg) {
    display: block;
    margin: 0 auto 40px auto;
    max-width: 600px;
    width: 100%;
    height: auto;
  }
</style>

<div class="summary-box">
  <h4>At a Glance</h4>
  <ul>
    <li><strong>Problem:</strong> last year's differential wrist was shelved over backlash. I wanted to see whether a gear with rolling contact could remove that backlash while adding torque margin.</li>
    <li><strong>What I did:</strong> designed a differential wrist around a custom gear with rolling contact and no designed-in backlash. I generated the tooth geometry numerically when no published equations existed, then took it through three CAD revisions and two 3D-printed prototypes.</li>
    <li><strong>Result:</strong> the printed prototype drives pitch, roll, and combined motion on two motors (video below)</li>
    <li><strong>Status:</strong> independent R&amp;D project, concluded at the 3D-printed prototype stage. The team is keeping its planned segregated wrist (owned by other members) for the 2027 rover.</li>
  </ul>
  <div class="summary-stats">
    <span><strong>1.42×</strong> roll torque multiplier</span>
    <span><strong>0</strong> interference across the full mesh cycle</span>
    <span><strong>3</strong> CAD revisions + <strong>2</strong> prints in ~1 week</span>
    <span><strong>≈ same mass</strong> as current wrist, <strong>~$250</strong> cheaper in motors</span>
  </div>
</div>

<div class="row mt-3 mb-4 justify-content-center">
  <div class="col-md-10 col-12 mb-4 text-center">
    <video controls muted playsinline preload="metadata" poster="{{ '/assets/images/DiffWrist/prototype.jpg' | relative_url }}" class="border rounded" style="width: 100%; height: auto; display: block;">
      <source src="{{ '/assets/images/DiffWrist/prototype_test.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support embedded video.
    </video>
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">3D-printed prototype running pitch and roll on two motors, controlled manually via keyboard</p>
  </div>
</div>

<div style="text-align: center; padding-bottom: 10px">
  <em>Click images to enlarge · click the red headings to expand details</em>
</div>

### 1. Why a Differential
<p>In a differential, two identical motors drive both wrist axes together, so their torques add on whichever axis needs it (so twice the torque is achieved compared to a segregated wrist if the same motors are used). That adds torque margin without heavier motors.</p>

<details class="deep-dive">
<summary>Motors and torque math</summary>
<p>The arm's current wrist has two degrees of freedom but is not a differential. Each axis has its own motor:</p>
<ul>
<li><strong>Pitch:</strong> CubeMars AK60-39 (24 Nm nominal / 72 Nm peak)</li>
<li><strong>Roll:</strong> CubeMars AK45-36 (8 Nm nominal / 24 Nm peak), which the team considers sufficient</li>
</ul>
<ul>
<li><strong>Pitch</strong> (motors turn the same way): τ<sub>pitch</sub> = τ<sub>L</sub> + τ<sub>R</sub></li>
<li><strong>Roll</strong> (motors turn opposite ways): τ<sub>roll</sub> = (τ<sub>L</sub> − τ<sub>R</sub>) × gear ratio</li>
</ul>
<p>Other requirements: low backlash for manipulation accuracy, compact and light, a hollow center for end-effector wiring, and manufacturable in house or by outsourcing. The CubeMars planetary gearboxes already add about 0.2° of backlash that can't be designed out, so the goal is for the wrist gears to add nothing on top of that.</p>
</details>

### 2. The Gear: Trochoidal Crown + Conical Rollers
<p>One gear's teeth are replaced with free-spinning conical rollers. The other gear's teeth are shaped by the exact path those rollers sweep, so the rollers stay in contact with the teeth throughout the mesh, with 3–4 engaged at once. With no gap between roller and tooth, there is theoretically no backlash: about 0–1 arcmin if machined well.</p>

<div class="row mt-3 mb-4 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/DiffWrist/assembly_iso.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; height: auto; display: block; cursor: zoom-in;" alt="Gear set render">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">17-tooth trochoidal crown (gold) between two 12-roller wheels</p>
  </div>
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/DiffWrist/assembly_side.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; height: auto; display: block; cursor: zoom-in;" alt="Gear set side view">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Side view: tapered rollers aimed at the common apex</p>
  </div>
</div>

<details class="deep-dive">
<summary>Key geometry decisions</summary>
<ul>
<li><strong>Common apex:</strong> every cone (the crown, both roller wheels, and every roller) has its tip at one point. That's the only arrangement where the gears roll without slipping along the entire contact line.</li>
<li><strong>Conical rollers instead of cylindrical pins:</strong> a cone whose tip is at the apex rolls along a tooth instead of sliding on it. It also allows preload with a single shim: moving the output gear toward the apex wedges the rollers into both mating gears at once.</li>
<li><strong>17:12 tooth count (1.417× roll multiplier):</strong> adds roll torque margin. The counts are coprime (a "hunting tooth" pair), so every roller eventually meets every tooth, which averages out manufacturing error and spreads wear.</li>
<li><strong>Crown on the output, roller wheels on the motors:</strong> my first layout put crowns on the motors, which forced a steep crown with large, spiky teeth. Swapping the roles (like the spider gear in a car differential) keeps the same roll ratio while making the crown the large, flat gear, and it means only one hard-to-make crown.</li>
<li><strong>Material:</strong> Hertz contact stress calculations showed a 6061 aluminum crown would yield under wrist loads, so the machined crown needs to be hardened steel. Hand calculations also showed the roller pins must be supported at both ends rather than cantilevered.</li>
</ul>
</details>

<details class="deep-dive">
<summary>How the tooth shape was generated</summary>
<p>Published equations exist only for the straight (rack and pinion) version of this gear. The one reference likely to cover the bevel version, a Chinese master's thesis, couldn't be obtained, so I generated the geometry numerically:</p>
<ul>
<li><strong>Envelope method:</strong> the crown is held still while the rollers sweep through every meshing position and are subtracted from a blank, the same way a hob generates a gear. Computed in OpenSCAD; the resulting teeth fit the rollers exactly by construction.</li>
<li><strong>Speed:</strong> the mesh pattern repeats every crown tooth, so one tooth period is swept and copied 17 times, about 15× less work</li>
<li><strong>STEP conversion:</strong> the raw output was a ~32,000-triangle mesh that Fusion couldn't handle, so it was converted (with AI assistance) into a smooth STEP solid for the CAD assembly</li>
<li><strong>Software verification:</strong> zero interference between crown and rollers at 22 positions across a full tooth period, and 3–4 rollers within 0.05 mm of contact at every position</li>
</ul>
<p>With the crown generated, I CAD'd the roller wheels and the rest of the wrist in Fusion 360.</p>
</details>

<p><em>Transparency note: I set the requirements, made the design decisions, and reviewed the results. The generation and verification code in OpenSCAD was written and run with an AI assistant (Claude).</em></p>

---

### 3. Prototyping
<p>In about a week, three CAD revisions and two 3D prints took the wrist from impossible to assemble to easy to assemble and sturdy. Testing traced the remaining backlash to the printed frame flexing under load, not to the gear geometry.</p>

<div class="row mt-3 mb-4 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/DiffWrist/v3_cad.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; height: auto; display: block; cursor: zoom-in;" alt="V3 CAD">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Current design (V3): spider block, sheet-metal motor bracket, carbon-fiber tube interface</p>
  </div>
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/DiffWrist/print2.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; height: auto; display: block; cursor: zoom-in;" alt="Second 3D printed prototype">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">V3 printed prototype</p>
  </div>
</div>

<details class="deep-dive">
<summary>Full iteration log (V1 → V3)</summary>

<p><strong>V1:</strong> the first full wrist around the gear set. It worked on paper but was heavy, wide, not interfaced with the arm, and impossible to assemble, since the top plate couldn't be installed.</p>
<div class="row mt-3 mb-4 justify-content-center">
  <div class="col-md-8 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/DiffWrist/v1_cad.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; height: auto; display: block; cursor: zoom-in;" alt="V1 CAD">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">V1 CAD: motors on either side, crown on the output carrier</p>
  </div>
</div>

<p><strong>V2:</strong> reworked so it could actually be assembled. I widened the top plate, decoupled the motor plate from the roller shaft, and shortened the outboard shafts. The tradeoff was width (235 mm) and a slotted roller shaft that needs FEA to confirm it can carry the torque.</p>
<div class="row mt-3 mb-4 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/DiffWrist/v2_section.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; height: auto; display: block; cursor: zoom-in;" alt="V2 section view">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">V2 section view: bearings, shafts, and the roller/crown mesh</p>
  </div>
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/DiffWrist/v2_front.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; height: auto; display: block; cursor: zoom-in;" alt="V2 front view">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">V2 front view</p>
  </div>
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/DiffWrist/v2_with_ee.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; height: auto; display: block; cursor: zoom-in;" alt="V2 with end effector">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">V2 with the <a href="{{ '/projects/cmr-end-effector/' | relative_url }}">end effector</a> mounted</p>
  </div>
</div>

<p><strong>First 3D print:</strong> it worked. The rollers rolled, the differential behaved correctly, there was little backlash by hand, and the whole print weighed 131 g. Problems found:</p>
<ul>
<li>The gears slid out along their shafts and lifted off the plate unless pressed down</li>
<li>It was only assemblable by bending the differential plate, so a machined version would be impossible to assemble</li>
<li>With the end effector mounted, the differential plate flexed and shifted on the roller shafts, lifting the crown off the rollers. That flex was the main source of the backlash, not the gear geometry; without the end effector, the crown stayed seated.</li>
</ul>
<div class="row mt-3 mb-4 justify-content-center">
  <div class="col-md-8 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/DiffWrist/print1.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; height: auto; display: block; cursor: zoom-in;" alt="First 3D printed prototype">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">First 3D-printed prototype</p>
  </div>
</div>

<p><strong>V3:</strong> redesigned for assembly and manufacturing:</p>
<ul>
<li>The rigid central holder was replaced by a simple spider block that carries the roller wheels</li>
<li>The differential plate was split into three parts so it can be assembled without bending</li>
<li>The motor bracket became a single sheet-metal part for cheap, fast outsourcing</li>
<li>The end-effector interface plate was raised to eliminate friction at the differential plate</li>
<li>The wrist was integrated with the arm's actual carbon-fiber tube from the arm structure CAD</li>
</ul>

<p><strong>Second 3D print (V3):</strong> much sturdier and easy to assemble. The spider block worked as intended, and the differential plate became more rigid now that it's held with metal screws. With the end effector on, a pin through the roller gear carried its full weight. Remaining issues:</p>
<ul>
<li>The top differential plate still flexes under the end effector's weight, lifting the crown and adding backlash</li>
<li>The nuts holding the roller gears together have no room for a tool to hold them, and one fell out during testing</li>
<li>Only some rollers contact the crown at a time, which points to print clearances. A machined crown and real bearings are needed for a meaningful backlash measurement. An early attempt measured 0.286° about the crown axis, but the clearances were too large for that number to be accurate.</li>
</ul>
</details>

---

### 4. Motor Testing
<p>Driven by two motors on moteus controllers, the wrist ran pitch, roll, and combined motions as intended. The motors now hold the gears in position, so the printed base plate isn't needed.</p>
<div class="row mt-3 mb-4 justify-content-center">
  <div class="col-md-8 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/DiffWrist/prototype.jpg' | relative_url }}" class="img-fluid border rounded" style="width: 100%; height: auto; display: block; cursor: zoom-in;" alt="Differential wrist hooked up to motors">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Motor test rig (power and CAN-FD wires daisy chained from left to right; power supply not shown)</p>
  </div>
</div>
<ul>
<li><strong>Flex:</strong> the printed structure is flimsy. The spider block twists when the roller gears are turned by hand, which shows up as backlash, so I can't isolate the backlash from the gear design until the parts are machined.</li>
<li><strong>Motion lag:</strong> movements sometimes kept going after the key was released. This may be the motors hitting a torque or speed limit, which needs investigation since the wrist is essentially unloaded.</li>
<li><strong>Width:</strong> still the biggest drawback. A 1:1 ratio would shrink the crown, and correctly sized outer roller shafts (the printed ones were over twice as long as needed) would make it much narrower.</li>
</ul>

---

### 5. Mass & Cost vs. the Current Wrist
<p>The two wrists come out essentially the same mass. The lighter motors offset the heavy crown, and the differential gets the roll-torque multiplier for less money. The cost is width.</p>
<div class="table-wrap">
<table class="spec-table">
  <tr><th></th><th>Differential wrist</th><th>Current wrist</th></tr>
  <tr><td>Motors</td><td>2 × AK45-36 (680 g)</td><td>AK60-39 + AK45-36 (1090 g)</td></tr>
  <tr><td>Heaviest other part</td><td>Trochoidal crown (251 g)</td><td>-</td></tr>
  <tr><td>Total</td><td>≈ 1343 g (bearings estimated at 50 g)</td><td>≈ 1329 g</td></tr>
  <tr><td>Motor cost</td><td>≈ $400</td><td>≈ $650</td></tr>
</table>
</div>
<p style="font-size: 0.9rem;"><em>Part-by-part CAD masses, excluding motor controllers and their mounts, and fasteners on both.</em></p>

---

### 6. Outcome &amp; What I Learned
<p>The team is keeping its planned segregated wrist for the 2027 rover, so I concluded the project at the 3D-printed prototype stage and am focusing on the <a href="{{ '/projects/cmr-end-effector/' | relative_url }}">end effector</a>.</p>
<ul>
<li><strong>Stiffness matters as much as tooth shape:</strong> nearly all the backlash in the prototypes came from the structure (plate flex, shaft clearance, the spider block twisting), not the gear geometry</li>
<li><strong>Design for assembly early:</strong> V1 couldn't be assembled at all. Splitting the differential plate and switching to a spider block is what made the design buildable.</li>
<li><strong>Gear geometry from first principles:</strong> with no published equations for this gear, I generated the teeth numerically with an envelope method and checked them for interference</li>
<li><strong>Print early:</strong> three CAD revisions and two prints in about a week; every print exposed problems the CAD didn't</li>
<li><strong>Pin down requirements first:</strong> the torque requirement that motivated the extra roll multiplier was never firmly settled. Confirming it up front would have shown whether a simpler 1:1 ratio (smaller crown, narrower wrist) was enough.</li>
</ul>
<details class="deep-dive">
<summary>What a continuation would need</summary>
<ul>
<li>Fix the roller-gear nut retention and the top-plate flex; run FEA on the slotted roller shaft</li>
<li>Machine the crown (hardened steel on the 5-axis mill or outsourced) and fit real bearings</li>
<li>Measure backlash with a 0.2 m stick attached to the EE interfacing plate</li>
</ul>
</details>

<div id="imageModal" class="modal">
  <span class="close-btn">&times;</span>
  <img class="modal-content" id="modalImg" onclick="event.stopPropagation()">
  <div id="caption"></div>
</div>
