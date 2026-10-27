---
layout: project
title: Cornell Mars Rover End Effector
description: Redesign, prototyping, and hardware validation for the 6-DOF arm end effector.
permalink: /projects/cmr-end-effector/
status: current
image: /assets/images/EndEffector/EndEffector.jpg
technologies: [Autodesk Fusion 360, Autodesk Inventor & Vault, Ansys Mechancial (FEA), Silicone Molding, 3D Printing (Bambu Lab Studio), Arduino]
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
    <li><strong>Problem:</strong> last year's end effector had a key clicker that broke, grippers too soft for heavy objects, and parts that failed on impact</li>
    <li><strong>What I did:</strong> redesigned the grippers (skeleton-reinforced molded silicone), added laser aiming mounts and claw hard stops, designed the new motor interface, and evaluated key-clicker concepts down to a linear actuator</li>
    <li><strong>Result:</strong> the prototype picks up a 5.94 kg cache (above the 5 kg competition limit), plus a mallet, hammer, and power tool</li>
    <li><strong>Status:</strong> finishing CAD (actuator mount, top plate, TOF sensor), then testing on the arm</li>
  </ul>
  <div class="summary-stats">
    <span><strong>5.94 kg</strong> cache lifted (5 kg required)</span>
    <span><strong>5</strong> competition-style objects tested</span>
    <span><strong>2</strong> silicone grades compared</span>
    <span><strong>~720 g</strong> total mass</span>
  </div>
</div>

<div style="text-align: center; padding-bottom: 10px">
  <em>Click images to enlarge · click the red headings to expand details</em>
</div>

### 0. Project Requirements
<p>The End Effector serves two University Rover Challenge (URC) missions, Equipment Servicing (ESM) and Delivery (ERDM). It must grasp objects up to 5 kg, open boxes and drawers, and type autonomously.</p>
<details class="deep-dive">
<summary>Relevant 2027 URC rules</summary>
<ul>
<li> "Objects [to carry] may consist of small lightweight hand tools or instruments, rocks, or supply containers. Objects may be up to <strong>5 kg in mass</strong> … All objects … graspable feature, no greater than <strong>7.5 cm diameter"</strong></li>
<li>"Open boxes with hinged lids such as toolboxes."</li>
<li>“The cache [to pick up and move into lander] will have a handle at least 10 cm long and not more than 5 cm in diameter. The cache will weigh less than 5 kg."</li>
<li>"Open a drawer on the lander. Insert the cache into a tight-fitting space in the drawer, and close the drawer."</li>
<li><strong>Autonomous typing, key insert, picking up a hammer autonomously</strong></li>
</ul>
</details>

### 1. Problems with Last Year's End Effector
<p>I started the year by listing what went wrong with last year's design and brainstorming solutions for each:</p>
<ul>
<li><strong>The key clicker broke</strong>, and its linear servo may have been too compliant</li>
<li><strong>The silicone grippers were too compliant</strong> to hold heavy objects firmly</li>
<li><strong>Parts failed on impact</strong>; options considered were rubber isolators between mounted parts or sacrificial plastic housings</li>
<li><strong>The hook was too close</strong> to the end effector to pick anything up</li>
<li><strong>The rack and pinion meshed poorly</strong>, likely because the rack was imperial while the rest of the assembly was metric</li>
</ul>

### 2. Key Engineering Features & Mechanisms
<ul>
<li>Rack and Pinion Mechanism allows for constant gripping force of a variety of objects within a 9 cm size range</li>
<li>Utilizes a Gobilda 5 turn high torque servo</li>
<li>Sheet Metal Fabrication</li>
<li>Lasers used for precise grasping</li>
<li>Total mass of about 720 g</li>
</ul>

<div class="row mt-3 mb-5 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/ClickerStowed.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: contain; background: #2e3440; display: block; cursor: zoom-in;" alt="End Effector CAD">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">End Effector CAD (shown with the since-scrapped folding key clicker)</p>
  </div>
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/RP.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: contain; background: #fff; display: block; cursor: zoom-in;" alt="Rack and Pinion CAD">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Rack and Pinion (CAD)</p>
  </div>
  <div class="col-md-6 col-12 mb-4 text-center" style = "">
      <img src="{{ '/assets/images/EndEffector/RealRP.jpg' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Rack and Pinion">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Rack and Pinion Mechanism</p>
  </div>
</div>

---

### 3. Skeleton-Reinforced Silicone Grippers
<p>A 3D-printed "skeleton" screws onto each claw, and silicone is molded around it. This caps the silicone at 0.8–1 cm thick so the grip stays firm but grippy, with no screws or joints in the silicone that could tear.</p>
<details class="deep-dive">
<summary>Design history and molding</summary>
<p>Comparing previous years' end effectors showed how silicone thickness drives grip stiffness:</p>
<ul>
<li>One design had no backing at all, with over 2 cm of 0A silicone, which made it too squishy for the delivery mission</li>
<li>Another had a rigid plate at the back of the gripper, leaving about 1.3 cm of silicone at the gripping face</li>
</ul>
<ul>
<li>I designed a mold for the grippers. The first mold left a very thin clearance at the flat bottom, so the second mold has a larger clearance.</li>
<li>Unlike the old grippers, the new ones don't extend into the metal walls of the claw. That didn't turn out to matter in testing, and they're easy to remold if it does.</li>
</ul>
</details>

<div class="row mt-3 mb-5 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/Claws.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: contain; background: #fff; display: block; cursor: zoom-in;" alt="Skeleton grippers CAD">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Gripper skeletons (gray) inside the claws</p>
  </div>
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/RealClaws.jpg' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Silicone grippers">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Silicone Grippers with 3D Printed Skeleton</p>
  </div>
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/GripperCloseup.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: contain; background: #fff; display: block; cursor: zoom-in;" alt="Molded silicone gripper on the claw">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Molded silicone gripper on the claw</p>
  </div>
</div>

---

### 4. Laser Mounts, Side Plates & Motor Interface
<p>Two lasers converge just short of the claw tips to show the operator exactly where the claws will close. Hard stops on the side plates keep the claws from rotating when closed.</p>
<details class="deep-dive">
<summary>Mount iterations, side plates, and motor interface</summary>
<ul>
<li><strong>Laser mounts:</strong> the first design screws into two existing holes on the side plate and holds the laser in a slot. Screws through a flange on the slot clamp the laser in place. I chose a clamp over a set screw because a set screw could easily break a precision laser.
  <ul>
    <li>The PETG mount flexed a lot while being screwed in, and clamping cracked the outer flange (it still held). The second side's mount was made thicker; future versions need more flange material.</li>
    <li>Both lasers are mounted and point toward the center, where the claws meet at the top</li>
    <li><strong>Internal laser mount:</strong> a long beam that screws into the servo mount, inside the hollow space of the EE housing, and extends to either side. Each laser is held at an angle by a screwed clamp (again, not a set screw), aimed so the two beams converge near the claw tips but not at the very end. For now, the lasers shine through holes drilled in the top plate; the plate will be redesigned with the holes built in.</li>
  </ul>
</li>
<li><strong>Side plates:</strong> reprinted with the correct hole patterns (the two sides differ). Each now has a small extrusion where the claws meet the wall, acting as a hard stop so the claws stop exactly when they close instead of rotating slightly. One rack was a bit longer than the other, so I trimmed the stop on that side by hand.</li>
<li><strong>CubeMars interface plate:</strong> designed to connect the EE to the new CubeMars motor used in the arm structure, via the motor's six screws and the existing sheet-metal adapter. I'm waiting for the motors before printing, and later plan to replace both plates with one interfaced sheet-metal part to cut weight and failure points.</li>
</ul>
</details>

<div class="row mt-3 mb-5 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/LaserMounts.jpg' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Laser mounts">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">First-generation laser mounts</p>
  </div>
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/LaserBeamCAD.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: contain; background: #fff; display: block; cursor: zoom-in;" alt="Internal laser mount (CAD, top-down)">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Internal laser mount (CAD)</p>
  </div>
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/LaserBeamReal.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: contain; background: #fff; display: block; cursor: zoom-in;" alt="Internal laser mount installed on the servo mount">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Internal laser mount installed on the servo mount</p>
  </div>
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/LasersOn.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: contain; background: #fff; display: block; cursor: zoom-in;" alt="Lasers converging near the claw tips">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Lasers converging near the claw tips</p>
  </div>
</div>

---

### 5. Key Clicker
<p>After evaluating three concepts, I selected an Actuonix L16 linear actuator (50 mm stroke) on a sheet-metal side mount for autonomous typing. It's simple and rigid, and the arm keeps all its DOF.</p>
<div class="row mt-3 mb-5 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/LAMount.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: contain; background: #fff; display: block; cursor: zoom-in;" alt="Linear actuator on the side of the EE (earlier printed-bracket version)">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Linear actuator on the side of the EE (earlier printed-bracket version)</p>
  </div>
</div>
<details class="deep-dive">
<summary>Concepts considered, including a folding cable-driven clicker</summary>
<ul>
<li><strong>Push-pull solenoid:</strong> simple on/off control, but short stroke and weak. Its speed is no advantage, since the competition keyboard doesn't repeat keys when held.</li>
<li><strong>Rod in the toolkit for the arm to hold:</strong> at PDR, the team pointed out the arm loses a DOF this way, and the current IK likely can't reach every key</li>
<li><strong>Claw-tip folding clicker:</strong> two bars that stow stacked on each other and extend until collinear, driven by cables over pulleys from a small motor. I added a simple stick clicker as a placeholder, researched underactuated linkages, and worked out a preliminary design with my lead.
  <ul>
    <li>Motor: I ruled out a worm-gear motor as too bulky. My main candidate was a low-RPM gimbal motor, only 15 mm thick and 32 mm in diameter, small enough to fit on the EE face.</li>
    <li>Concern: the fully extended collinear position is an unstable equilibrium, so pressing keys could fold it, letting the claws touch the keyboard</li>
    <li>Friction at the joints could lock it up. Cables would be clamped to the pulleys, with thrust washers between bars and pulleys and bushings on the shafts.</li>
  </ul>
</li>
</ul>
<div class="row mt-3 mb-5 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/ClickerExtended.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: contain; background: #fff; display: block; cursor: zoom-in;" alt="Folding clicker extended (bars collinear)">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Folding clicker extended (bars collinear)</p>
  </div>
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/ClickerStowed.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: contain; background: #fff; display: block; cursor: zoom-in;" alt="Folding clicker partially folded">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Folding clicker partially folded</p>
  </div>
</div>
<p><strong>Decision:</strong> I scrapped the folding clicker as too complicated for little real benefit, in favor of the linear actuator. Its mount was first CAD'd as a printed bracket and has since been redesigned as a sheet-metal part.</p>
</details>

---

### 6. Testing
<p>Every test object was picked up, including a cache heavier than the competition limit. The silicone grade changed which orientations gripped best.</p>
<p style="font-size: 0.95rem;">Setup: the EE ran on a power supply and an Arduino, and a Python script mapped the left and right arrow keys to close and open the claws.</p>
<div class="table-wrap">
<table class="spec-table">
  <tr><th>Object</th><th>Grip location size</th></tr>
  <tr><td>Cache (5.34 kg)</td><td>1.4 cm handle</td></tr>
  <tr><td>Cache (5.94 kg, heavier than required)</td><td>1.05 cm handle</td></tr>
  <tr><td>Mallet</td><td>2.8 cm handle, 6.1 cm head</td></tr>
  <tr><td>Milwaukee cordless rivet tool</td><td>5.1 cm handle, 8.1 cm head, 0.2 × 3.1 cm clip</td></tr>
  <tr><td>Hammer</td><td>3.2 cm handle, 3 cm head, 1.2 cm claw</td></tr>
</table>
</div>
<ul>
<li>All objects were picked up easily. The lighter cache only fell after vigorous shaking, and the hammer, gripped at the end of its handle, rotated to about 45°.</li>
<li>The silicone deforms quite a bit under load, but the deformation lets the metal housing help retain the cache</li>
<li>Comparing silicone grades: 15A grips better with the EE horizontal, and 0A grips better pointed down, where its extra deformation lets the metal claws hold the object. Overall I think 0A is better because of its higher deformation, and tests that better reflect the URC environment.</li>
</ul>

<div class="row mt-3 mb-5 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/test1-3.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">High deformation can be seen</p>
  </div>
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/test1-4.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Mallet Picked up at End</p>
  </div>
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/test1-7.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Power Tool</p>
  </div>
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/test1-8.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Hammer Picked up at End</p>
  </div>
</div>

---

### 7. Design Reviews & Next Steps
<ul>
<li><strong>CDR feedback:</strong> a time-of-flight (TOF) sensor would likely work better than lasers for precise grasping, since it reports back actual distance (good for the new key insert task). Extrapolating distance from lasers is much more difficult. I plan to switch to a TOF sensor.</li>
<li>Finish the EE CAD (sheet-metal linear actuator mount, redesigned top plate with laser holes, CubeMars interface plate), then test the EE extensively on the arm</li>
<li>Find the optimal skeleton volume and silicone grade for the best all-round grip, including tests against non-skeleton grippers and different skeleton sizes</li>
<li>Add camera mounts and interfacing plate with current wrist (already interfaced with my differential wrist)</li>
<li>Continue rapid prototyping by 3D printing so testing, rather than analysis alone, confirms function</li>
<li>Related: I'm also developing a <a href="{{ '/projects/cmr-diff-wrist/' | relative_url }}">roller-crown differential wrist</a> for the arm</li>
</ul>

<div id="imageModal" class="modal">
  <span class="close-btn">&times;</span>
  <img class="modal-content" id="modalImg" onclick="event.stopPropagation()">
  <div id="caption"></div>
</div>
