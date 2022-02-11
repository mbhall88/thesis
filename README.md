### Examining bacterial variation with genome graphs and Nanopore sequencing

<!-- todo insert link to online version -->

This PhD thesis was completed under the supervision of Zamin Iqbal at the [European Bioinformatics Institute (EMBL-EBI)][EBI]. The degree is conferred by the University of Cambridge. Funding was provided by the [EMBL International PhD Programme][EIPP].

- [Abstract](#abstract)
- [Executive summary](#executive-summary)
- [Chapters](#chapters)

## Abstract

A bacterial species' genetic content can be remarkably fluid. The collection of genes found within a given species is called the pan-genome and is generally much larger than the gene repertoire of a single cell. A consequence of this pan-genome is that bacterial genomes are highly adaptable and thus variable.

The dominant paradigm for analysing genetic variation relies on a central idea: all genomes in a species can be described as minor differences from a single reference genome, which serves as a coordinate system. As an introduction to this thesis, we outline why this approach is inadequate for bacteria and describe a new approach using genome graphs.

In the first chapter, we present algorithms for *de novo* variant discovery within such genome graphs and evaluate their performance with empirical data. The remaining chapters address a question relating to a critical bacterial pathogen: can Nanopore sequencing of *Mycobacterium tuberculosis* provide high-quality public health information? We collect data from Madagascar, South Africa, and England to help answer this question. First, we assess outbreaks identified using single-reference and genome graph methods. Second, we evaluate antimicrobial resistance predictions and introduce a framework for using genome graphs to improve current methods. Lastly, we train an *M. tuberculosis*-specific Nanopore basecalling model with considerable accuracy improvement.

Together, this thesis provides general methods for uncovering bacterial variation and applies them to an important global public health question.

## Executive summary

We begin this thesis in Chapter 2 by describing algorithms to facilitate the *de novo* discovery of variants in a ([`pandora`][pandora]) genome graph. We first calibrate this method, and associated parameters, on a simulated dataset. Next, we use an empirical dataset of 20 diverse *E. coli* genomes with Illumina and Nanopore data to evaluate the precision and recall of `pandora`, with and without *de novo* variant discovery. We additionally show that `pandora`'s representation of a pan-genome as a genome graph provides superior recall to single-reference methods and a substantially lower Nanopore error rate than existing methods.

For the remainder of the thesis, we turn our attention to *M. tuberculosis* and investigate how genome graphs and Nanopore sequencing can improve public health applications for this pathogen. In Chapter 3, we provide a detailed analysis of Nanopore-based transmission cluster inference. Using a diverse dataset of 150 *M. tuberculosis* clinical isolates, we show that BCFtools SNP calls from Nanopore data produce transmission clusters that are highly concordant with those inferred from Illumina and do not miss any samples from their expected cluster. Additionally, we explore the efficacy of `pandora` for constructing transmission clusters and find that while no samples are missed from their expected clusters, more work is needed to prevent the merging of separate clusters.

In Chapter 4, we outline a method for drug resistance prediction with `pandora` reference graphs ([`drprg`][drprg]). We compare this method and [`mykrobe`] against available first- and second-line drug phenotypes for the 150 samples from Chapter 3. As a result, we simultaneously show that Nanopore whole-genome sequencing antimicrobial resistance predictions are concordant with Illumina and `drprg` predictions are consistent with `mykrobe`. We also find the major sources of error for both `mykrobe` and `drprg` with Nanopore data and investigate. In addition, we measure `drprg`'s ability to detect off-catalogue mutations and find that it leads to less missed resistance predictions.

Finally, in Chapter 5, we train an *M. tuberculosis*-specific Nanopore basecalling model and illustrate its increased read- and consensus-level accuracy over the default basecalling model. Furthermore, we show that our species-specific model reduces homopolymer deletion errors - an error type we encounter multiple times in this thesis.

## Chapters

Chapter 1: Background

Chapter 2: Variant discovery in genome graphs

Chapter 3: Nanopore sequencing for *M. tuberculosis* transmission clustering

Chapter 4: Predicting *M. tuberculosis* drug resistance

Chapter 5: Improving Nanopore sequencing accuracy for *M. tuberculosis*

---

> This thesis was built on top of the [CUED latex template][template], with alterations.

[EBI]: https://www.ebi.ac.uk/
[EIPP]: https://www.embl.org/about/info/embl-international-phd-programme/
[template]: https://github.com/kks32/phd-thesis-template
[pandora]: https://github.com/rmcolq/pandora
[drprg]: https://github.com/mbhall88/drprg
[mykrobe]: https://github.com/Mykrobe-tools/mykrobe
