# Galaxy Collision Simulation

A Python project for visualising the gravitational encounter of two spiral galaxies.

The simulation uses a restricted N-body method inspired by Toomre & Toomre (1972). Each galaxy is represented by a massive core surrounded by many massless star particles. The particles feel the gravity of both galaxy cores, while the two cores also attract each other.

The goal is to create a lightweight but visually engaging galaxy-collision simulation that can show tidal tails, bridges, and merger-like structures without using a full astrophysical simulation package.

![Preview](preview.png)

---

## Overview

Galaxy collisions are mainly driven by gravity. Even though stars inside galaxies are separated by huge distances, the overall gravitational field of one galaxy can strongly distort another galaxy during a close encounter.

This project demonstrates that idea using a simplified numerical model. It is not intended to replace professional galaxy simulations, but it is useful for science outreach, visualisation, and understanding the basic physics behind interacting galaxies.

The rendering is also handled directly in Python, with a custom visual pipeline for glow, bloom, motion trails, and cinematic colour grading.

---

## Physics model

The code uses a restricted N-body approximation:

- Each galaxy has one massive central core.
- Each disk contains thousands of massless star particles.
- Star particles feel gravity from both galaxy cores.
- Star particles do not attract each other.
- The two galaxy cores interact gravitationally.

This reduces the computation from a full pairwise N-body problem to a much lighter calculation, making the simulation practical on a normal laptop.

The motion is integrated using a leapfrog scheme, which is commonly used for orbital systems because it is more stable than a simple Euler update.

---

## Galaxy structure

Each galaxy disk is generated with:

- an exponential radial profile,
- a simple spiral-arm pattern,
- a softened rotation curve,
- random stellar brightness variation,
- a small number of brighter stars for visual highlights.

One galaxy is tilted relative to the other to make the encounter look more three-dimensional in projection.

---

## Rendering

The final animation is rendered using a custom Python-based pipeline rather than Blender or a game engine.

The renderer includes:

- additive light accumulation,
- sub-pixel star splatting,
- Gaussian bloom at multiple scales,
- diffraction spikes around bright stars,
- motion trails from previous frames,
- soft background nebulosity,
- vignette and filmic tone mapping.

This gives the output a more cinematic look than a standard scatter plot.

---

## Main parameters

The behaviour of the collision can be changed by editing the parameters near the top of the script.

Useful parameters to experiment with:

- `INITIAL_SEP` — starting distance between the two galaxy cores.
- `IMPACT_PARAM` — how direct or off-centre the encounter is.
- `APPROACH_VEL` — approach speed of the galaxies.
- `M1`, `M2` — masses of the two galaxy cores.
- `N1`, `N2` — number of star particles in each galaxy.
- `INC2` — tilt angle of the second galaxy.
- `VIEW_START`, `VIEW_END` — camera zoom range.

Smaller impact parameters usually create stronger tidal disruption. Higher approach velocities produce faster flybys, while lower velocities can lead to a more merger-like encounter.

---

## Limitations

This is a simplified educational and visual simulation.

It does not include:

- dark matter halos,
- gas dynamics,
- star formation,
- particle-particle self-gravity,
- hydrodynamics,
- realistic stellar evolution.

The simulation is useful for showing the gravitational origin of tidal tails and galaxy distortion, but it should not be treated as a precision astrophysical model.

---
