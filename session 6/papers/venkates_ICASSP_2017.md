## Accelerating Deep Convolutional Networks using low-precision and sparsity

> Title: Accelerating Deep Convolutional Networks using low-precision and sparsity 

> Conference/Journal: ICASSP

> Year: 2017

> Authors: Ganesh Venkatesh, Eriko Nurvitadhi, Debbie Marr

### Summary

The idea of adaptive interfaces is very intuitive, but (at least to me) vague and difficult to formalize. This paper presents a formal model to reason about a diverse set of what are otherwise heuristics 1. The framework models: User Task -> System Task -> Abstract UI -> Physical UI, and independently the following also contributes to the final Physical UI design

Platform: physical characteristics of the target platforms
Interactors: e.g. GUI widgets, speech sentences
Environment: context of use

### Cool Ideas

Plasticity: this is a more targeted word than adaptivity in the sense that it’s not only adaptive but also robust.
In section 4.1, the notion of priority is important: “first class objects should be observable whereas second class objects may be browsable if observability cannot be guaranteed due to the lack of physical resources”, and it seems to be more relevant for information heavy UIs (such as data visualization).
It’s neat to identify components that are not dependent on the domain concepts, these are opportunities for declarative designs.

### Questions

While the framework seems clean, I feel like to make an automatic UI design work there still needs to be a large set of input rules that specifies how the components connect.

Also when there are conflicts between the implications, it’s unclear how to best resolve — that is the system did not provide a way to reason about trade-offs. To put this in their system’s language: the correspondence matching process’ constraint resolution (1) might not be possible (2) might have multiple possibilities.

The details of the models (section 4) seem to be rather eclectic, with a couple recommendations for each model. While the recommendations seem important, it’s unclear how to build the full model.

1: this summer I have been working on something related and came up with a subset of this model — I think the framework is fairly intuitive.