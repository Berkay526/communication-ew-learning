## What I learned
The history of 50 Ohm impedance goes back to the late 1920s/early 1930s, when the telecom industry was in its infancy. Engineers were designing air-filled coaxial cables for radio transmitters designed to output kW worth of power. These cables would also span long distances, reaching hundreds of miles. This means the cables need to be designed with highest power transfer, highest voltage, and lowest attenuation. Which impedance should be used to satisfy all three objectives?

As it turns out, it’s impossible to balance all three objectives, just like in many other design problems. 

Lowest loss: This depends on losses in the internal dielectric in a coaxial cable. For the air-filled coaxial, this occurs at approximately 77 Ohms, or at approximately 50 Ohms for certain dielectric-filled cables (more on this below).

Highest voltage: This is based on the electric field between the center conductor and sidewalls in the air-filled coax cable. The electric field in the TE10 mode is maximized when the conductor is constructed such that its impedance is approximately 60 Ohms.

Highest power transfer: Coaxial cables of any size might be long enough to act like transmission lines and support wave propagation. The power carried by a coaxial cable is limited by the breakdown field and the impedance of the cable: V2/Z. It turns out that, for the air-filled coax operating below the TE11 cutoff, power transfer is maximized at about 30 Ohms.

## Why it matters
What goes wrong if you ignore it: reflections, which show up as poor return loss and VSWR. You also get mismatch loss and gain ripple versus frequency. PAs pull or become unstable into a bad load, filters detune, and an unterminated stub at λ/4 produces a resonant notch.

Core equations

General line: Z₀ = √[(R + jωL)/(G + jωC)]. When lossless, Z₀ = √(L/C).
Reflection coefficient: Γ = (Z_L − Z₀)/(Z_L + Z₀). Return loss RL = −20·log₁₀|Γ|. VSWR = (1+|Γ|)/(1−|Γ|). Mismatch loss = −10·log₁₀(1−|Γ|²).

Microstrip (Hammerstad/Wheeler form, as given in Pozar). W is trace width, h is dielectric height, εr is substrate permittivity. Copper thickness is assumed zero.

ε_eff = (εr+1)/2 + (εr−1)/2 · 1/√(1 + 12h/W)
For W/h ≤ 1: Z₀ = (60/√ε_eff)·ln(8h/W + W/4h)
For W/h ≥ 1: Z₀ = 120π / {√ε_eff·[W/h + 1.393 + 0.667·ln(W/h + 1.444)]}

IPC-2141/IPC-D-317 microstrip approximation: Z₀ = 87/√(εr+1.41) · ln[5.98h/(0.8W+t)]. It is only valid over a narrow range (roughly 0.1 < W/h < 2). Its error grows quickly outside that range, so don't use it for final geometry.

Via stub resonance: f ≈ c / (4·L_stub·√ε_eff).

Microstrip bend with an optimal miter (Douville & James): M(%) = 52 + 65·e^(−1.35·W/h), valid for W/h ≥ 0.25.

## Design considerations
To implement 50 Ω, make every RF path between 50 Ω ports a transmission line with a controlled cross-section, meaning the width, dielectric height, reference plane and gap stay the same along the whole path. Here's how to do that in order, using KiCad since your roadmap uses it.

## 1. Decide which nets need it

Any RF trace that connects 50 Ω ports needs it: SMA/antenna → switch → filter → LNA/PA → transceiver. This matters once the trace is longer than about λ/10. Some chip pins aren't 50 Ω (for example a transceiver's differential RF pins). Those need the matching network from the datasheet, not just a 50 Ω trace.

## 2. Get the stackup from your fab first

Ask for their controlled-impedance stackup and write down:

- the L1→L2 prepreg thickness after pressing
- Dk at your frequency
- the finished copper thickness on the outer layer
- whether solder mask covers the trace

## 3. Choose the line type

- **Microstrip:** the trace sits on L1 over L2, with no copper beside it. It's the simplest option.
- **CPWG:** the same trace with ground copper on L1 on both sides at a fixed gap, plus stitching vias. Use this if you pour ground on L1. Otherwise a pour placed arbitrarily close to the trace changes its impedance without you noticing.

## 6. Routing rules

- Keep the path short and direct, in the order the signal flows, with the same width all the way.
- Put no vias in the RF path if you can avoid it. If you can't, add a ground via right beside each signal via.
- Leave no stubs. Test points and unused footprint pads count as stubs.
- Use curved or mitered bends, not 90° corners.
- Keep L2 continuous under the whole RF path, with no slots, splits or rows of antipads.
- For CPWG, place stitching vias along both edges near the gap, spaced a few mm apart at GHz frequencies. That spacing is a rule of thumb (≤ λ/20), not a standard.
- Keep other traces at least 3h away. Keep the path away from the board edge.
- If component pads are much wider than the trace, the pad acts as a capacitive step. Simulate it before cutting ground away under the pad.
- Use the connector manufacturer's recommended footprint for the SMA.

## 7. Specify it on the fab order

Add a note such as: *"Controlled impedance: 50 Ω ±10%, L1 referenced to L2, nominal width 0.37 mm / gap 0.2 mm (CPWG); fab may adjust width."* Request an impedance test coupon and a TDR report, measured per IPC-TM-650 2.5.5.7A. The fab tunes the width to its own process, and that final adjustment is what actually gets the line to 50 Ω.

## 8. Verify it

Put a straight 50 Ω thru line between two SMAs somewhere spare on the panel. Measure S11 and S21 with your NanoVNA. Return loss better than about 15–20 dB across your band suggests the line and launches are working. That threshold is a common design target, not a standard.

## Common mistakes

- Using the 1.6 mm board thickness as h when the ground plane is actually on L2.
- Letting a GND pour sit close to a microstrip that was calculated without it.
- Routing signals on L2 under the RF area.
- Treating 50 Ω as the goal at a chip pin that needs a specific matching network.

## Sources
https://resources.altium.com/p/mysterious-50-ohm-impedance-where-it-came-and-why-we-use-it

## AI Assistance
Anthropic, Claude Opus 5.5, used for research assistance, explanations, and topic exploration.