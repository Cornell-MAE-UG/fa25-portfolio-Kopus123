---
layout: project
title: Adjustable Netting Post (MAE 2250, updated)
description: Telescoping trellis post for efficient insect netting management during vineyard harvest
image: /assets/images/SLF.jpg
---

## Table of Contents

- [Client Pitch](#client-pitch)
- [Functional Prototype](#functional-prototype)

---

## Client Pitch

**Team:** FABulous engineers who make lanternflies DI  
**Clients:** Cornell CALS Extension / E&J Gallo Winery / National Grape

### Problem Statement

Research has shown that over-the-row insect netting can reduce SLF population by up to 99.8%. This netting has a 6×1.8mm mesh and must be secured on the bottom and sides of the row. This solution is not perfect, however. The netting must be removed before harvest and reapplied after. Not only is this process labor-intensive, it leaves the grape plants unprotected before and during harvest. It must also be noted that pesticides cannot be used for a certain interval before harvest. There are other styles of netting — such as side netting — which allow hand-harvesting without complete removal of the netting. However, side netting is not as effective at protecting against SLF in comparison to over-the-row netting.

### Impact

Despite its potential effectiveness at protecting grape vines, very fine mesh has seen limited use. Large-scale vineyards are unable to efficiently use small-scale, drape-over-the-vine nets because of the significant time and labor required in installation and removal. If this process is made more efficient, more vineyards could use this fine mesh to prevent lanternflies from accessing the vines.

### Proposed Direction

**Concept: Adjustable Netting Post**

**What it is:** The Adjustable Netting Post is a method of efficiently raising and lowering over-the-row insect netting during harvest. It is a telescoping post which can extend roughly 4 feet, allowing for over-the-row netting to be raised before harvest.

**How it would be used:** Each modified trellis post is extendable. Over-the-row netting is then installed over the trellis. When the vines are ready for harvest, workers can extend the poles nearest to them, raising the netting. They can then harvest grapes and lower the Adjustable Netting Posts behind them.

**Why it's better than the status quo:**
- Eliminates need to fully uninstall and reinstall SLF nets before and after harvest
- Eliminates period of vulnerability to SLF damage while nets are down
- Can eventually be adapted to work for machine harvesting as well

**End-of-semester proof-of-concept:** Full-sized telescoping post + net and demonstrated functionality.

### Key Risks / Unknowns

**Tangle Risk** — Nets can tangle in the vines or on the post itself, damaging vines and increasing difficulty of operation. *Test:* Trials removing the nets from various bushes.

**Ground-Net Gap** — Attaching the net to the bottom of the post may create a gap between the net and the ground, lowering the system's effectiveness. *Test:* Minimize gap + do research.

**Post Accessibility** — Inability to easily access the posts for raising/lowering would defeat the system's purpose of saving labor. *Test:* Measure time required to raise/lower post.

### Questions for the Client

1. How often do you use hand harvesting (as opposed to using harvesters)?  
   *Decision affected:* Focus on hand harvesting in our design.
2. At what height on the vines do your variety of grapes grow?  
   *Decision affected:* Height post needs to extend to.
3. If you utilize netting, what is your typical process for installation/removal?  
   *Decision affected:* Overall design direction.

### References

- Leach, Heather & Mariani, Tom & Centinari, Michela & Urban, Julie. (2023). Evaluating integrated pest management tactics for spotted lanternfly management in vineyards. *Pest Management Science*, 79. [doi:10.1002/ps.7528](https://doi.org/10.1002/ps.7528)
- [Spotted Lanternfly Management in Vineyards — Penn State Extension](https://extension.psu.edu/spotted-lanternfly-management-in-vineyards)
- [Cornell Research on SLF Netting — Facebook Video](https://www.facebook.com/Cornell/videos/cornell-research-led-by-gavin-sacks-is-helping-ej-gallo-winery-in-modesto-califo/1700985444195723/)

---

## Functional Prototype

**Group R2**

### Purpose

The functional prototype tests the core telescoping mechanism of the Adjustable Netting Post. The goal was to validate that the pole can extend and retract smoothly, lock securely at full height, and require a reasonable amount of force to operate — all critical requirements for vineyard use.

### Bill of Materials

| Name | Description | Specs | Fabrication Details |
|------|-------------|-------|---------------------|
| Outer Tube | Cardboard tube from McMaster package | OD: 106mm, ID: 104mm, Length: 1.96m | Cut a 54″ slot ~1″ thick; cut a J at the top; cut hole in back for handle; attach pulley |
| Inner Tube | Cardboard tube from McMaster package | OD: 81mm, ID: 79mm, Length: 1.96m | Cut 2 holes opposite each other for handle to pass through at bottom |
| Pulley | 3D-printed PLA pulley for lifting & locking mechanism (outer casing, side supports, center axis, pulley wheel) | ~60×60mm, pulley diameter ~20mm | Side supports epoxied to outer tube; screw attaches center axis to outer tube |
| Rope | Nylon thread for pulley (scavenged) | Arbitrary length (≥190cm) | Tie to handle, slide through pulley |
| Handle | Wooden handle for raising & lowering | 95×81mm rectangle + 105×20mm handle | Slides through outer tube hole into inner tube; thick section fits inner tube slots; thin section sticks out through slot |

### Moving Components Sketches

<img src="{{ '/assets/images/MAE2250/InitialSketch.png' | relative_url }}" width="100%" alt="Moving Components Sketch">

### Initial CAD

**Extended and locked into place:**

<img src="{{ '/assets/images/MAE2250/ExtendedCAD.png' | relative_url }}" width="80%" alt="Extended and Locked CAD">

**Unextended:**

<img src="{{ '/assets/images/MAE2250/UnextendedCAD.png' | relative_url }}" width="80%" alt="Unextended CAD">

### Assembly Documentation

**Step 1: Attach pulley body/wheel to top of base tube**

Install the pulley pin and pulley wheel/body onto the top of the outer tube.

<img src="{{ '/assets/images/MAE2250/PulleyInstalling.png' | relative_url }}" width="40%" alt="Assembly Step 1">

**Step 2: Slide inner tube into base tube**

<img src="{{ '/assets/images/MAE2250/OuterTube.png' | relative_url }}" width="40%" alt="Outer Tube">

<img src="{{ '/assets/images/MAE2250/InnerTube.png' | relative_url }}" width="40%" alt="Inner Tube">

**Step 3: Insert pin handle through the outer tube into the inner tube**

<div style="display: flex; justify-content: center; gap: 20px;">
  <img src="{{ '/assets/images/MAE2250/Handle.png' | relative_url }}" style="width: 30%;" alt="Pin Handle">
  <img src="{{ '/assets/images/MAE2250/InnerTube.png' | relative_url }}" style="width: 30%;" alt="Pin Handle Slot">
  <img src="{{ '/assets/images/MAE2250/What.png' | relative_url }}" width="40%" alt="Result">
</div>
**Step 4: Tie rope around pin handle, run through mounted pulley**

<div style="display: flex; justify-content: center;align-items: center; gap: 20px;">
  <img src="{{ '/assets/images/MAE2250/PulleyString.png' | relative_url }}" style="width: 30%;" alt="Rope setup">
  <img src="{{ '/assets/images/MAE2250/ExtendedIRL.png' | relative_url }}" style="width: 30%;" alt="Pulley close-up">
</div>

**Step 5: Check that the pole can extend**

<img src="{{ '/assets/images/MAE2250/Tower.png' | relative_url }}" width="40%" alt="Pole extended">

### Test Documentation

#### Tube Deflection Test
*Testing alignment between the two tubes to prevent damage from torquing.*

- **Description:** Inner tube is fully extended using the pin mechanism. The angle between the inner tube and vertical is measured to quantify deflection from ideal vertical orientation.
- **Result:** Tube deflected 3.5°.
- **Conclusion:** This test is of limited use in its current form. Spacers between the inner and base tubes were intended to stabilize the inner tube, but the first spacers had too-small tolerances and a second set could not be manufactured in time. The inner tube therefore has much more play than it would with spacers. This test will be repeated once spacers are fabricated.

#### Lifting Force Test
*Testing the pin/handle mechanism and pulley mechanism for required force to extend the pole.*

- **Description:** Using a force gauge, the force required to lift the pin handle was recorded across several scenarios — both with the pulley and by lifting the pole directly from the pin handle. Scenarios included holding the inner tube stationary at an intermediate height, recording the force to start moving the inner tube, and extending the pole from minimum to maximum height in under two seconds. Ten trials of the third scenario were conducted and averaged.
- **Results:**

| Scenario | Pin Handle | Pulley |
|----------|-----------|--------|
| Holding force | 4.9 N | 12.8 N |
| Lifting force (to start moving) | 18.6 N | 14.7 N |
| Avg. max force during full extension | 35.3 N | 32.5 N |

Both methods required very low perceived effort.

- **Conclusion:** Results are lower than expected, which is encouraging. The final prototype will use heavier PVC pipe (2.4 kg vs. 1.3 kg cardboard), so forces are expected to scale by approximately 1.85×. Research shows that the optimum pull strength for repeated tasks is roughly ⅓ of maximum pull strength (~130 N threshold). Current forces are well below this limit, and can be further reduced with lubrication between tubes and bearings for the pulley.

#### Pin Locking Test
*Testing the pin/handle locking mechanism for quick extension and locking time.*

- **Description:** Slot the pin handle into the J-slot to fully extend the rod. The rod must stay securely extended without additional support and must not suffer visible damage. The time to lift the handle and slot it into the lock was measured 5 times.
- **Result:** The pole extended and remained in place without outside support. No visible damage was found after deconstruction. Average time to raise and lock: **3.48 seconds**.
- **Conclusion:** The J-slot locking mechanism is sufficient to bear the weight of the pole. PVC tubes (2.4 kg) will increase the force, but PVC is significantly stronger than cardboard, so durability should not be an issue. Slotting the handle into the lock took slightly longer than desired; a wider initial J-slot opening could reduce the need for precise alignment.

#### Pulley Wrap Locking Test
*Testing the pulley wrap locking mechanism for quick extension and locking time.*

- **Description:** Using the pulley, extend the pole to full height, then wrap the rope around the pole so it remains fully extended without support. Measure time to fully secure the pole and check for damage.
- **Result:** The pole extended easily with the pulley system. No visible damage. Four wraps of rope were needed for sufficient friction. Average time to lift and wrap: **10.98 seconds**.
- **Conclusion:** Initial lifting took only 1–2 seconds; most time was spent wrapping the string at an awkwardly high position. Future designs can improve lock time by including a knob to wrap the rope around or a small spike on the pulling end of the rope to insert into the ground.

### Success Criteria Summary

| Criterion | Threshold | Result | Status |
|-----------|-----------|--------|--------|
| Pull force to actuate | < 130 N | Both methods well under 130 N | **PASS** |
| Locking time | < 5 s | Pin: 3.48 s / Pulley: 10.98 s | Pin: **PASS** / Pulley: **FAIL** |
| Deflection off vertical | < 1° | 3.5° | **FAIL** |

**Next steps:** Address deflection with tighter tolerancing and spacers. Improve pulley locking time with a rope knob or ground spike. Transition from cardboard to PVC tubes for the next prototype.