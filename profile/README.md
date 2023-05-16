# AmpliconSuite

## What is AmpliconSuite?
AmpliconSuite is a collection of related tools for studying focal amplifications in cancer genomes. Somatic focal copy number amplifications can be mediated by extrachromsomal DNA (ecDNA), breakage fusion bridge (BFB) cycles or other complex mechanisms of genome rearrangement followed by amplification (e.g. chromothripsis + amplification).

At the core of AmpliconSuite is AmpliconArchitect (AA), a joint structural variation (SV) and copy-number (CN) analysis tool which extracts computational substructures of genomic focal amplifications using paired-end whole genome sequencing (WGS) data. AmpliconArchitect was developed in Vineet Bafna's lab by Viraj Deshpande. The substructures reported by AA can be classified according to generative mechanism using AmpliconClassifier.

To improve reproducibility of the outputs and simplify their interpretation, we created AmpliconSuite-pipeline, which wraps the relevant tools into a single workflow. Please use AmpliconSuite-pipeline to wrap the running of AmpliconArchitect.

## What tools are part of AmpliconSuite and what do they do?
### AmpliconArchitect (AA)
Performs joint analysis of SVs and copy numbers to analyze the genome structure of focal amplifications and reports computational substructures. In some simple cases, the substructure will represent a complete ecDNA structure itself. Developed by Viraj Deshpande, maintained by Jens Luebeck. 

### AmpliconClassifier (AC)
Takes the outputs of AA and predicts the mechanism of focal amplification, and reports annotations such as the genome regions in the focal amplification, the genes present, the estimated copy numbers (bulk, not subclonal) and other properties including complexity and similarity scores.

### [AmpliconSuite-pipeline](https://github.com/AmpliconSuite/AmpliconSuite-pipeline)
Wraps the input preparation steps (PrepareAA.py), AA and AC analysis in one workflow containing our current best practices. Please use AmpliconSuite-pipeline to invoke AA instead of trying to run AA as a standalone module. PrepareAA applies multiple filters to ensure that the collection of seed regions AA takes as input are properly identified.

### AmpliconRepository
AmpliconRepository.org is an online platform for community sharing of AmpliconArchitect outputs and classification files. Developed in collaboration between members of the Vineet Bafna lab, Jill Mesirov's lab and the GenePattern team at UC San Diego.

## Other utilities
**[CycleViz](https://github.com/AmpliconSuite/CycleViz)**: Create circular visualizations of AA-identified focal amplification substructures, such as for ecDNA, and optionally show user-supplied genome track annotations. Can also support non-AA derived genome visualizations given a bed file.

**AmpliconReconstructor**: Combines Bionano optical genome map assemblies with AmpliconArchitect to infer larger-scale scaffolds of the focal amplification structure.

**AmpliconSuiteAggregator**: Takes AmpliconSuite-pipeline output files and prepares them for upload to AmpliconRepository.


