---
title: "An overview of Müller, P. et al (2006) 'Procedural modeling of buildings'"
categories:
    - Thesis
tags:
    - Shape Grammars
    - L-Systems
---

## Disclaimer:

- This post serves as a mere summary of the aforementioned research paper for organizational purposes which will hopefully come in useful for the completion of my thesis' report.
- I will carefully attempt to appropriately cite and quote the authors' work so that their intellectual property is preserved.
- As a natural side effect of the paper's publication date, the notion of time relative to that of grammatical conjugation within this overview might not old true to current standards.
- Details regarding technically heavy terminology and implementation are excluded from this overview and will be reserved for future analysis.
- Personal comments of my authorship (if any) with regards to the research paper in question will be clearly delimited from the overview in the **'Comments and more'** section

## Overview:

The *Müller, P. et al (2006) "Procedural Modeling of Buildings"* paper presents a shape grammar, *CGA shape*, for the procedural modeling of buildings and demonstrates solutions to previously unsolved problems constituting important benefits to both the entertainment and architectural domain, namely low cost production and efficient generation of massive urban models with a high level-of-detail (LOD).

## Challenges that motivated this paper:

*Müller, P. et al (2006)* identified a set of challenges that served as a motivational force to propose a solution:
1. Modeling large 3D environments is both laborious and expensive
2. Previous solutions *(Parish and Muller (2001))* were not able to generate sufficient geometric detail to buildings and were prone to unwanted intersections of architectural elements
3. Split rules *(Wonka et al (2003))* are only sufficient for simple mass models, mass models can't be easily changed, and objects of arbitrary orientation cannot be easily handled
4. Deriving shape grammars is extremely complex and either done manually, or by computer, with external human help 
    - Solution: Simplifying shape grammars to set grammars to facilitate computer implementation *(Wonka et al (2003))*

## Major contributions:

The *Müller, P. et al (2006). "Procedural Modeling of Buildings"* paper constitutes important contributions:
1. *CGA shape* - An extension of set grammars introduced by *Wonka et al (2003)*
2. A procedural approach to model highly detailed buildings with consistent mass models without being restricted to axis aligned shapes while, at the same time, including roof surfaces and rotated shapes
3. Application related details in the context of procedural modeling of buildings - shape rules definition, concise notation, modeling strategies

## An overview of *CGA shape*:

On a general view, *Müller, P. et al (2006)* proposal is powerful enough to specify complex shapes:
1. Building mass models are constructed as a union of volumetric shapes and a combination of operations - scaling, translation, splits
2. Arbitrary rotations of shapes
3. Cylinder inclusion in the shape vocabulary
4. Inclusion of basic roof shapes - Gambrel, cone, gabled, hipped, cross-gable, mansard

According to *Müller, P. et al (2006)*, shape formulation via *CGA shape* follows the below-mentioned principles:
1. Representation of shapes via:
    - Symbol (string) - Terminal/ Non-terminal symbols
    - Geometric and numeric attributes - Positional vectors, cartesian vectors, and size that, together, comprise an oriented bounding box (scope)
2. Shape replacement via production rules

As a result, *CGA shape* is able to generate buildings with high visual fidelity by employing production rules that obey the following iterative process:
1. Create the building's volumetric model (mass model)
2. Construct its façade
3. Add details for windows, doors, and ornaments

As referred by *Müller, P. et al (2006)*, this process constitutes a major benefit - the creation of an hierarchical structure that allows reusing production rules for procedural variations

## Mass model construction:

*Müller, P. et al (2006)* propose two possible ways to construct a mass model:
1. Building lot as an axiom of the grammar
    - Generate mass models via scaling, translation, rotation, and split operations while being careful not to protrude parcel boundaries
2. Importing from GIS database or architectural model
    - Attempt at classifying the imported model as basic shapes already defined in the shape vocabulary. If such an approach proves impossible, it uses general extruded footprint together with a general roof obtained by straight skeleton computation
    - Problem: Restrictive when it comes to modifications in the mass model

## Façade construction:

With regards to directly computing visible façade surfaces, *Müller, P. et al (2006)* enumerate the following problems:
- Visible surfaces can be general polygons (not necessarily trivial to compute)
- Writing meaningful shape rules for general polygons is not straightforward
- Assigning non-terminal symbols for the façade grammar is not trivial (mainly outputs of algorithms and not of production rules)

As such, in order to overcome the aforementioned challenges, *Müller, P. et al (2006)* propose a modeling strategy that works for arbitrarily aligned polygons:
1. 2D scopes generation aligned with façade and roof surfaces by extracting the faces of 3D shapes with a component split
    - This keeps the resulting 2D faces correctly aligned and parametrized
    - Similarly, edge extraction can be performed by generating 1D scopes
2. Refinement of resulting quads and triangles through the grammar

As mentioned by *Müller, P. et al (2006)*, this model allows to work on many configurations of mass models, while retaining the necessary simplicity for procedural modeling.

Additionally, *Müller, P. et al (2006)* mention that after a shape is reduced to 2D, it is often replaced by 3D through subsequent rule application. As such, for the sake of consistency, they propose two solutions:
1. Testing spatial overlap (occlusion)
2. Testing nearby important lines and planes in the shape configuration (snap lines)

### Occlusion

*Müller, P. et al (2006)* propose a solution to avoid placing façade elements on the intersection of the mass model's volumetric shapes by employing the following mechanisms:
- Occlusion queries that test for intersections between shapes
    - No occlusion
    - Partial occlusion
    - Full occlusion
- There are several variations to query subsets of a shape's configuration
    - Occlusion against all shapes (even inactive ones)
    - Occlusion against shapes with a specific label
    - Occlusion against all shapes except the selected shape's predecessors
- The intersection type can also include distance for analyzing occlusions when enlarging a model

### Snapping

To further improve the layout of the façade's structure, *Müller, P. et al (2006)* propose a mechanism to be performed in 2D faces of volumetric shapes, as detailed below:
- Alter existing shape rules to snap to a dominant face or line in the shape configuration (snap shapes)
- There are two types of splits that snap lines can be applied to:
    - **Repeat split:** Scope division and repeat rule invocation to each divided part via snap lines
    - **Subdivision split:** The closest split is altered via snap lines (everything else is kept unchanged)

## Discussion:

*Müller, P. et al (2006)* also enumerate relevant advantages, disadvantages, and differences of *CGA shape* when compared to other solutions, such as:

### Comparison to mesh modeling tools:

- Existing commercial scripting tools to accelerate modeling processes can only replicate parts of *CGA shape*
- *CGA shape* models are significantly more detailed than modeling practices in the entertainment industry
- Despite *CGA shape's* strengths, generating smaller complex geometric details is sometimes inefficient
- *CGA shape* drastically reduces modeling times.

### Efficiency and robustness:

- Complex and error-prone geometric operations do not have to be executed
- Good tradeoff between visual quality and speed
- Fast shape grammar derivation (one billion polygon models can be generated in less than one day)
- Disadvantage - Procedural approach might generate implausible shape configurations
    - Potential for future research - Shape grammars for shape understanding

### Usability:

- Learning curve similar to that of other scripting languages
- Carelessly written rules might produce unwanted side effects
- *CGA shape* is most naturally understood by people with a background in Computer Science

### Architecture and computer graphics:

Application to architectural design is yet to be explored and might require significant changes (e.g. adapting architectural concepts and deriving a set of specific rules)

### Comparison to L-Systems:

#### Similarities:

- Notation of rules
- The idea of scope corresponds to an evolution of the L-System turtle
- Necessity of context sensitive rules

#### Distinctions:

- Shapes instead of strings
- Rules replacing shapes with shapes instead of string replacement
- Shape rules non-existing in L-Systems
- L-Systems are oriented towards biological systems which do not directly relate to the modeling of buildings
- Direct application of L-Systems to architecture emphasizes the idea of growth (counterproductive for procedural modeling of buildings)

### Real-time rendering:
- Requires post-processing algorithms not yet developed
    - This poses an interesting challenge - develop LOD techniques for massive city models

## References:  
*Müller, P., Wonka, P., Haegler, S., Ulmer, A., & Van Gool, L. (2006). Procedural modeling of buildings. In ACM SIGGRAPH 2006 Papers (pp. 614-623).*