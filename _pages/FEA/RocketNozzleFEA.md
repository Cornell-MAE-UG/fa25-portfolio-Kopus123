---
layout: project
title: Rocket Nozzle FEA
permalink: /analysis/RocketNozzleFEA/
description: "Thermal-Structural coupled analysis of a rocket nozzle."
technologies: [ANSYS Workbench, ANSYS Mechanical (Static Structural), Spaceclaim]
---


<div style="clear: both;"></div>

<div style="position: relative; top: -50px; margin-bottom: -25px;">
  <strong>Objective:</strong> To validate the structural integrity of the F-1 rocket engine nozzle (mid and lower sections) used in NASA's Saturn V rocket during steady-state combustion.
</div>


### 1. Engineering Data
**Materials:** The main part of the nozzle uses 300 series stainless steel, and the bolt and nut holding the mid and lower nozzle together use A-286 steel.

### 2. Geometry
In order to analyze the rocket nozzle more easily, only one slice of the whole nozzle was taken. Also, in order to simplify hand calculations to verify the ANSYS solver's solution, the shape was simplified into a slice of a cone, rather than a converging-diverging nozzle. The reason that this simplifies the geometry because it allows for the hoop stress formula (&sigma; = Pr/t) to be used. Though this does greatly simplify the calculations, there is little difference in the answers of the cone and the nozzle.

<div style="text-align: center; margin: 25px 0;">
<img src="{{ '/assets/images/RocketNozzleSlice.jpg' | relative_url }}" 
     style="width: 65%; max-width: 500px; border-radius: 6px; border: 1px solid #ddd; box-shadow: 0 2px 10px rgba(0,0,0,0.05);">
<p style="margin-top: 8px; font-size: 0.85rem; opacity: 0.8;">
    <i>Middle section of rocket nozzle slice used for solving the model</i>
</p>
</div>

### 3. Model & Mesh

After generating the auto-generated mesh by ANSYS, I added a few changes. The first change was adding a specific sizing to the nozzle and the bolt & nut, with the bolt & nut having a mesh with an element size that is roughly three times finer than the nozzle body. The other change that I made was to add a hex dominant method to the entire geometry, as a cleaner mesh is achieved in this case. The mesh had a total of 26134 nodes and 4255 elements. Additionally, a frictionless boundary condition was added where the mid and top parts of the nozzle meet near the bolt to conduct a more rigorous test of the model. The force from the regen channel was also included in the analysis.

<div style="text-align: center; margin: 25px 0;">
<img src="{{ '/assets/images/RocketNozzleSliceMesh.jpg' | relative_url }}" 
     style="width: 65%; max-width: 500px; border-radius: 6px; border: 1px solid #ddd; box-shadow: 0 2px 10px rgba(0,0,0,0.05);">
<p style="margin-top: 8px; font-size: 0.85rem; opacity: 0.8;">
    <i>Middle section mesh of the rocket nozzle slice</i>
</p>
</div>

### 4. Results
For the analysis, I split the loading stages of the nozzle into three steps. The first step is the initial condition (including bolt pretension), the second having the regen channels flow with fluid as well as the pressure increasing in the nozzle (82.9 kPa at the bottom of the nozzle and 329.02 kPa at the top), and the third step adding in the temperature increase of 350 degrees celsius.  All values were determined by data from the engine's actual use. The results of the deformation, gap at the regen channel, and von mises stress distribution are shown below.
<br>
The results revealed that after the third time step, there might come to be a gap that is too big near the regen channel, which may cause some problems, as fuel could leak or could mix with oxidizer. However, that result is likely because of the frictionless boundary condition, and in a further analysis that would need to be refined, because, after all, the F-1 engine did see flight and successfully sent astronauts to the moon.
<div class="row g-3" style="margin: 20px 0;">
  <div class="col-4 text-center">
    <img src="{{ '/assets/images/TotalDeft1.jpg' | relative_url }}" class="img-fluid border rounded" style="height: 250px; width: 100%; object-fit: cover;">
    <p style="margin-top: 8px; font-size: 0.85rem; opacity: 0.8;"><i>Total Deformation at t=1</i></p>
  </div>
  <div class="col-4 text-center">
    <img src="{{ '/assets/images/Totaldeft2.jpg' | relative_url }}" class="img-fluid border rounded" style="height: 250px; width: 100%; object-fit: cover;">
    <p style="margin-top: 8px; font-size: 0.85rem; opacity: 0.8;"><i>Total Deformation at t=2</i></p>
  </div>
  <div class="col-4 text-center">
    <img src="{{ '/assets/images/TotalDeft3.jpg' | relative_url }}" class="img-fluid border rounded" style="height: 250px; width: 100%; object-fit: cover;">
    <p style="margin-top: 8px; font-size: 0.85rem; opacity: 0.8;"><i>Total Deformation at t=3</i></p>
  </div>
</div>

<div class="row g-3" style="margin: 20px 0;">
  <div class="col-4 text-center">
    <img src="{{ '/assets/images/gapt1.jpg' | relative_url }}" class="img-fluid border rounded shadow-sm" style="height: 250px; width: 100%; object-fit: cover;">
    <p style="margin-top: 8px; font-size: 0.85rem; opacity: 0.8;"><i>Gap at t=1</i></p>
  </div>
  <div class="col-4 text-center">
    <img src="{{ '/assets/images/gapt2.jpg' | relative_url }}" class="img-fluid border rounded shadow-sm" style="height: 250px; width: 100%; object-fit: cover;">
    <p style="margin-top: 8px; font-size: 0.85rem; opacity: 0.8;"><i>Gap at t=2</i></p>
  </div>
  <div class="col-4 text-center">
    <img src="{{ '/assets/images/gapt3.jpg' | relative_url }}" class="img-fluid border rounded shadow-sm" style="height: 250px; width: 100%; object-fit: cover;">
    <p style="margin-top: 8px; font-size: 0.85rem; opacity: 0.8;"><i>Gap at t=3</i></p>
  </div>
</div>

<div style="text-align: center; margin: 40px 0;">
<img src="{{ '/assets/images/VonMisesStress.jpg' | relative_url }}" 
     style="width: 50%; max-width: 700px; border-radius: 8px; border: 1px solid #eee; box-shadow: 0 4px 15px rgba(0,0,0,0.1);">
<p style="margin-top: 12px; font-size: 0.9rem; opacity: 0.8;">
    <i>Von Mises stress distribution</i>
</p>
</div>

<div id="imageModal" class="modal">
  <span class="close-btn">&times;</span>
  <img class="modal-content" id="modalImg" onclick="event.stopPropagation()">
  <div id="caption"></div>
</div>

<style>
/* The Modal Background */
.modal {
  display: none; /* Hidden by default */
  position: fixed; 
  z-index: 9999; /* Sit on top of everything */
  padding-top: 0; 
  left: 0;
  top: 0;
  width: 100%; 
  height: 100%; 
  overflow: auto; 
  background-color: rgb(0,0,0); /* Fallback color */
  background-color: rgba(0,0,0,0.9); /* Black w/ opacity */
  justify-content: center;
  align-items: center;
}

/* The Image Box */
.modal-content {
  margin: auto;
  display: block;
  width: auto;
  max-width: 90%;
  max-height: 90vh;
  border-radius: 5px;
  box-shadow: 0 0 20px rgba(255,255,255,0.2);
}

/* Animation */
.modal-content {  
  animation-name: zoom;
  animation-duration: 0.3s;
}

@keyframes zoom {
  from {transform:scale(0)} 
  to {transform:scale(1)}
}

/* The Close Button */
.close-btn {
  position: absolute;
  top: 25px;
  right: 35px;
  color: #f1f1f1;
  font-size: 40px;
  font-weight: bold;
  transition: 0.3s;
  cursor: pointer;
}

.close-btn:hover,
.close-btn:focus {
  color: #bbb;
  text-decoration: none;
  cursor: pointer;
}

/* Add a magnifying glass cursor to images so users know to click */
img {
  cursor: zoom-in;
}
/* Force the enlarged image to have a normal arrow cursor */
#modalImg {
  cursor: default !important;
}
</style>

<script>
// Get the elements
var modal = document.getElementById("imageModal");
var modalImg = document.getElementById("modalImg");
var span = document.getElementsByClassName("close-btn")[0];

// 1. OPEN LOGIC: Find all images and make them clickable
var images = document.querySelectorAll('img');
images.forEach(function(img) {
  // Skip profile pic and the modal image itself
  if (img.classList.contains('profile-image')) return;
  if (img.id === 'modalImg') return;

  img.onclick = function(){
    modal.style.display = "flex"; // Shows the modal
    modalImg.src = this.src;      // Puts the image inside
  }
});

// 2. CLOSE LOGIC: Click the X to close
span.onclick = function() { 
  modal.style.display = "none";
}

// 3. SMART BACKGROUND CLOSE
// This detects exactly what you clicked.
modal.onclick = function(event) {
  // If you clicked the black background (modal), CLOSE it.
  if (event.target === modal) {
    modal.style.display = "none";
  }
  // If you clicked the image (event.target === modalImg), do NOTHING.
}
</script>