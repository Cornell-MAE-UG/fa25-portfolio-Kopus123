---
layout: project
title: Cornell Mars Rover End Effector
description: Redesign, prototyping, and hardware validation for the 6-DOF arm end effector.
permalink: /projects/cmr-end-effector/
status: current
image: /assets/images/EndEffector/EndEffector.jpg
technologies: [Autodesk Fusion 360, Autodesk Inventor & Vault, Ansys Mechancial (FEA), Silicone Molding, 3D Printing (Bambu Lab Studio)]
current: true
---

<div style="clear: both;"></div>

<div style="text-align: center; padding-bottom: 0px">
  <em>Click to enlarge images</em>
</div>

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

### 0. Project Requirements
<p>The End Effector will participate in 2 missions for the University Rover Challenge: The Equipment Servicing mission (ESM) and the Delivery Mission (ERDM). Relevant rules from the 2027 challenge are below:</p>
<ul>
<li> "Objects [to carry] may consist of small lightweight hand tools or instruments, rocks, or supply containers. Objects may be up to <strong>5 kg in mass</strong> … All objects … graspable feature, no greater than <strong>7.5 cm diameter"</strong></li>
<li>"Open boxes with hinged lids such as toolboxes."</li>
<li>“The cache [to pick up and move into lander] will have a handle at least 10 cm long and not more than 5 cm in diameter. The cache will weigh less than 5 kg."</li>
<li>"Open a drawer on the lander. Insert the cache into a tight-fitting space in the drawer, and close the drawer."</li>
<li><strong>Autonomous typing, key insert, picking up a hammer autonomously</strong></li>
</ul>


### 1. Key Engineering Features & Mechanisms
<ul>
<li>Rack and Pinion Mechanism allows for constant gripping force of a variety of objects within a 9 cm size range</li>
<li>Utilizes a Gobilda 5 turn high torque servo</li>
<li>Sheet Metal Fabrication</li>
<li>Lasers used for precise grasping</li>
</ul>

<div class="row mt-3 mb-5 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center" style = "">
      <img src="{{ '/assets/images/EndEffector/RealRP.jpg' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Rack and Pinion">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Rack and Pinion Mechanism</p>
  </div>
</div>

<div class="row mt-3 mb-5 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/LaserMounts.jpg' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Rack and Pinion">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Laser Mounts (Under Redesign for Compactness)</p>
  </div>
</div>


<li>Skeleton-backed (3D printed) silicone grippers allow for more rigidity while grasping objects (which increases grip strength compared to previous fully silicone grips) while retaining a high coefficient of friction to keep objects held</li>
<div class="row mt-3 mb-5 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/RealClaws.jpg' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;" alt="Rack and Pinion">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Silicone Grippers with 3D Printed Skeleton</p>
  </div>
</div>

---
### 2. Modification
<p>My design this year modifies last year's design.</p>
<li>The silicone skeleton, new laser mounts, new keyclicker design (for autonomous typing), and camera mounts are part of my project currently</li>
<li>There likely will be more components to add to the End Effector as the semester progresses and more testing is done</li>

---

### 3. Testing
<p>A lot of testing was conducted (and is still being conducted) to ensure all changed components work as intended</p>
<p>In order to test the components, I powered the End Effector with a power supply and an arduino board, and programmed the left and right keys on my keyboard to open and close the claws</p>
<ul>
<li>I have so far tested with 0A and 15A silicone grades, but have only recorded tests with 0A</li>
<li>The most important test I conducted was picking up a cache (5.94 kg, so a bit heavier then needed)
<ul><li>It can be seen that the silicone deforms quite a bit, but the cache is retained within the claws due to deformation</li>
<li>The 15A grade silicone did not deform enough, so the grip strength was not high enough to keep the cache in when I shook it (still a very vigorous test)</li>
</ul>

<div class="row mt-3 mb-5 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/test1-3.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">High deformation can be seen</p>
  </div>
</div>

<li>I also tested various other objects, such as a hammer, mallet, and Milwaukee cordless rivet power tool, all which were held by the End Effector, though the hammers did rotate a bit when picked up from the edge of the handle (extreme case)</li>
</li>
<div class="row mt-3 mb-5 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/test1-4.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Mallet Picked up at End</p>
  </div>
</div>
<div class="row mt-3 mb-5 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/test1-7.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Power Tool</p>
  </div>
</div>
<div class="row mt-3 mb-5 justify-content-center">
  <div class="col-md-6 col-12 mb-4 text-center">
      <img src="{{ '/assets/images/EndEffector/test1-8.png' | relative_url }}" class="img-fluid border rounded" style="width: 100%; aspect-ratio: 4/3; object-fit: cover; display: block; cursor: zoom-in;">
    <p style="text-align: center; font-size: 0.9rem; padding: 10px; margin: 0; background: #f9f9f9;">Hammer Picked up at End</p>
  </div>
</div>
</ul>

<div id="imageModal" class="modal">
  <span class="close-btn">&times;</span>
  <img class="modal-content" id="modalImg" onclick="event.stopPropagation()">
  <div id="caption"></div>
</div>


### 4. Future Improvements
<ul>
<li>Through my testing, I want to find the optimal skeleton volume and silicone grade for the End Effector to have the best all round capability
<ul><li>Currenlty, the 0A grade is better at picking up objects when the EE is pointed down, and when deformity allows for the metal housing to hold in objects</li>
<li>The 15A grade is better at picking up objects when the EE is horizontal</li>
<li>I will in the future test different size skeletons as well</li>
</ul>
<li>I am currenlty designing a laser mount that is contained inside the empty space in the EE housing (between the rack and pinion), and to power the lasers with a small circular battery instead of a power supply</li>
<li>Camera mounts will also be made</li>
<li>I will continue to rapidly prototype parts by 3D printing to ensure testing is the main factor for function confirmation rather than analysis</li>