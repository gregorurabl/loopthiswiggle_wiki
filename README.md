<img width="4321" height="4320" alt="grafik" src="https://github.com/user-attachments/assets/a018f228-cbcf-4bc1-bd8e-c57f847ff5df" />

<h1 style="text-align: center;">Seamless wiggle loops with absolutely reproducible randomness</h1>

**Manual V1.0**  
by Gregor Urabl  
<https://gregorurabl.at>

---

## Overview

**Loop This! Wiggle** generates loopable wiggle motion—via expressions or baked keyframes—based on seeded randomness.  
The result: perfectly seamless, **100% reproducible loops** from something inherently unpredictable.

---

## Key Features

### Dockable ExtendScript Panel
Stays right inside your AE workspace, no floating scripts to manage.

### Universal Property Support
Works with any numeric keyframeable property. If it has a stopwatch icon and accepts numbers (not colors, text, or paths), it's compatible.

Supported examples include:
- Transform properties (Position, Scale, Rotation)
- Effect controls (Blur, Color Correction)
- Masks, shapes, text animators
- Puppet Tool pins
- 3rd-party plugin parameters

Each axis (X, Y, Z) can be independently enabled or disabled in the calculation.

### Clamp Controls
Define maximum and minimum values for each axis individually.

Clamping ensures that wiggle values never exceed a certain range—critical when animating properties like position, rotation, or scale, where uncontrolled randomness would cause jumps or distortions.

### Precise Time Range Control
Specify Start and End frames with professional timecode support (`HH:MM:SS:FF`) or decimal seconds.

The generated animation loops perfectly across this range.

### Dual Noise Algorithms
Choose between:
- **Multi-Frequency (Perlin)** for organic motion
- **AE-Style (Random Walk)** for clean, traditional wiggle behavior

### Expression or Bake
- **Expression mode**: evaluates wiggle in real time
- **Bake mode**: converts the generated values to keyframes

Both modes produce **100% identical outputs**.

### Tabula Rasa or Additive Wiggle
Choose whether the wiggle is generated on top of existing keyframes or on a cleaned property track.

### Load from Expression
Read back settings from previously generated expressions to continue editing or apply to new properties.

### Expression Portability
Copy expressions between different property types—a Position wiggle can be pasted onto Scale, Rotation, or any other numeric property.  
The expression adapts automatically to property dimensions.

---

## How It Works

### 1. Select Your Property (or Multiple Properties)
Choose any numeric keyframeable property in the timeline.

Examples include:
- **Transform properties**: Position, Scale, Rotation, Opacity, Anchor Point
- **Effect controls**: Gaussian Blur Blurriness, Color Balance RGB, Lens Distortion Amount
- **Shape layers**: Rectangle Size, Ellipse Position, Stroke Width
- **Masks**: Mask Feather, Mask Expansion
- **Text animators**: Position, Scale, Rotation, Tracking, Character Offset
- **Puppet Tool**: Pin positions, Mesh deformations
- **3rd-party plugins**: Any numeric parameter that accepts keyframes

Notes:
- As long as the property accepts numeric values (not colors, text strings, or paths), Loop This! Wiggle can animate it.
- Multiple properties across layers can be selected and processed in a single pass.

### 2. Open the Loop This! Wiggle Dockable Panel
Fully ScriptUI-based and dockable inside the AE interface.

### 3. Set Start / End Times
Loop This! Wiggle offers multiple ways to define your animation's time range:

#### Manual Input
Type times directly into the Start and End fields:
- **Decimal seconds:** `4.5` (4.5 seconds)
- **Timecode:** `00:00:04:12` (4 seconds + 12 frames)

See "Timecode Support" chapter for detailed format information.

Additional behavior:
- Timecode is validated against the comp's frame rate
- Ambiguous formats (e.g., `04:12`) trigger a clarification dialog
- Times can be set beyond composition bounds
---

#### Quick Buttons

**Composition-Based Buttons:**
- **Comp In:** Sets Start time to composition start (usually 0s)
- **Comp Out:** Sets End time to composition end
- **Full Comp:** Sets both Start and End to span entire composition
- **Refresh Comp:** Updates time range if composition settings changed

**Playhead-Based Buttons:**
- **Set In:** Sets Start time to **current playhead position**
- **Set Out:** Sets End time to **current playhead position**

---

#### Using Playhead Buttons

**Workflow:**

1. **Move playhead** to desired start position in timeline
2. Click **"Set In"** button
3. Start field updates to current playhead time

4. **Move playhead** to desired end position
5. Click **"Set Out"** button
6. End field updates to current playhead time

**Use Cases:**
- **Precise timing:** Scrub to exact frame, then set
- **Visual reference:** See animation context while setting times
- **Quick adjustments:** Fine-tune range by moving playhead

**Example:**

You want wiggle from frame 100 to frame 200:
1. Scrub timeline to frame 100
2. Click "Set In" (Start = 4.00s at 25fps)
3. Scrub timeline to frame 200
4. Click "Set Out" (End = 8.00s at 25fps)

---

#### Button Comparison

| **Button** | **Source** | **When to Use** |
|------------|------------|-----------------|
| Comp In | Composition start | Quick full-comp setup |
| Comp Out | Composition end | Quick full-comp setup |
| Full Comp | Both boundaries | Fastest full-comp setup |
| **Set In** | **Playhead position** | **Precise visual timing** |
| **Set Out** | **Playhead position** | **Precise visual timing** |
| Refresh Comp | Updated comp info | After changing comp settings |

---

#### Validation

All buttons respect the same validation rules:
- Times can extend beyond composition boundaries (with confirmation)
- Start must be less than End
- Timecode validated against composition frame rate

**Tip:** Use "Set In/Out" for precision, "Comp In/Out" for speed.

---

### 4. Enter Frequency and Amplitude for X, Y, Z
- Independent control per axis
- Any axis can be disabled entirely
- Frequency controls wiggles per second (higher = faster motion)

### 5. Apply Clamps (Optional)
- Define min/max values per axis
- Prevents unwanted drift

Common use cases:
- Keep Scale within safe bounds
- Rotation within a natural range
- Position inside the frame

### 6. Choose Your Noise Type
- **Multi-Frequency (Perlin)**: Organic, layered motion
- **AE-Style (Random Walk)**: Clean, single-frequency wiggle
- **Octaves slider (1–8)**: Controls motion complexity (Perlin only)

### 7. Input a Seed Value
- Same seed = same animation every time
- Guarantees identical results between baked keyframes and live expressions

### 8. Choose Loop Mode

#### Chain
Wiggle fades in from the base animation at the start and fades back to the base animation at the end.  
Ideal for adding temporary wiggle segments that connect smoothly to existing motion.

#### Self-Loop (Default)
The wiggle loops back to its own starting value.  
Creates a perfectly repeating wiggle segment that can sit on top of ongoing base animation.

#### Comp Loop
The wiggle returns to the property value at composition start.  
Designed for animations that must loop seamlessly when the entire composition repeats.

### 9. Choose Expression or Bake Mode
- **Expression**: Real-time calculation inside AE
- **Bake**: Keyframes generated via the same engine, guaranteeing identical results

Bake Mode is ideal for creating seamless animation chains across multiple time segments.

### 10. Choose Additive or Clean Baking (Bake Mode Only)
- **Additive**: Wiggle layered on top of existing keyframes
- **Clean**: Applies wiggle to a cleared property timeline

### 11. Generate Loopable Animation
Click the button and Loop This! Wiggle outputs a seamless, deterministic loop.

---

## Understanding Noise Types

Loop This! Wiggle offers two fundamentally different approaches to generating random motion, each suited to different creative needs.

---

## Multi-Frequency (Perlin Noise)

### What It Is
Perlin noise is a procedural texture generation technique invented by Ken Perlin in 1983.  
It creates smooth, natural-looking gradients by blending multiple frequencies of noise.

### How It Works
Think of layered ocean waves:
- Low frequency: large, slow waves
- Mid frequency: medium ripples
- High frequency: fine surface detail

The **Octaves slider (1–8)** controls how many layers are combined:
- **1–3**: Simple, broad movement
- **4–5**: Balanced, natural motion (recommended)
- **6–8**: Complex, turbulent motion

### Motion Character
Smooth, flowing, organic.  
Feels like natural phenomena such as floating leaves, drifting clouds, or underwater movement.

### When to Use
- Organic, lifelike animations
- Camera shake with realistic turbulence
- Natural object behavior

### Technical Note
Loop This! Wiggle uses **3D Perlin noise sampled along a circular path** to ensure perfect loops.  
Perlin noise has continuous derivatives, preventing sudden jumps between values.

---

### ⚠️ High Frequency Limitation

Perlin Noise is **not suitable for frequencies above 20 Hz**.

At high frequencies (50+ Hz), this results in:
- Loss of characteristic smoothness
- Reduced effective frequency output
- Visual artifacts from over-sampling

**Technical reason:**  
Perlin Noise uses a fixed spatial grid. When sampling speed exceeds grid resolution, interpolation smoothing dominates, acting as a low-pass filter.

**Recommendation:**  
For motion above 20 Hz, always use **AE-Style (Random Walk)** mode.

**UI Indicator:**  
The frequency field displays a warning when Perlin mode is selected with frequencies above 20 Hz.

---

## AE-Style (Random Walk)

### What It Is
A simplified algorithm mimicking After Effects’ native `wiggle()` expression.  
It generates control points using a **Linear Congruential Generator (LCG)** and interpolates them with **Catmull-Rom splines**.

### How It Works
- Random control points are generated at regular intervals
- Points are connected using smooth Catmull-Rom interpolation
- Produces clean, predictable wiggle motion

Notes:
- Single-frequency only
- Octaves slider has no effect

### Motion Character
Clean, mechanical, predictable.  
Feels like traditional keyframe animation with randomized values.

### When to Use
- Matching AE’s native wiggle behavior
- UI and graphic design animations
- Lottie or web exports
- Situations requiring minimal expression complexity

### Technical Note
- LCG ensures identical results for the same seed
- Catmull-Rom interpolation provides C1-continuous curves (continuous velocity)

---

## Choosing Between Noise Types

| Aspect | Multi-Frequency (Perlin) | AE-Style (Random Walk) |
|------|---------------------------|------------------------|
| Complexity | Multi-layered, rich detail | Single-layer, clean |
| Motion Feel | Organic, natural, turbulent | Mechanical, predictable |
| Octaves Control | Yes (1–8) | No effect |
| Performance | Slightly more complex | Faster evaluation |
| Best For | Nature, cameras, particles | UI, graphics, traditional effects |
| Matches AE `wiggle()` | No | Yes |

---

## Frequency Recommendations

Different noise types have different **frequency stability ranges**. Choosing the right mode for your frequency ensures optimal results.

### Recommended Ranges

#### Multi-Frequency (Perlin Noise)
**Stable range:** Up to **~20 Hz**  
**Warning above:** 20 Hz

**Why the limit?**  
Perlin noise uses a spatial grid structure. At high frequencies, the sampling rate exceeds the grid resolution, causing the characteristic smoothness to break down.

**What happens above 20 Hz:**
- Loss of organic feel
- Reduced effective frequency
- Visual artifacts

**UI Indicator:**  
When Perlin mode is selected and frequency exceeds 20 Hz, an orange **"WARNING!"** appears next to the frequency field.

---

#### AE-Style (Random Walk)
**Stable range:** Up to **~80 Hz**  
**Warning above:** 80 Hz

**Why this is higher:**  
Random Walk uses linear interpolation between control points, which handles high frequencies more gracefully than Perlin's grid-based approach.

**What happens above 80 Hz:**
- Mathematical instability
- Unpredictable motion
- Potential crashes or NaN values

---

### Frequency Guidelines

| **Frequency Range** | **Recommended Mode** | **Typical Use** |
|---------------------|----------------------|-----------------|
| 0.1 - 5 Hz | Either mode | Slow drift, floating |
| 5 - 20 Hz | Either mode | Standard wiggle, shake |
| 20 - 80 Hz | **Random Walk only** | Fast jitter, vibration |
| 80+ Hz | **Not recommended** | Technical limitation |

---

### Practical Examples

**Slow floating (2 Hz):**  
✅ Perlin (organic)  
✅ Random Walk (clean)  
→ Use Perlin for natural feel

**Camera shake (10 Hz):**  
✅ Perlin (turbulent)  
✅ Random Walk (mechanical)  
→ Choose based on style preference

**Fast vibration (50 Hz):**  
❌ Perlin (unstable above 20 Hz)  
✅ Random Walk (stable)  
→ **Use Random Walk**

**Extreme jitter (100 Hz):**  
❌ Perlin (breaks down)  
❌ Random Walk (unstable above 80 Hz)  
→ **Not recommended, reduce frequency**

---

### The Warning System

**When you enter a frequency that exceeds the recommended range:**

1. **Perlin mode + >20 Hz:**  
   Orange "WARNING!" text appears next to frequency field  
   Tooltip: "Perlin mode not recommended above 20 Hz. Consider Random Walk."

2. **Random Walk mode + >80 Hz:**  
   Confirmation dialog appears when generating:  
   "WARNING: Random Walk mode with [X] Hz. Random Walk is unstable above 80 Hz. Continue anyway?"

**You can override warnings**, but results may be unpredictable.

---

### Best Practices

**Always check your frequency:**
- Start with low frequencies (2-10 Hz) for natural motion
- Test with Expression mode before baking
- Switch to Random Walk if you need >20 Hz

**When switching modes due to frequency:**
- Keep all other settings identical (amplitude, seed, etc.)
- Preview both modes to compare results
- Perlin → Random Walk maintains similar motion character

**For extreme frequencies (>80 Hz):**
- Consider if you really need that much speed
- Test thoroughly before baking
- Have backup layers ready

---

### Technical Note on Noise Types

**Why these limits exist:**

- **Perlin:** Grid-based noise with fixed spatial resolution
- **Random Walk:** Control points + interpolation

Higher frequencies mean faster time-based sampling. Perlin's grid can't keep up beyond 20 Hz, while Random Walk's simpler math works until 80 Hz.

**This is a fundamental mathematical limitation, not a software bug.**

---

### Summary

- **0-20 Hz:** Use either mode (choose by style)
- **20-80 Hz:** Use Random Walk only
- **80+ Hz:** Reduce frequency or accept instability
- **Watch for orange WARNING! indicator**
- **Test before baking at high frequencies**

---

## Quick Decision

- Want it to feel **alive and organic**? → **Multi-Frequency (Perlin)**
- Want it to feel **clean and controlled**? → **AE-Style (Random Walk)**

## Loop Behavior & Safety Features

### Loop Behavior Modes

Loop This! Wiggle offers three different ways to control how your animation loops.  
The default mode creates self-contained loops that can exist anywhere in your timeline.

---

## The Three Modes

### Self-Loop (Default – Core Feature)

#### What it does
The wiggle value at the **END** returns to the wiggle value at the **START**.  
This creates a perfect loop within the wiggle itself, independent of composition boundaries.

**Value flow**  
value@T2 → wiggle → value@T2 (returns to its own beginning)

#### Why this is the default
This is the core philosophy of Loop This! Wiggle. You can create a looping segment anywhere in your timeline (T2 to T3), extract it, nest it, or repeat it—without depending on composition start/end times.

#### When to use
- Extracting a looping segment from a larger animation
- Creating reusable looping elements in precomps
- Building nested loops on top of base animation
- Anytime you want a self-contained loop that works independently

#### Example
You have a 60-second animation. You want seconds 20–25 to loop perfectly.

- Set **Start = 20s**
- Set **End = 25s**
- Use **Self-Loop mode**

That 5-second segment now loops perfectly on its own, regardless of what happens before or after.

**Visual:**  
<img width="727" height="174" alt="grafik" src="https://github.com/user-attachments/assets/dd830675-838f-4fbc-94f7-61ef505fa1fa" />

---

### Chain (For Sequential Segments)

#### What it does
Your wiggle smoothly fades in from your property's base curve at the start, and fades out back to the base curve at the end.

**Value flow**  
base_value → wiggle → base_value

#### When to use
- Sequential animations that chain together
- Adding wiggle segments to existing motion
- Building modular animation blocks that flow smoothly
- When you want smooth integration with before/after keyframes

#### Example
A character walks:
- Base animation: **0–3s**
- Wiggle segment: **3–5s**
- Base animation continues: **5–8s**

Chain Mode ensures smooth transitions at 3s and 5s.

**Visual:**  
<img width="722" height="177" alt="grafik" src="https://github.com/user-attachments/assets/ab22f1c5-2a64-49e4-aeff-5a350cfee1e9" />


---

### Comp Loop (For Full-Composition Cycles)

#### What it does
The wiggle value at the **END** returns to the property's value at composition start (**T0**).

Designed for animations where:
- **T2 = T0**
- **T3 = T1** (full composition duration)

**Value flow**  
value@T0 → wiggle → value@T0

#### When to use
- Looping background animations spanning the full comp
- Cyclic camera movements across entire comp duration
- When your animation *is* the comp (no before/after segments)
- Exporting comps that will be time-remapped or repeated

#### Example
A logo floats with wiggle motion from **0s–10s** (full comp duration).  
Time remapping is enabled on the comp. The animation loops perfectly when repeated.

**Visual:**  
<img width="726" height="173" alt="grafik" src="https://github.com/user-attachments/assets/c6d55daa-2c9f-4da2-bf80-fa9b3c5a105b" />


---

## Timeline Reference: T0, T1, T2, T3

To understand Loop Modes, you need to know these timeline markers:

- **T0** = Composition Start (automatic reference, usually 0s)
- **T1** = Composition End (T0 + comp duration)
- **T2** = Wiggle Start (your **Start** input in the UI)
- **T3** = Wiggle End (your **End** input in the UI)

### Timeline Flow
<img width="726" height="175" alt="grafik" src="https://github.com/user-attachments/assets/bf2a653a-b855-44f8-aa8d-74cb07cb6a01" />

## Key Insight

- **Self-Loop (Default)**: T3 returns to wiggle value at T2  
- **Chain Mode**: T2 / T3 fade to base curve  
- **Comp Loop**: T3 returns to property value at T0 (requires T2 = T0, T3 = T1)

---

## Self-Loop vs Comp Loop – The Critical Difference

### Self-Loop (T2 to T3)

- Loop segment can be anywhere in the timeline
- T2 and T3 define the loop boundaries
- Independent of composition start/end
- Perfect for extraction and nesting

**Example**  
60s animation, loop seconds 20–25:

- Start = 20s
- End = 25s
- Mode = Self-Loop

That 5-second segment loops perfectly on its own.

---

### Comp Loop (T0 to T1)

- Loop segment must span the entire comp
- Requires T2 = T0 and T3 = T1
- Designed for full-comp loops
- Perfect for time-remapped comps

**Example**  
10s comp, entire animation should loop:

- Start = 0s
- End = 10s
- Mode = Comp Loop

The entire comp loops when repeated.

---

## Self-Loop: The Precomp Extraction Workflow

### Scenario: Extract Looping Segment from Long Animation

#### Setup
You animated a character for 60 seconds.  
At seconds 20–25, the character performs a “thinking” gesture you want to loop indefinitely.

#### Workflow
1. Create a precomp of the full animation (60s comp)
2. In the precomp, select the property (e.g., Head Position)
3. Set **Start = 20s**, **End = 25s**
4. Use **Self-Loop mode** (default)
5. Generate Expression or Bake
6. Duplicate the precomp and name it `Thinking_Loop`
7. In `Thinking_Loop`, delete frames **0–20** and **25–60**
8. Set comp duration to **5s** (25s − 20s)
9. Adjust layer in/out points accordingly

#### Result
You now have a standalone 5-second comp that loops perfectly.  
The wiggle returns to its own starting value (T2), not to composition start (T0).

#### Why Comp Loop Wouldn’t Work
Comp Loop would return to the value at second 0 (start of the 60s animation), not to second 20.  
This would cause a visible jump.

---

## Scenario: Nested Looping Elements

### Setup
You are building a scene with a looping background element (floating particle) nested in a larger composition.

### Workflow
1. Create precomp **`FloatingParticle`** (8s duration)
2. Animate particle Position from 0–8s using **Self-Loop mode**
3. Nest the precomp into the main comp (60s duration)
4. Enable time remapping on the precomp layer
5. Set speed to loop the 8s segment

### Result
The particle loops seamlessly within its own 8-second timeframe, while the main comp continues its 60-second animation.

### Why Self-Loop Is Essential
The particle’s loop (T2 = 0s, T3 = 8s) is independent of the main comp timeline.  
Comp Loop would fail because the main comp is 60s, not 8s.

---

## Choosing the Right Mode

| Your Goal | Use This Mode | Why |
|---------|---------------|-----|
| Extract looping segment from animation | Self-Loop | Loop within T2–T3, independent |
| Create reusable looping precomp | Self-Loop | Self-contained loop |
| Add shake on animated property | Self-Loop + Add Mode | Nested loop on base animation |
| Sequential animation segments | Chain | Smooth transitions |
| Full-comp loop (time remapping) | Comp Loop | Returns to T0 |
| Nested background elements | Self-Loop | Independent timeframe |

---

**When in doubt:** use **Self-Loop (default)**.  
It’s the most flexible option and works for **90% of use cases**.

## Best Practices

### For Self-Contained Loops
- Use **Self-Loop mode** (default)
- Define **T2** and **T3** anywhere in the timeline
- Perfect for extraction and nesting

### For Full-Comp Loops
- Use **Comp Loop mode**
- Requires **T2 = T0** and **T3 = T1**
- Best for time-remapped comps

### For Sequential Segments
- Use **Chain Mode**
- Smooth transitions between blocks
- Works with any T2 / T3 values

### For Nested Motion
- Use **Self-Loop Mode** with **Add Mode** enabled
- Apply to properties with existing base animation
- Test with **Expression Mode** first

---

## Important Notes

### Self-Loop Is *Not* the Same as Comp Loop
- **Self-Loop**: Loops within **T2–T3** (anywhere in timeline)
- **Comp Loop**: Loops across **T0–T1** (full comp duration)

### Time Ranges Beyond Comp
You can set **T2** and **T3** outside composition bounds.  
This is useful for pre-roll animations or extended nested comps.

### Fade Zones
All modes use smooth fade-in / fade-out at boundaries (first and last **5–15%** of duration).  
This ensures seamless transitions.

### Add Mode + Self-Loop
This combination creates **nested loops** (wiggle loops on top of base animation).  
Perfect for shake on animated objects.

---

## Timecode Support

Loop This! Wiggle accepts both **decimal seconds** and **professional SMPTE timecode** for precise timing control.

### Input Formats

#### Decimal Seconds
4.5 → 4.5 seconds
10 → 10 seconds
0.25 → 0.25 seconds

#### Full Timecode (HH:MM:SS:FF)
00:00:04:12 → 4 seconds + 12 frames
00:02:30:00 → 2 minutes 30 seconds
01:15:20:08 → 1 hour 15 minutes 20 seconds + 8 frames

---

### Ambiguous Formats

Short formats like `04:12` or `2:30` are ambiguous and trigger a confirmation dialog.

#### Two Segments (SS:FF or MM:SS?)
04:12
Could mean:
- Seconds : Frames (4.48s at 25fps)
- Minutes : Seconds (252s)

#### Three Segments (MM:SS:FF or HH:MM:SS?)
02:30:15
Could mean:
- Minutes : Seconds : Frames
- Hours : Minutes : Seconds

The script uses intelligent heuristics:
- If the last segment exceeds the frame rate, it is interpreted as time units
- Otherwise, a clarification dialog is shown

**Best practice:** Always use full timecode format (`HH:MM:SS:FF`).

---

### Frame Rate Validation

Frame numbers are validated against the composition’s frame rate:
- 25fps comp → valid frames: 0–24
- 30fps comp → valid frames: 0–29

Invalid frame numbers:
- Trigger an error
- Revert to the last valid input

---

### Display Behavior

After entering timecode, the field converts to decimal seconds internally.

Example:
Input: 00:00:04:12
Display: 4.48

This ensures precision while remaining compatible with After Effects’ time system.

---

### Out-of-Bounds Times

Loop This! Wiggle allows time ranges beyond composition boundaries.

Example:
- Comp duration: `0s–10s`
- Allowed input: `-5s–15s`

Use cases:
- Pre-rendering loops with pre-roll
- Animations extending beyond visible timeline
- Modular loops for nested compositions

The script confirms out-of-bounds values and lets you keep them or clamp to comp range.

---

## Seamless Time Continuation

One of Loop This! Wiggle’s most powerful features:  
**Adjacent time ranges with the same seed create seamless, continuous motion.**

### How It Works

When using **Bake Mode** with identical settings, the motion at a shared boundary is mathematically identical.

**First Animation**
- Start: `0s`
- End: `5s`
- Seed: `42`
- Amplitude: `100px`

**Second Animation**
- Start: `5s`
- End: `10s`
- Seed: `42`
- Amplitude: `100px`

**Result:** Perfect continuation—no jump, no discontinuity.

---

### Requirements for Seamless Continuation

- Identical **seed** across all segments
- Identical **noise settings** (type, octaves, frequency)
- Continuous time ranges (`End₁ = Start₂`)
- **Bake Mode**  
  (Expressions handle this automatically)

---

### Practical Applications

#### Modular Loop Building
Build separate segments:
- Intro: `0–3s`
- Main Loop: `3–6s`
- Outro: `6–9s`

Bake each segment separately, trim, and rearrange.  
All segments flow seamlessly.

#### Pre-Comp Workflows
- Pre-Comp 1: `0–5s`
- Pre-Comp 2: `5–10s`

Nest sequentially in a main comp.  
Motion continues smoothly across pre-comp boundaries.

#### Iterative Animation Building
- Day 1: Bake `0–10s`
- Day 2: Extend, bake `10–20s`
- Day 3: Add intro, bake `-5–0s`

All segments connect perfectly as long as the seed remains consistent.

---

### Why This Matters

Traditional wiggle expressions break when split or rearranged.  
Loop This! Wiggle’s deterministic approach enables:

- Non-destructive editing
- Collaborative workflows
- Iterative refinement
- Modular, reusable animation templates

---

### Technical Note

Both noise systems are **time-based**, not keyframe-based.  
The value at time `t` depends only on `t` and the seed—not on neighboring keyframes.

Same seed + same time = same value, always.

---

## Expression Portability

Loop This! Wiggle expressions are **dimension-agnostic** and can be copied between property types without modification.

### How It Works

The expression detects the target property’s dimensionality automatically:

- **1D**: Rotation, Opacity, Blur → X-axis only
- **2D**: Position, Scale → X and Y
- **3D**: 3D Position, Scale → X, Y, Z

---

### Copy / Paste Between Property Types

**Scenario**  
You create a Position wiggle (2D) and want the same motion on Rotation (1D) and 3D Scale (3D).

**Workflow**
1. Select Position property with expression
2. Copy (`Ctrl/Cmd + C`)
3. Paste onto Rotation (`Ctrl/Cmd + V`)
4. Paste onto 3D Scale

**Result**
- Position (2D): X + Y wiggle
- Rotation (1D): X-axis amplitude only
- 3D Scale (3D): X, Y, Z wiggle

---

### Practical Examples

**Camera Shake → Lens Distortion**
- Camera Position (3D) → Lens Distortion Amount (1D)
- Result: Synchronized camera motion and lens distortion

**Shape Size → Stroke Width**
- Rectangle Size (2D) → Stroke Width (1D)
- Result: Pulsing shape with matching stroke thickness

**Text Position → Character Offset**
- Text Position (2D) → Character Offset (1D)
- Result: Bouncy text with jittery spacing

---

### Axis Mapping

- **Higher → Lower dimensions**
  - X → X
  - Y → Y
  - Z ignored (3D → 2D)
  - Only X used (2D/3D → 1D)

- **Lower → Higher dimensions**
  - 1D → 2D: X maps to both X and Y
  - 1D → 3D: X maps to X, Y, Z
  - Disable axes in UI or edit expression to differentiate amplitudes

---

### Cross-Property Seed Consistency

Using the same seed keeps motion synchronized across properties:
- Position (seed 42)
- Rotation (seed 42)
- Scale (seed 42)

All move in rhythmic harmony.  
Change a seed to intentionally desynchronize.

---

### Limitations

Not supported:
- Color properties (RGBA)
- Text **Source Text** (string-based)
- Dropdown menus and checkboxes (boolean / index values)

Supported:
- All numeric properties  
  (Sliders, angles, percentages, positions, sizes, intensities)
## Universal Property Compatibility

If it has a stopwatch icon next to it **and is a numeric property**, Loop This! Wiggle can animate it.

Below are examples (but not limitations) of supported properties.

---

## Transform Properties

- **Position** (2D / 3D)
- **Anchor Point** (2D / 3D)
- **Scale** (2D / 3D)
- **Rotation**  
  - 1D Rotation  
  - X / Y / Z Rotation (3D layers)
- **Opacity** (1D)

---

## Effect Controls

### Built-in Effects

- **Gaussian Blur** → Blurriness
- **Fast Blur** → Blurriness
- **Color Balance** → RGB Levels
- **Curves** → Input / Output White & Black
- **Lens Distortion** → Curvature, Field of View
- **Transform Effect** → Position, Scale, Rotation
- **Any numeric slider or angle control**

---

### 3rd-Party Plugins

Loop This! Wiggle works with **any plugin exposing numeric parameters**:

- **Trapcode Particular** → Particle velocities, sizes, lifespans
- **Red Giant Universe** → Transition amounts, distortion levels
- **Boris FX** → Effect intensities, positions
- **Native Instruments** → Parameter knobs
- **Custom plugins** → Any keyframeable numeric control

---

## Shape Layers

- Rectangle Size
- Rectangle Roundness
- Ellipse Position
- Ellipse Size
- Polystar Points
- Polystar Rotation
- Stroke Width
- Stroke Opacity
- Fill Opacity
- Path Trim Start / End

---

## Masks

- Mask Path *(animates vertices – advanced usage)*
- Mask Feather
- Mask Opacity
- Mask Expansion

---

## Text Animators

- Position
- Scale
- Rotation
- Tracking
- Line Spacing
- Character Offset
- Character Value *(numeric properties only)*
- Fill Opacity
- Stroke Opacity
- Stroke Width

---

## Puppet Tool

- **Pin Positions (2D)**  
  Loop This! Wiggle was tested extensively with Puppet Pins
- Mesh deformations
- Starch amounts

### Example Use Case
Animate a character’s face with 10 Puppet Pins, each with subtle wiggle motion.

- **Multi-Property Mode + Shared Seed** → Synchronized movement  
- **Individual Seed** → Organic variation

---

## Audio Keyframes

- Left / Right Channel levels (1D)
- Slider Control values (1D)

---

## Camera Properties

- Point of Interest (3D)
- Position (3D)
- Zoom (1D)
- Depth of Field Focus Distance (1D)
- Aperture (1D)

---

## Light Properties

- Position (3D)
- Point of Interest (3D)
- Intensity (1D)
- Cone Angle (1D)
- Cone Feather (1D)

---

## Compatibility Notes

### ✅ Works With

- All numeric properties (integers, floats, angles, percentages)
- 1D, 2D, and 3D properties
- Properties with or without units (pixels, degrees, percentages)
- Nested property groups (effects within effects)
- Third-party plugin parameters

### ❌ Does Not Work With

- Text strings (Source Text, Comments)
- Color properties (Fill Color, Stroke Color)  
  *(4D RGBA, not standard 1D/2D/3D)*
- Dropdown selections (Layer Index, Blending Mode)
- Checkboxes (Effect On / Off toggles)
- Path data (Mask Path vertices – requires special handling)

---

## Property Auto-Detection

When you click **Generate Expression** or **Bake Keyframes** without explicitly selecting properties, Loop This! Wiggle automatically scans for:

1. Selected properties in the timeline *(highest priority)*
2. Common transform properties (Position, Scale, Rotation)
3. Effect properties *(scans up to 4 levels deep in effect groups)*

### This means you can:

- Select a layer  
- Click **Generate Expression**  
- The script finds Position / Scale / Rotation automatically

**Or:**

- Select a layer with multiple effects applied
- Enable **Multi-Property Mode**
- Click **Refresh Properties**
- The script finds all compatible effect parameters

---

## Load from Expression Feature

The **Load from Expression** button reads settings from existing Loop This! Wiggle expressions, allowing you to:

- Continue editing a previously generated wiggle
- Copy settings from one property to another
- Batch-apply identical settings across multiple properties

---

### How It Works

1. Select property/properties with Loop This! Wiggle expressions
2. Click **Load from Expression**
3. Script behavior depends on selection:

#### Single Property
- Settings load automatically into the UI
- All parameters update:
  - Time
  - Amplitude
  - Clamps
  - Seed
  - Noise type
  - Octaves

#### Multiple Properties with Identical Expressions
- Settings load automatically
- Confirmation message:  
  *“Loaded shared settings from N identical expressions”*

#### Multiple Properties with Different Expressions
- Dialog asks: *Load from first property?*
  - **OK** → Load from first property
  - **Cancel** → Abort operation

---

### Loaded Parameters

The parser extracts:

- ✅ Start / End times *(converted to composition time)*
- ✅ Frequency
- ✅ Amplitude per axis (X, Y, Z)
- ✅ Clamp ranges per axis
- ✅ Seed value
- ✅ Noise type (Multi-Frequency or AE-Style)
- ✅ Octaves *(Perlin mode only)*
- ✅ Enabled axes *(detected from non-zero amplitudes)*

---

### Limitations

The parser **cannot** recover:

- **Disabled axes**: Any axis that was disabled (checkbox unchecked) during expression generation is stored as `0` in the expression code. This applies regardless of whether the axis had a value before being disabled. The parser cannot distinguish between intentional zero amplitude and a disabled axis.

- **Loop Mode**: The `loopMode` parameter is extracted from the expression, but if you're loading settings to apply to **new properties**, you'll need to manually set the Loop Mode dropdown to match.

- **Add Mode state**: Baking-only setting, not stored in expression.

- **Prompts & Backup checkbox**: UI-only setting, not stored in expression.

- **Multi-Property settings**: Seed mode, time offset mode (only relevant in Multi-Property Mode).

**Workaround for disabled axes:**  
After loading, manually uncheck axes that should remain static. The parser assumes all non-zero amplitudes indicate enabled axes, but cannot detect disabled axes stored as zero.

**Workaround for Loop Mode:**  
After loading, check the Loop Mode dropdown and adjust if needed. The parser extracts the value but doesn't automatically update the dropdown.
---

## Typical Workflow

**Generate Expression → Test & Tweak → Load Back → Adjust → Regenerate**

## Multi-Property Mode Guide

**Multi-Property Mode** processes multiple properties simultaneously with coordinated settings.  
The **Seed Mode** and **Time Offset** controls determine how properties interact with each other.

---

## Seed Mode – Movement Variation Control

The **Seed** is the starting value for the random number generator.  
**Identical seed = identical movement pattern.**

---

### Individual (Default)
Layer 1 Position: Seed 1
Layer 1 Rotation: Seed 2
Layer 2 Position: Seed 3
Layer 2 Rotation: Seed 4


- Each property receives a different seed *(Base Seed + Index)*
- **Result:** Every property moves completely differently
- **Use Case:** Maximum variation, organic-looking movements

---

### Shared
Layer 1 Position: Seed 1
Layer 1 Rotation: Seed 1
Layer 2 Position: Seed 1
Layer 2 Rotation: Seed 1


- All properties use the same seed
- **Result:** All properties move identically (scaled by amplitude)
- **Use Case:** Synchronized movements, unified “rhythm”
- **Note:** Only mode guaranteeing reproducible results

---

### Sequential
Layer 1 Position: Seed 1
Layer 1 Rotation: Seed 101
Layer 2 Position: Seed 201
Layer 2 Rotation: Seed 301


- Seeds increment in steps of 100 *(Base Seed + Index × 100)*
- **Result:** Similar but recognizably different movements
- **Use Case:** Controlled variation with discernible patterns

---

### Random
Layer 1 Position: Seed 1 + random(0–10000)
Layer 1 Rotation: Seed 1 + random(0–10000)
Layer 2 Position: Seed 1 + random(0–10000)
Layer 2 Rotation: Seed 1 + random(0–10000)

- Completely random seeds for each property
- **Result:** Maximum unpredictability
- **Use Case:** Chaotic, unstructured movements

---

## Time Offset – Layer Timing Control

### None (Default)
Layer 1: Start 0s, End 10s
Layer 2: Start 0s, End 10s
Layer 3: Start 0s, End 10s


- All layers start and end simultaneously
- **Result:** Synchronous animation of all elements

---

### Layer Index × 0.1s
Layer 1 (Index 0): Start 0.0s, End 10.0s
Layer 2 (Index 1): Start 0.1s, End 10.1s
Layer 3 (Index 2): Start 0.2s, End 10.2s


- Each higher layer starts 0.1 seconds later
- **Result:** “Waterfall” effect, staggered animation
- **Use Case:** Sequential buildup, domino-like effects

---

### Random
Layer 1: Start -0.05s, End 9.95s
Layer 2: Start +0.23s, End 10.23s
Layer 3: Start -0.12s, End 9.88s


- Random offset of ±0.25 seconds for each layer
- **Result:** Slightly offset but unpredictable starts
- **Use Case:** Organic, non-mechanical timing

---

## Practical Combinations

| Scenario | Seed Mode | Time Offset | Result |
|--------|-----------|-------------|--------|
| Synchronized groups (e.g., dancers) | Shared | None | Identical, simultaneous motion |
| Organic swarm (e.g., fish school) | Individual | Random | Unique motion with natural timing |
| Mechanical sequences (e.g., gears) | Sequential | Layer Index × 0.1s | Ordered, offset movement |
| Chaos / explosions (e.g., debris) | Random | Random | Maximum unpredictability |

---

## Workflow Tips

1. **Start Simple**  
   Begin with default settings (Individual / None)
2. **Preview First**  
   Use *Generate Expression* before baking
3. **Layer Order Matters**  
   Time offset is based on layer stack order
4. **Performance**  
   Preview with fewer properties, batch process later
5. **Reproducibility**  
   Note your seed value to recreate results

---

## Manual Expression Editing

After generating an expression, you can manually edit animation parameters directly in After Effects’ **Expression Editor** without regenerating.

---

### Editable Parameters Section

```javascript
// ===== USER EDITABLE VARIABLES =====
var t0=4.200000;          // Start Time
var t1=7.200000;          // End Time
var freq=10.000000;       // Frequency (wiggles per second)
var ax=5.000000;          // X Amplitude
var ay=5.000000;          // Y Amplitude
var az=0.000000;          // Z Amplitude
var cminX=-50.000000;     // X Clamp Min
var cmaxX=50.000000;      // X Clamp Max
var cminY=-30.000000;     // Y Clamp Min
var cmaxY=30.000000;      // Y Clamp Max
var cminZ=-30.000000;     // Z Clamp Min
var cmaxZ=30.000000;      // Z Clamp Max
var seed=25717;           // Random Seed
var octaves=5;            // Octaves (Perlin mode only)
var mode=0;               // 0=Perlin, 1=Random Walk
var fps=25.00;            // Frame Rate
// ==================================
```

Editable Parameters Reference
=============================

**Time Range**  
- `t0` – Start time (in seconds, relative to composition start)  
- `t1` – End time (in seconds, relative to composition start)  

**Animation Intensity**  
- `ax` – X-axis amplitude (horizontal movement range)  
- `ay` – Y-axis amplitude (vertical movement range)  
- `az` – Z-axis amplitude (depth movement range, 3D properties only)  

**Movement Constraints**  
- `cminX` / `cmaxX` – Minimum / maximum X-axis offset limits  
- `cminY` / `cmaxY` – Minimum / maximum Y-axis offset limits  
- `cminZ` / `cmaxZ` – Minimum / maximum Z-axis offset limits  

**Motion Character**  
- `freq` – Frequency (number of wiggles per second)  
- `seed` – Random seed (change for different motion patterns)  
- `mode` – Noise algorithm (0 = Multi-Frequency/Perlin, 1 = AE-Style/Random Walk)  
- `octaves` – Detail level for Perlin noise (1-8, ignored in mode=1)  

**Technical**  
- `fps` – Composition frame rate (used for loop calculations)  

**Loop Behavior:**
- `loopMode` -- Loop behavior mode:
  - `0` = Chain Mode (fades to base curve)
  - `1` = Self-Loop Mode (returns to T2, **default**)
  - `2` = Comp Loop Mode (returns to T0)

**Common Edits:**

```javascript
// Switch from Self-Loop to Chain:
var loopMode=1; → var loopMode=0;

// Switch to Comp Loop:
var loopMode=1; → var loopMode=2;

// Try Self-Loop after using Chain:
var loopMode=0; → var loopMode=1;
```

**Important:** Changing `loopMode` affects how the animation loops. See "Loop Behavior Modes" chapter for detailed explanations.

Editing Best Practices
----------------------

**Quick Tweaks:**  
- Adjust `freq` to speed up or slow down the wiggle  
- Change `seed` to try different motion patterns  
- Modify amplitude values (`ax`, `ay`, `az`) to scale movement intensity  
- Fine-tune time range (`t0`, `t1`) to shift or extend animation  

**Algorithm Switching:**
```javascript
// Switch from Perlin to Random Walk:
var mode=0;  →  var mode=1;

// Switch back and increase detail:
var mode=1;       →  var mode=0;
var octaves=5;    →  var octaves=7;
```

**Common Edits:**
```javascript
// Make wiggle twice as fast:
var freq=10.000000;  →  var freq=20.000000;

// Reduce horizontal movement by half:
var ax=50.000000;  →  var ax=25.000000;

// Try completely different motion:
var seed=12345;  →  var seed=99999;

// Increase Perlin complexity:
var octaves=3;  →  var octaves=6;
```

# Regenerating vs. Manual Editing

## When to Edit Manually
- Small parameter adjustments
- Testing different seeds or frequencies
- Fine-tuning amplitude or clamp values
- Experimenting with octaves or noise mode

## When to Regenerate
- Major structural changes (time range shifts across multiple properties)
- Switching between 1D / 2D / 3D properties
- Enabling / disabling axes (X / Y / Z checkboxes)
- Batch applying to multiple properties

---

# Important Notes

## Do Not Edit
- Any code below the `// ==================================` line
- The noise functions (`h3`, `p3`, `tb`, `wigglePath`, etc.)
- Loop transition logic
- Dimension-aware return statements

> Modifying these sections may break the expression.

## Expression Persistence
Manual edits persist until you regenerate or modify the expression through other means.

## Undo Support
After Effects' standard undo (`Ctrl+Z` / `Cmd+Z`) works with expression edits.

---

# Loop Behavior & Chaining

This chapter explains how **Loop This! Wiggle** creates seamless animations and how to chain multiple animation blocks together.

## Understanding Loop Perfection
**Loop This! Wiggle** is designed to create mathematically perfect loops.  
The core feature is **Self-Loop mode**, which creates loops that return to their own starting value (T2), not composition start (T0).

The three factors that determine loop behavior:
1. Which Loop Behavior Mode you choose (Self-Loop / Chain / Comp Loop)
2. Whether you create one block or multiple blocks
3. Your Add Mode setting

---

## Single Block Animation (Perfect Loops)

**When:** You create one animation block using Self-Loop mode (default).

**Example:**
- Layer: Position property with no keyframes
- Animation: 0s to 10s, Seed 42, Self-Loop mode

**Result:**
- ✅ Pixel-perfect loop - Value at T3 returns to value at T2
- ✅ Seamless loop - Animation repeats infinitely without jumps
- ✅ Predictable behavior - Same seed always produces identical results
- ✅ Can be extracted - Works independently of comp boundaries

> Recommended approach for pure, self-contained loops.

---

## Multiple Block Animation (Chained Segments)

**When:** You create multiple animation blocks using Chain mode.

**Example:**
- Block 1: 0s to 5s, Seed 42, Chain Mode
- Block 2: 5s to 10s, Seed 99, Chain Mode

**Result:**
- ✅ Seamless transitions - Blocks connect smoothly at boundaries (5s)
- ✅ No jumps between blocks - Fade zones ensure continuity
- ⚠️ Loop precision affected - Fade zones modify the motion curve slightly

**Why this happens:**  
Each block uses fade-in/fade-out zones (first/last 5-15% of duration) to ensure smooth connections to the base curve. These fades are necessary to prevent jumps when seeds differ.

---

## The Role of Seed Values

### Identical Seeds
If all blocks use the same seed, transitions are seamless and each block loops perfectly within itself.

### Different Seeds
If blocks use different seeds, transitions are smooth but individual blocks may not loop perfectly due to fade zones.

**Example:**
- Block 1: 0-5s, Seed 42, Self-Loop Mode
- Block 2: 5-10s, Seed 42, Self-Loop Mode

**Result:** Seamless 10-second animation where both blocks loop individually.

---

## Loop Mode Impact on Chaining

**Self-Loop Mode (Default)**
- Best for: Self-contained loops anywhere in timeline
- Behavior: T3 returns to value at T2
- Use when: Extracting segments, nesting precomps, building reusable loops

**Chain Mode**
- Best for: Sequential segments that flow into each other
- Behavior: Each block fades from/to base curve
- Use when: Building animations that integrate with before/after keyframes

**Comp Loop Mode**
- Best for: Full-comp loops (T2=T0, T3=T1)
- Behavior: T3 returns to value at T0
- Use when: Time-remapped comps, full-duration loops

---

## Add Mode Considerations

**Add Mode OFF (Clean Slate)**
- Keyframes in T2-T3 range are deleted (with warning)
- Wiggle replaces existing motion
- Best for: Creating fresh animation from scratch

**Add Mode ON (Layering)**
- Existing keyframes preserved
- Wiggle adds on top mathematically
- Best for: Adding shake/tremor to existing animation

**Example - Layered Motion:**
1. Animate Position: 0-10s (base movement)
2. Apply wiggle: 3-7s, Self-Loop Mode, Add Mode ON
3. Result: Base movement continues + wiggle loops within 3-7s segment

---

## Seamless Time Continuation (Advanced)

When using identical seeds and settings, adjacent time ranges create mathematically continuous motion.

**Requirements:**
- Same seed across segments
- Same noise settings (type, octaves, frequency)
- Continuous time ranges (End₁ = Start₂)
- Use Bake Mode for best results

**Example:**
- Segment 1: Bake 0-5s, Seed 42, Self-Loop
- Segment 2: Bake 5-10s, Seed 42, Self-Loop
- Result: Motion at 5s is identical in both segments → perfect continuation

**Use Cases:**
- Modular loop building (intro, main, outro)
- Pre-comp workflows (nested compositions)
- Iterative animation (extend later without breaking existing parts)

---

# Best Practices

**For self-contained loops:**
- Use Self-Loop mode (default)
- Define T2 and T3 anywhere in timeline
- Perfect for extraction and nesting

**For sequential animations:**
- Use Chain Mode for smooth transitions
- Use identical seeds across segments
- Plan time ranges in advance

**For full-comp loops:**
- Use Comp Loop mode
- Ensure T2=T0 and T3=T1
- Perfect for time-remapping

**For nested motion:**
- Use Self-Loop Mode with Add Mode enabled
- Apply to properties with existing base animation
- Test with Expression Mode first

---

# Troubleshooting

**"My extracted segment doesn't loop perfectly"**
- Verify you used Self-Loop mode (not Comp Loop)
- Check that T2 and T3 match your extraction range
- Ensure single, uninterrupted block

**"Comp Loop doesn't work in nested precomp"**
- Comp Loop requires T2=T0 and T3=T1 of the comp
- For nested loops, use Self-Loop mode instead

**"Chained blocks don't match in style"**
- Use identical seeds for visual continuity
- Match frequency and amplitude between blocks
- Use same noise type (both Perlin or both Random Walk)

---

# Summary Table

| Goal                        | Mode       | Add Mode | T2/T3 Position        |
|------------------------------|------------|----------|----------------------|
| Extract looping segment      | Self-Loop  | OFF      | Anywhere             |
| Reusable precomp loop        | Self-Loop  | OFF      | Anywhere             |
| Shake on animation           | Self-Loop  | ON       | Anywhere             |
| Sequential segments          | Chain      | OFF      | Continuous           |
| Full-comp time remap         | Comp Loop  | OFF      | T2=T0, T3=T1         |
| Nested background            | Self-Loop  | OFF      | Anywhere             |

---

# FAQs

**Q: How is this different from the native wiggle() expression?**  
A: Native wiggle cannot loop. Existing hacks usually blend sine curves. Loop This! Wiggle generates real pseudo-random values that repeat perfectly.

**Q: Why "reproducible randomness"?**  
A: Uses seeded pseudo-randomness—identical settings and seed produce identical motion, even though it appears random.

**Q: What's the difference between Perlin and Random Walk?**  
A: Perlin creates organic, multi-layered motion. Random Walk creates clean, single-frequency wiggle matching AE's native behavior.

**Q: When should I use Octaves?**  
A: Only in Multi-Frequency (Perlin) mode. Higher octaves (5-8) add complexity. Lower octaves (1-3) create simpler motion. Random Walk ignores this setting.

**Q: Can axes be controlled separately?**  
A: Yes. Each axis (X, Y, Z) can be enabled/disabled individually.

**Q: Can I limit the range of motion?**  
A: Yes, with per-axis Clamp Controls.

**Q: Expression vs. Bake—what's the difference?**  
A: Expressions calculate live; Bake creates keyframes. Both produce identical results.

**Q: Can this tool work with existing keyframes?**  
A: Yes. Use Additive Mode to build on existing animation, or Clean Mode to start fresh.

**Q: Does it support 3D properties?**  
A: Yes, full support for 1D, 2D, and 3D with independent controls.

**Q: What properties can I animate with this tool?**  
A: Any numeric property with a stopwatch icon, including transforms, effects, masks, shapes, text animators, Puppet Tool pins, and 3rd-party plugin parameters.

**Q: Can I copy expressions between different property types?**  
A: Yes! Expressions are dimension-agnostic. They adapt automatically.

**Q: Can I create seamless animations across multiple time segments?**  
A: Yes, using Bake Mode with identical seeds and settings.

**Q: Can I enter time in professional timecode instead of seconds?**  
A: Yes, either in seconds or SMPTE timecode.

**Q: What happens if my timecode is ambiguous?**  
A: The tool prompts for clarification; full HH:MM:SS:FF is recommended.

**Q: Does the script validate timecode against my comp's frame rate?**  
A: Yes, invalid frames are rejected.

**Q: Can I read back settings from an existing expression?**  
A: Yes, via "Load from Expression".

**Q: What are the Loop Behavior Modes and which should I use?**  
A: Loop This! Wiggle offers three modes:

- **Self-Loop (Default):** The wiggle returns to its own starting value (T2). Perfect for creating self-contained loops anywhere in your timeline, extracting segments, or nesting in precomps. This is the core feature of the script.

- **Chain Mode:** The wiggle fades smoothly from/to the property's base curve. Best for sequential animation segments that flow into each other.

- **Comp Loop:** The wiggle returns to the value at composition start (T0). Designed for full-comp loops that will be time-remapped or repeated.

**When in doubt, use Self-Loop** (default). It's the most flexible and works for 90% of use cases. See "Loop Behavior Modes" chapter for detailed explanations and workflows.

**Q: What does the "Prompts & Backup" checkbox do?**  
A: This checkbox controls the safety system:

**Enabled (Default):**
- Shows warning dialogs before overwriting expressions or deleting keyframes
- Offers to create backup layers automatically
- Requires confirmation for destructive operations
- **Recommended while learning the script**

**Disabled (Silent Mode):**
- No warning dialogs
- No automatic backup creation
- Operations execute immediately
- **For experienced users who want faster workflow**

All operations are still undoable with Ctrl+Z / Cmd+Z regardless of this setting. See "Prompts & Backup System" chapter for details.

**Q: How does the Warning System work?**  
A: The script uses a 3-step warning flow when "Prompts & Backup" is enabled:

**Step 1 - Initial Warning:**  
Detects existing expressions and/or keyframes, shows what will be affected.  
- OK = Create backup layer + proceed
- Cancel = Show more options

**Step 2 - No-Backup Option:**  
Confirms you want to proceed without creating a backup.  
- OK = Proceed without backup
- Cancel = Abort operation

**Step 3 - Self-Loop Info (if applicable):**  
Informational dialog explaining nested loop behavior when using Self-Loop + Add Mode.

You can bypass all warnings by disabling the "Prompts & Backup" checkbox. See "Prompts & Backup System" chapter for detailed scenarios.

**Q: What's the difference between Expression Mode and Bake Mode?**  
A: Both modes produce **identical animations**, but differ in execution:

**Expression Mode:**
- Creates live expression code
- Evaluates in real-time during playback
- Easy to adjust parameters by editing expression
- Best for: Previewing, testing, iterating

**Bake Mode:**
- Converts expression to actual keyframes
- Static keyframes, no real-time calculation
- Better playback performance
- Best for: Final optimization, older AE versions, delivery

**Tip:** Use Expression Mode to dial in your settings, then Bake for final delivery.

**Q: Can I use frequencies above 20 Hz?**  
A: Yes, but with limitations:

- **Perlin Mode:** Stable up to ~20 Hz, becomes unstable above
  - Orange "WARNING!" appears in UI above 20 Hz
  - Switch to Random Walk for >20 Hz

- **Random Walk Mode:** Stable up to ~80 Hz
  - Confirmation dialog appears above 80 Hz
  - Not recommended above 80 Hz

**Best practice:** Start with low frequencies (2-10 Hz), test thoroughly if going higher. See "Frequency Recommendations" for detailed guidelines.
---

# Use Cases
- Seamless camera shake for looping titles or trailers
- Logo or UI animations with subtle, repeatable motion
- Looping animations for the web (icons, banners)
- Lottie animations (loading indicators, micro-interactions)
- Corporate design video elements (looping logos, branding loops)
- Generative designs or template pipelines
- Adding motion to existing rigs
- Natural phenomena simulations (Perlin mode)
- Mechanical/technical animations (Random Walk mode)
- Puppet Tool character animation (subtle face movements)
- Plugin parameter automation (Trapcode, Red Giant, Boris FX)
- Modular animation segments
- Multi-layer synchronization
- Effect intensity pulsing
- Text animator jitter

---

### Self-Loop Mode Examples

**Extracting looping segments from long animations:**
- Character animation: Extract a 5-second "thinking" gesture from a 60-second performance
- Product showcase: Isolate a 3-second rotation loop from a full turnaround
- UI elements: Extract looping loading indicators from complex interface animations
- Background elements: Pull out seamlessly looping clouds from a sky animation

**Reusable precomp loops:**
- Create library of looping effects (floating particles, ambient motion, subtle breathe)
- Build modular animation blocks that can be nested anywhere
- Template system: Looping segments that work across multiple projects
- Stock footage enhancement: Add looping wiggle to static elements

**Nested repetitive motion:**
- Heartbeat on breathing character (chest movement loops while character breathes)
- Engine vibration on moving vehicle (vibration loops while vehicle drives)
- Screen flicker on animated monitor (flicker loops while UI animates)
- Typing jitter on moving keyboard (keys wiggle while keyboard rotates)

---

### Comp Loop Mode Examples

**Time-remapped backgrounds:**
- Looping clouds that seamlessly repeat when comp is time-remapped
- Animated textures that cycle perfectly across composition boundaries
- Environmental effects (rain, snow, fog) that loop without visible seams
- Abstract backgrounds for motion graphics templates

**Cyclic camera movements:**
- 360° camera orbit that returns to starting position
- Dolly push/pull that loops seamlessly
- Handheld camera shake for entire composition duration
- Establishing shot camera moves that repeat perfectly

**Template animations:**
- Lower thirds that loop when comp is extended
- Logo reveals designed to work with time remapping
- Transition elements that can be repeated indefinitely
- Stock motion graphics that clients can loop as needed

---

### Chain Mode Examples

**Sequential animation building:**
- Character walks → pauses with shake → continues walking
- Camera travels → adds turbulence during action → stabilizes
- Logo animates in → adds accent wiggle → animates out
- Timeline: calm → chaos → calm transitions

**Modular animation segments:**
- Building block approach: Intro (0-3s) + Main (3-6s) + Outro (6-9s)
- Each segment flows smoothly into the next
- Can rearrange or replace segments independently
- Smooth transitions maintained throughout

---

### Prompts OFF Workflow (Experienced Users)

**Rapid iteration workflow:**
1. Disable "Prompts & Backup" checkbox
2. Generate expression with settings A
3. Preview result
4. Regenerate immediately with settings B (no dialogs)
5. Compare results
6. Repeat until satisfied
7. Final bake with Prompts re-enabled (safety for final version)

**Batch processing workflow:**
1. Prepare 20 layers with properties selected
2. Disable Prompts
3. Enable Multi-Property Mode
4. Click Generate → Instant application to all layers
5. No interruptions, no backup layer clutter
6. Rely on Ctrl+Z if needed

**When to use Prompts OFF:**
- You've already manually backed up
- Working in a version-controlled project
- Processing many layers at once
- You're confident and want speed over safety
- Prototyping/testing phase (not final delivery)

**⚠️ Remember:** Prompts OFF means no warnings and no automatic backups. Use with caution!

---

### Advanced Workflow Examples

**Building a character animation library:**
- Create precomps for each looping gesture (thinking, idle, breathing)
- Use Self-Loop mode for each gesture (3-5 second loops)
- Build main animation by nesting gesture precomps
- Each gesture loops perfectly independently

**Modular template system:**
- Base animation: 0-10s (Chain Mode, Seed 42)
- Accent 1: 3-5s (Chain Mode, Seed 42, Add Mode)
- Accent 2: 7-9s (Chain Mode, Seed 42, Add Mode)
- All use same seed → Seamless integration
- Can enable/disable accent layers independently

**Nested precomp architecture:**
- Main Comp (60s): Camera flight path
- Precomp A (5s): Looping particle system (Self-Loop)
- Precomp B (8s): Looping background element (Self-Loop)
- Precomp C (3s): Looping UI element (Self-Loop)
- Each precomp repeats independently via time remapping

**Stock footage enhancement:**
- Import static element (tree, building, person)
- Apply Self-Loop wiggle (subtle, 10s duration)
- Extract to precomp
- Nest multiple times with different placements
- Entire scene comes alive with motion

---

### Industry-Specific Examples

**Broadcast Graphics:**
- Lower thirds with looping accent motion (Self-Loop, 4s)
- News ticker with subtle position jitter (Self-Loop, continuous)
- Logo bugs with breathing animation (Self-Loop, 6s)

**Product Visualization:**
- Extract 360° rotation segment as loop (Self-Loop, 8s)
- Add subtle hover motion to static product (Self-Loop, Add Mode)
- Ambient lighting fluctuation (Comp Loop, full duration)

**Social Media Content:**
- Instagram story loops (Self-Loop, 3-5s)
- Looping cinemagraphs (Self-Loop on specific elements)
- Endless scroll animations (Comp Loop for seamless repeat)

**Motion Design:**
- Kinetic typography with rhythmic shake (Self-Loop, beat-synced)
- Abstract shape morphing (Chain Mode, sequential blocks)
- Particle systems (Self-Loop nested in larger animations)

---

# Compatibility
- Tested from After Effects 25.4 (2025) onward
- Should work in older versions
- Requires modern JavaScript engine (V8, ECMAScript 2018+)

---

# Support & Resources
- Documentation: This manual  
- Other Products: [aescripts.com/authors/gregor-urabl](https://aescripts.com/authors/gregor-urabl/)  
- Support: Available through aescripts.com  

---

**Loop This! Wiggle V1.0**  
© 2025 Gregor Urabl  
[https://gregorurabl.at](https://gregorurabl.at)
