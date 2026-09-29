## What I learned
Physics. At RF, the return current doesn't take the lowest-resistance path. It takes the lowest-inductance path, which runs directly under the signal trace. For a microstrip over a solid plane, image theory gives the return current density:

J(D) = (I/πh) · 1/[1 + (D/h)²], where D is the lateral distance from the trace centreline.

The fraction of return current within ±x is (2/π)·arctan(x/h). Within ±3h that is about 80%. So "keep 3h clear" is a real physical result, not folklore.

## Why it matters
Emerging EM waves due to flowing current may cause electromagnetic inference and unwanted currents near the flowing current.

## Design considerations
To ensure efficient return paths:

 Route low-frequency return currents along the path of least resistance and high-frequency return currents along the path of least inductance.

 Implement solid ground planes under signal traces to minimize loop area and inductance.

 If possible, use a differential pair for high-frequency circuits.

 Avoid ground plane discontinuities such as slots, cutouts, or overlapping clearance holes to prevent current loops and noise.

## Sources
https://www.protoexpress.com/blog/current-return-path-signal-integrity/

## AI Assistance
Anthropic, Claude Opus 5.5, used for research assistance, explanations, and topic exploration.