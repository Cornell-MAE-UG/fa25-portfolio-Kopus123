---
layout: default
title: Ahmed Arif - Portfolio
permalink: /projects/
---

<!-- Clear any rogue layout floats from the header -->
<div style="clear: both;"></div>

<!-- High-Impact Machined Crimson Centered Gradient Header Area -->
  <div style="margin-bottom: 35px; width: 100%; text-align: center;">
    <h2 style="font-size: 2.8rem; font-weight: 900; margin: 0; text-transform: uppercase; letter-spacing: 2px;
               background: linear-gradient(to right, #dd1c1a, #900c3f, #4a001f);
               -webkit-background-clip: text;
               -webkit-text-fill-color: transparent;">
      Featured Projects
    </h2>
    <div style="height: 4px; width: 100%; background: linear-gradient(to right, #dd1c1a, #900c3f, #4a001f); margin-top: 12px; margin-bottom: 40px; border-radius: 2px;"></div>
  
  
  <!-- Scaled-Up Premium Showcase Block (No loop required) -->
<div class="featured-item" style="margin-bottom: 50px; width: 100%; border: 2px solid #dcdcdc; padding: 25px; border-radius: 18px; background-color: #85e5ff; box-sizing: border-box;">
  
  <!-- Engine Image with Crimson Border -->
  <div style="overflow: hidden; border-radius: 14px; border: 3px solid #900c3f; box-sizing: border-box;">
    <!-- CHANGE THIS IMAGE PATH TO YOUR ACTUAL RENDER -->
    <img src="{{ '/assets/images/RocketEngine/Inj&CC.png' | relative_url }}" alt="LOX/RP-1 Liquid Rocket Engine" style="width: 100%; max-height: 500px; object-fit: cover; display: block;" />
  </div>
  
  <h3 style="font-weight: 800; font-size: 1.75rem; margin-top: 22px; margin-bottom: 10px; color: #111; text-align: left; letter-spacing: -0.5px;">
    Personal LOX/RP-1 Liquid Rocket Engine
  </h3>
  <p style="color: #333; font-size: 1.05rem; line-height: 1.65; margin: 0 0 20px 0; text-align: left;">
    End-to-end geometry design, system integration, and multi-phase ANSYS Fluent transient simulations of a custom liquid rocket engine, featuring cold flow impinging injector analysis and full thermal management profiling.
  </p>

  <!-- Multi-Link Routing Buttons -->
  <style>
    .engine-btn {
      background: #900c3f;
      color: white;
      padding: 10px 18px;
      text-decoration: none;
      border-radius: 6px;
      font-weight: bold;
      font-size: 0.95rem;
      display: inline-block;
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }
    
    .engine-btn:hover {
      transform: translateY(-4px);
      box-shadow: 0 6px 15px rgba(144, 12, 63, 0.4);
      color: white; /* Prevents theme from changing text color on hover */
    }
  </style>

  <div style="display: flex; justify-content: center; gap: 15px; flex-wrap: wrap;">
    <a href="{{ '/projects/2026-Rocket-Engine/injector/' | relative_url }}" class="engine-btn">
      Injector Design and CFD ➔
    </a>
    <a href="{{ '/projects/2026-Rocket-Engine/cc-nozzle/' | relative_url }}" class="engine-btn">
      CC & Nozzle Design and CFD ➔
    </a>
    <a href="{{ '/projects/2026-Rocket-Engine/full-assembly/' | relative_url }}" class="engine-btn">
      Full System Assembly ➔
    </a>
  </div>

</div>
</div>

<hr style="margin: 40px 0; border: none; border-top: 1px solid #ddd; clear: both;">

<!-- 2. FOUNDATIONAL PROJECTS (BOTTOM SECTION) -->
<div style="width: 100%; display: block;">
  <h2 style="font-weight: bold; margin-bottom: 20px; color: #555; text-align: left;">Foundational Projects & Archives</h2>
  
  <div class="gallery-container">
    <div class="project-gallery">
      {% for project in site.projects %}
        {% unless project.featured == true %}
          <div class="gallery-item">
            <a href="{{ project.url | relative_url }}">
              <img src="{{ project.image | relative_url }}" alt="{{ project.title }}" />
              <p>{{ project.title }}</p>
            </a>
          </div>
        {% endunless %}
      {% endfor %}
    </div>
  </div>
</div>