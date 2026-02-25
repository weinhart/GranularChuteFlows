# GDR-MiDi Inclined Plane Flow --- ON-DEM Benchmark

The official benchmark description explains the physics and validation quantities:\
https://on-dem.atlassian.net/wiki/spaces/Index/pages/432996353/Physical+validation+of+DEM+comparison+with+GDR-MiDi+inclined-plane+flow+experiments

This repository provides the **initial configuration and run
protocol** for participating in the ON-DEM inclined-plane granular flow
validation.

This file explains **exactly how to run the simulation and what to
submit**.

------------------------------------------------------------------------

## 1. The case study

We will run chute flows with varying inclinations and heights. In total we run ten cases:
- height 20, 18, 16, 14 at inclination 21 degree; the flows of height 20 and 18 should arrest, whereas the flows at height 16 and 14 should flow (though there might be some variation).
- height 40 at inclinations 18, 20, 22, 24, 26, 28 degree; the flow of inclination 18 should arrest, whereas the flows at inclinations 20, 22, 24, 26, 28 degree should flow.

A full diagram of what heights and inclinations should arrest can be found here (Figure 4):
https://link.springer.com/article/10.1007/s10035-012-0355-y
The first case study tests whether we observe the same h_stop(theta) dependance in all flows, see Figure 4; the second case study shows whether we can recover the flow rule F(h/h_stop), see Figure 12.

------------------------------------------------------------------------

## 1. Initial configuration

To run each case, use the provided data files:

`InitialConfiguration/H*A*.data`

This file defines the initial particle positions (columns 1-3) and radii (column 7) of the particles.

The first **114 particles** are the rough base; their positions must remain fixed. All remaining particles are flowing grains, and should be free to move.

The parameters of the simulations are described in the benchmark description (and can also be found in the paper referenced above). For clarity, I have also attached a file with all simulation settings: `InitialConfiguration/H40A24.restart`. Participants should reproduce these parameters as closely as possible in their own DEM code.

A description of the .data and .restart file formats can be found here: https://tiplath.github.io/docs.mercurydpm.github.io/db/da1/VisualisingYourResults.html#UnderstandingTheOutputFiles

------------------------------------------------------------------------

## 3. Running the simulation

Run the simulation until time `t=2500`

The system should reach steady flow at `t=2000`.

------------------------------------------------------------------------

## 4. Output to submit

Participants must export particle data during the steady regime.

Save particle **positions and velocities** at `t = 2000 : 10 : 2500`

This produces **51 output files**.

Each file must contain particle positions and volocities. Please use the .data file format, described above. An example output is provided here: `SampleOutput/H40A24.data.*`

------------------------------------------------------------------------

## 6. Submission

Upload:

1.  the 51 data files for each of the ten cases
2.  DEM code name and version

Do **not** upload post-processed data.\
Only raw particle data will be used for analysis.

------------------------------------------------------------------------

## 7. Notes

The purpose of this benchmark is cross-code comparison.\
Reproducing the initial state and output times exactly is essential;
otherwise results cannot be compared.
