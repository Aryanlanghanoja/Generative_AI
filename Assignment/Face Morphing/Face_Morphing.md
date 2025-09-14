# Triangulations and Face Morphing – Summary

## Introduction
- Face morphing is widely used in apps and media, enabling smooth transformation from one face to another.  
- Mathematical tools make morphing possible; one of the simplest is **morphing triangulations**.  
- Process:  
  - Identify key facial points (e.g., nose tip, mouth corners).  
  - Create a triangulation of these points.  
  - Morph one triangulated structure into another while preserving planarity.  

---

## Historical Foundations
- **1944 – Cairns**:  
  - Proved two equivalent triangulations can be morphed without edge crossings.  
  - Method: contract low-degree vertices.  
  - Drawback: required **exponential steps**.  
- **1983 – Thomassen**:  
  - Extended to all **planar straight-line drawings** (not only triangulations).  
  - Method: augmented input drawings into isomorphic triangulations, then applied Cairns’ result.  

---

## Algorithmic Developments
- **1999 – Floater & Gotsman**:  
  - Introduced method based on **Tutte’s graph drawing algorithm**.  
  - Extended in 2001 by Surazhsky & Gotsman.  
  - Limitation: provided only **snapshots** at time points, not continuous vertex trajectories.  
- **2017 – Alamdari et al.**:  
  - Major breakthrough: algorithm for morphing planar graphs using **linear number of steps**.  
  - Each step = **unidirectional linear morph** (each vertex moves at constant speed along a straight line, though speeds differ).  
  - Proved the linear complexity is **worst-case optimal**, improving drastically over Cairns’ exponential bound.  

---

## Core Methodology
- **Two-step approach**:  
  1. Solve for **triangulations**.  
  2. Reduce general planar straight-line drawings to triangulations.  
- For triangulations:  
  - Similar to Cairns – find a vertex *v* that can be contracted to neighbor *u* without crossings.  
  - Recursively apply contraction on smaller graphs.  

---

## Challenges and Solutions
- **Issue 1 – Suitable vertex may not exist**:  
  - Solution: choose an **interior vertex of degree ≤ 5** (always exists in planar graphs).  
  - Morph neighbors of *v* into a polygon where a chosen neighbor *u* can “see” the entire polygon.  
  - Reduces Cairns’ exponential steps to just **two**.  
- **Issue 2 – Avoid coincident vertices**:  
  - Cairns’ solution required nonlinear motion.  
  - Alamdari et al. use a new method ensuring vertices come “close enough” without overlap.  

---

## Quadrilateral Convexification Problem
- Key subproblem: given a triangulation containing a **nonconvex quadrilateral**, morph it into convex shape.  
- Let quadrilateral vertices = (a, b, c, d).  
  - *c* = reflex vertex (interior angle > 180°).  
  - *a* = tip of arrowhead shape.  
  - Edge *ac* must be part of triangulation.  
- Strategy:  
  - Reorient so *ac* is nearly horizontal.  
  - Apply **Hong & Nagamochi’s result**: redraw plane graph using **only horizontal vertex movements** to achieve convex faces.  

---

## Significance
- Combines work of **13 researchers** over multiple papers, culminating in Alamdari et al. (2017).  
- Demonstrates the power of **collaboration over competition** in solving long-standing mathematical problems.  
- Advances understanding of planar graph morphing, with implications in:  
  - Face morphing software.  
  - Computational geometry.  
  - Graph drawing and visualization.  
- Represents a solution to a problem studied for over **a century**.  
