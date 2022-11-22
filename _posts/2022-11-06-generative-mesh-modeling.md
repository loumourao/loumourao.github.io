---
title: "An overview of Havemann, Sven, and Dieter W. Fellner. (2005) 'Generative mesh modeling'"
categories:
    - Thesis
tags:
    - Procedural Modeling
    - Euler Operations
    - Boundary Representation
    - GML
---

## Disclaimer:

- This post serves as a mere summary of the aforementioned research paper for organizational purposes which will hopefully come in useful for the completion of my thesis' report
- I will carefully attempt to appropriately cite and quote the authors' work so that their intellectual property is preserved
- As a natural side effect of the paper's publication date, the notion of time relative to that of grammatical conjugation within this overview might not old true to current standards
- Details regarding technically heavy terminology and implementation are excluded from this overview and will be reserved for future analysis
- Personal comments of my authorship (if any) with regards to the research paper in question will be clearly delimited from the overview in the **'Comments and more'** section

## Overview:

The *Havemann, Sven, and Dieter W. Fellner (2005) 'Generative mesh modeling'* paper introduces a 3D modeling language - *Generative Mesh Modeling (GML)* - that aims at representing 3D shapes in such a way that effectively solves some of the disadvantages associated to common 3D modeling practices. As such, *GML's* approach to tackle these challenges is structured upon the notion of representing 3D shapes by the means of functions, and corresponding parameters, instead of geometric primitives/ polygon count. Consequently, the evaluation of a well-defined function and/ or group of functions results in the visual representation of the desired 3D shape. Moreover, *GML* has the potential of separating a model's geometric features (*content*) from ornamental aspects (*presentation*) (e.g., if given a building's window, we must be able to change its architectural style with ease by merely focusing on its ornamental aspect)

In addition to its main feature, *GML* can represent a myriad of concepts:
- Modeling history
- Separation of data and operations
- Semantic level-of-detail
- Event-driven animations
- Data-flow networks

## Challenges that motivated this paper:

*Havemann, Sven, and Dieter W. Fellner (2005)* enumerated several disadvantages associated to 3D modeling via geometric primitives:

**Modeling bottleneck:**
- High cost associated to 3D modeling
- Lack of automation in 3D modeling
- Difficulty in changing the 3D model's basic early stage shapes in late modeling periods

Taking into account the last problem, *Havemann, Sven, and Dieter W. Fellner (2005)* mention *forward modeling* as a possible alternative. However, the authors point out the unsustainable nature of such a solution due to the limited changeability and limited reusability that it brings to 3D models.

**Model file sizes:**
- The size of 3D models depends on their representation model

For that matter, *Havemann, Sven, and Dieter W. Fellner (2005)* recognize the potential of *progressive meshes* to effectively reduce a 3D model's file size. Nevertheless, the authors enumerate significant problems still remaining:
1. The complexity of the *progressive mesh* is still in the order of the input mesh
2. Post-processing mechanisms result in the loss of modeling history
3. Simplification schemes are insensitive to the structure of 3D models

**Digital libraries for 3D models:**
- The efficiency of a digital library is highly dependent of the representation formats of the models it stores

**Static virtual worlds:** 
- The static nature of most virtual worlds and 3D applications inhibiting the possibility of modifying a model's mesh 

## An overview of *GML*:

Given the aforementioned challenges and despite *GML's* possibility of representing 3D models via triangle meshes, *GML* encourages following and prioritizes the *information reduction paradigm* - only the essential information required for 3D model representation is stored - which makes the visual representation of 3D models dependent on its on-demand generation via a runtime engine, drastically reducing their corresponding file size. Additionally, due to modeling operations residing in a function's definition, complex shapes can be achieved by the composition of simple modeling operations.

With the above-mentioned factors taken into consideration, *Havemann, Sven, and Dieter W. Fellner (2005)* structure their proposal on the following principles/ techniques:
- Catmull/ Clark subdivision surfaces
- Boundary representation meshes (BRep)
- Euler operations
- Stack-based programming language

**Combined BRep Meshes (CBRep):**
Shape representation relies on CBReps and its mesh can be manipulated at runtime through Euler operators. Additionally, this form of representation has a number of benefits when compared to solely using triangular meshes, namely a higher degree of abstraction.

**Euler Operators:**
Euler operators allow for the modification of a shape's mesh by changing both its connectivity and geometry. As such, to support the modeling of any orientable manifold mesh, there are 5 possible operations followed by their inverses, comprising 10 operations in total. It is worth noting that, for each operation, ***V*** is short for *Vertex*, ***E*** for *Edge*, ***F*** for *Face*, ***S*** for *Shell*, ***R*** for *Ring*, and ***H*** for *Hole*. The operators are:
1. ***makeVEFS*** - creates a new connected component consisting of two vertices connected via a pair of half-edges - and its inverse ***killVEFS***
2. ***makeEV*** - creates an edge and a vertex - and its inverse ***killEV***
3. ***makeEF*** - splits a face by making an edge between two of its vertices - and its inverse ***killEF***
4. ***killEmakeR*** - creates a ring from an edge - and its inverse ***makeEkillR***
5. ***killFmakeRH*** - turns a smaller face into a ring of the bigger face - and its inverse ***makeFkillRH***

**Euler Macros:**
*Havemann, Sven, and Dieter W. Fellner (2005)* propose a logging mechanism to easily undo and redo operations on a model's mesh. This mechanism is responsible for storing Euler operations which when grouped together are termed as Euler macros. As such, to undo a set of Euler operations on a model's mesh, the Euler macro associated to that very set is traversed back to front with its corresponding inverse operators being executed. Moreover, it is worth noting Euler macros are stored within a macro graph, given that there is a dependency between Euler macros, more specifically - if a given operator within a macro received an input value produced by another macro, the latter macro is considered to be the parent of the former macro. As such, if one desires to undo a parent macro, the child macro must be undone first - the inverse applies for a redo operation.

***GML* and operator libraries:**
*GML* is based upon Adobe's Postscript language and, in order to appropriately execute the necessary 3D modeling operations, it makes use of a set of operations conveniently organized in *C++* libraries:
1. Core - Basic Postscript operations
2. Geometry - Vector algebra operations and additional operations for computing distances and projections
3. CBRep - Functionalities pertaining to Euler operators and Euler macros
4. Modeling - High-level modeling operations (extrude, polygon/ face conversions, among others)
5. Interaction - Input handling and visual display


## Comments and more:

*Havemann, Sven, and Dieter W. Fellner (2005)* propose an interesting and powerful approach for procedural modeling that targets the interactive aspects of 3D modeling - an extremely important aspect for *CAD* that has the potential to allow architects to explore different architectural designs to a great extent, stemming from a base structural model. However, its implementation based on Adobe's Postscript language seems rather convoluted and could be further simplified.

## References:

*Havemann, S., & Fellner, D. W. (2005). Generative mesh modeling.*