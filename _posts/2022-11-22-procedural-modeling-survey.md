---
title: "An overview of Smelik, Ruben M., et al. (2014) 'A survey on procedural modelling for virtual worlds'"
categories:
    - Thesis
tags:
    - Procedural Modeling
    - Survey
    - L-Systems
    - Shape Grammars
    - Inverse Procedural Modeling
    - Sketch-Based Procedural Modeling
---

## Disclaimer:

- This post serves as a mere summary of the aforementioned research paper for organizational purposes which will hopefully come in useful for the completion of my thesis' report
- I will carefully attempt to appropriately cite and quote the authors' work so that their intellectual property is preserved
- As a natural side effect of the paper's publication date, the notion of time relative to that of grammatical conjugation within this overview might not old true to current standards
- Details regarding technically heavy terminology and implementation are excluded from this overview and will be reserved for future analysis
- Personal comments of my authorship (if any) with regards to the research paper in question will be clearly delimited from the overview in the **'Comments and more'** section

## Overview:

The *Smelik, Ruben M., et al. (2014) 'A survey on procedural modelling for virtual worlds'* paper surveys procedural methods applied to a myriad of areas inherent to the virtual worlds domain and identifies aspects pertaining to procedural modeling that may contribute to its lack of widespread acceptance among non-technical and creative professionals. Additionally, the survey analyzes two important features relative to each procedural method that are crucial to its end users - the method's degree of intuitive control and of interactivity - and also highlights promising research results within this field. 

Due to my thesis' scope, this overview will solely focus on the survey's references to procedural methods applied to buildings.

## Main goals of this paper:

In this survey, *Smelik, Ruben M., et al. (2014)* aim at addressing the following topics:
- Introduction of procedural methods
- Classification of procedural methods 
- Overview of procedural modeling advancements
- Evaluation of procedural methods according to a pre-determined criteria
- Identification of open issues
- Identification of promising research paths

*Smelik, Ruben M., et al. (2014)* categorize procedural models as generative representations of the following:
- Nature inspired processes
- Man-centered processes

Additionally, *Smelik, Ruben M., et al. (2014)* established a set of criteria to evaluate each procedural method:
1. Intuitiveness and ease of use
2. Degree of user control
3. Classifications (e.g., grammars, data-driven, etc) and scope of application (e.g., buildings, terrain, etc)

## Advantages of Procedural Modeling:

*Smelik, Ruben M., et al. (2014)* enumerated the following advantages associated to procedural modeling:
- Data amplification - The procedural model's ability to produce a broad variety of outputs stemming from a few generation rules and a simple set of inputs
- Data compression - Geometric models can be represented by functions and respective parameters and its 3D model can then be generated on-demand
- Productivity gain - The potential to significantly reduce the amount of modeling effort when modeling 3D assets

## Challenges of Procedural Modeling:

Despite the numerous benefits that procedural modeling has brought to creative professionals, *Smelik, Ruben M., et al. (2014)* observe that procedural methods do not yet represent a satisfying enough alternative to manual modeling due to relevant challenges yet to overcome, namely:
- Non-intuitive rules and input parameters where the slightest parametric modification can lead to unpredictable results - which results in procedural methods purposefully limiting user controllability 
- Heterogenous procedural methods typically do not work together - which means that integrating these models involves extensive manual effort

This leaves a substantial and unwanted side effect in procedural modeling - the fact that end users either reuse provided models or randomly tweak a model's parameters until they achieve an acceptable output.

## Procedural Modeling applied to buildings:

With regards to procedural modeling applied to buildings, *Smelik, Ruben M., et al. (2014)* consider it one of the best-developed procedural modeling areas and enumerate the most recurrent methods within this subdomain:
- L-Systems
- Split Grammars
- Shape Grammars

*Smelik, Ruben M., et al. (2014)* also refer to procedural façade generation - a sub-area of building generation where the modeling of façades is structured upon split grammars combined with forward and inverse modeling approaches.

*Smelik, Ruben M., et al. (2014)* enumerate the following papers:
- *Parish, Yoav IH, and Pascal Müller. (2001) "Procedural modeling of cities."* (useful to produce simple building offices)
- *Greuter, Stefan, et al. (2003) "Real-time procedural generation of 'pseudo infinite' cities."* (useful to produce simple building offices)
- *Wonka, Peter, et al. (2003) "Instant architecture."* (a parametric context-free split grammar to produce building models)
- *Müller, P. et al (2006) ‘Procedural modeling of buildings’* (an extension of split grammars to computer generated architecture)
- *Yong, Liu, et al. (2004) "Semantic modeling project: Building vernacular house of southeast China."* (an extended shape grammar to create vernacular-style Chinese houses)

Despite the ability of shape grammars to generate high visual fidelity models, they lack semantic information regarding each shape's role within the building. As such, *Smelik, Ruben M., et al. (2014)* mention *Finkenzeller, Dieter, and Jan Bender. (2008) "Semantic representation of complex building structures."* approach to capture this semantic information.

Additionally, *Smelik, Ruben M., et al. (2014)* mention that defining suitable shape grammars is a complex process and refer to recent approaches that aim at addressing that problem:
- *Lipp, Markus, Peter Wonka, and Michael Wimmer. (2008) "Interactive visual editing of grammars for procedural architecture."* (a visually interactive system for shape grammar editing)
- *Silva, Pedro Brandão, et al. (2013) "Node-based shape grammar representation and editing."* (a dataflow graph representation to provide grammar structure awareness)

Finally, despite *Smelik, Ruben M., et al. (2014)* recognition that these methods are capable of generating buildings with a high level-of-detail, and referring to shape grammars as the most developed and compact method for representing buildings, they mention the methods' inherent necessity for authoring effort in order to produce acceptable outputs.


## Available Systems for Procedural Modeling:

With the aforementioned aspects of *Smelik, Ruben M., et al. (2014)* survey taken into consideration, the authors list a set of both commercially and freely available procedural modeling tools which they consider to be representative of the state of art. As such, for procedural modeling of buildings, we have the following tools:

**[CityEngine](http://www.esri.com/software/cityengine/)** - A city generator based on *Müller, P. et al (2006) ‘Procedural modeling of buildings’* CGA Shape that allows for interactive modeling, user assisted writing, and interpretation of CGA rules.

**[Houdini](http://www.sidefx.com/)** - A versatile tool for creating procedural methods via a visual editor composed of a graph of geometric and mathematical operations.

## Possible directions for tackling with Procedural Modeling challenges:

Taking into consideration the previously mentioned challenges, *Smelik, Ruben M., et al. (2014)* highlight a set of approaches aimed at diminishing the disadvantages that these challenges bring.

With the degree of intuitive control in mind, we have the following approaches:  

**Sketch-based techniques** - A system where intuitive techniques, such as sketching, serve as input to a model that derives its parametric features - putting it among the most promising approaches to interactive procedural modeling and bringing it closer to creative professionals who recurrently use sketching as a means of expressing their ideas

**Visual editors** - Visual node-based editors representing the flow of data that is being processed (e.g., geometric and mathematical operations) that aim at automating the generation of grammar production rules

**Inverse procedural modeling** - An approach that attempts to find a procedural representation of a given input (e.g., finding a model's rules and parameters) whose main advantage is that it leaves the designer outside of the process. Apart from that advantage, the remaining disadvantages and advantages of procedural modeling remain

However, when it comes to integrating heterogenous procedural methods, *Smelik, Ruben M., et al. (2014)* warn that, in order to design complete virtual worlds, heterogenous content will have to be implemented and maintained together within a framework or engine. Additionally, *Smelik, Ruben M., et al. (2014)* point out that there is no current mechanism capable of solving this challenge - making it a promising area for future research which will likely be instrumental for the procedural modeling domain.

## Comments and more:

*Smelik, Ruben M., et al. (2014)* present a valuable and broad overview of procedural modeling methods with the purpose of providing a structured state-of-the-art review while highlighting interesting approaches that aim at exploring possible solutions to inevitable challenges associated to procedural modeling. However, it is worth noting the survey's publication date (2014) as it is only natural that, in the span of 8 years, an extensive body of research might have been conducted.

Additionally, it is crucial to trace a strict distinction between the end users that the authors describe - non-technical and creative professionals - and the end users which my thesis will aim at addressing - architects that resort to computer aided design (whose skill set, in my opinion, belong to both the creative and technical domain). 

Taking that distinction into consideration, a fundamental change of perspective arises when considering the challenges enumerated by *Smelik, Ruben M., et al. (2014)*, more specifically, the level of comprehension concerning a given user with regards to modeling via functions and respective parametric changes that can be preformed by the means of procedural methods.  

As such, one can argue that architects have a clear understanding of both mathematical and geometric operations that are commonly used to define simple shapes, complex shapes, and respective combinations that can be performed in order to achieve the desired outcome. Naturally, this translates to a high-level of comprehension when it comes to the mapping of these operations to computer aided design - as most, if not all, of these operations are the common denominators of procedural modeling. For that matter, the only problem remaining for architects to efficiently resort to procedural modeling tools is to grasp the simple concepts associated to programming languages, namely function definition, arithmetic operations, and possible use of libraries specifically oriented to architectural modeling - this problem is already being explored in academia, as courses specifically designed to provide a solid background of programming fundamentals is becoming transversal to many technologically reliant areas (e.g., engineering, among others)

Moreover, one recurrent concept for the procedural modeling of buildings, which the architectural domain is familiar with, is shape grammars. As *Smelik, Ruben M., et al. (2014)* referred, and rightly so, defining and maintaining shape grammar rules is quite complex. As such, *Smelik, Ruben M., et al. (2014)* mention visual editors resorting to dataflow graphs as an approach that aims at addressing this problem. However, in my opinion, these naturally lead to increasingly complex relationships between nodes of this graph that, as the modeling progresses, ultimately lead to insurmountable visual clutter that may hinder the modeler's overall comprehension associated to their project.

Finally, it is worth highlighting the main advantage associated to procedural modeling enumerated by *Smelik, Ruben M., et al. (2014)*:

**Data amplification** - Which I believe holds great potential to explore alternative creative paths when projecting architectural ornaments and structures to a given building, such as combining different architectural styles to create an eclectic building, or even for architects to be surprised by the multitude of different combinations that can be produced by procedural methods (from which they may draw inspiration)