# Summary and implications
[TODO: fill out this section. This is just a start...]
Accurate representations of clouds in large-scale (global) climate models is of critical importance, but has remained elusive for model developers. An important test of the fidelity of models is the comparison of simulated climate against available observations of the physical climate. For cloud properties, this often means comparison with satellite-retrievals, but these types of comparisons have traditionally been challenged by fundamental limitations in both the satellite retrieval process and in the model formulation of clouds. An increasingly common approach to reconcile these limitations is to use the simulator framework, whereby psuedo-retrievals are simulated from model cloud fields to account for some of the known features and limitations of specific satellite retrievals. While this approach has been nominally enabled more consistent comparisons between modeled and observed cloud properties, it has been demonstrated in this dissertation that limitations in both the retrievals and in the models themselves remain unaccounted for, and in particular limitations on the model side introduce an additional layer of uncertainties that need to be accounted for.

As described in Chapter 1, the simulation of satellite-retrieved cloud properties from the description of clouds provided by a large-scale model is a multi-step process, involving 1) downscaling model gridbox-mean quantities to scales approximating satellite pixels, 2) simulating the individual satellite retrievals, and 3) aggregating the pixel-scale psuedo-retrievals into statistical summary products analogous to those produced for the individual satellite instruments. In general there can be uncertainties associated with each of these steps, and in this study the performance of the simulator framework has been evaluated separately for both steps 1) and 2).

[discuss errors on pixel-scale] The performance of the MISR simulator was evaluated by comparing psuedo-retrievals simulated from CloudSat and CALIPSO data with retrievals from MISR. It was shown that the MISR simulator is able to correct for many of the features of the MISR retrieval, and in general cloud top heights retrieved from CloudSat and CALIPSO are in much better agreement with MISR after using the MISR-simulator to account for the features of the MISR retrieval. In particular, mid and high-topped clouds are in agreement between MISR and CloudSat/CALIPSO retrievals when using the MISR simulator. Large differences remain in total and low-topped clouds, however, due to ambiguiuties in retrieving small (sub-pixel) scale clouds. The differences highlighted here between MISR and CloudSat/CALPISO cloud area are discouraging because they represent a fundamental uncertainty in the quantification of low-topped and total cloud area, making robust comparisons of modeled cloud area with these satellite retrievals difficult. More importantly, these differences point to the fragility of cloud area as a measure of cloudiness. [TODO: elaborate here...is this appropriate? most of this work makes me think using things like cloud area as metrics for model clouds is probably not the best idea...but I don't know enough (i.e., haven't done the research) to suggest suitable alternatives. I think maybe cloud top height is robust (when using the simulator framework), but have not specifically addressed this here]

[discuss errors due to subcolumn generation assumptions]
Because current global climate models do not explicitly resolve clouds at the scales at which satellite retrievals are performed, the additional step of downscaling cloud properties to pixel scales is needed before simulating the satellite retrievals. This process depends on additional assumptions about the unresolved cloud properties. In particular, cloud (and precipitation) condensate is nearly always assumed to be horizontally homogeneous on the scale of model gridboxes, and clouds are assumed to follow a simple "maximum-random" overlap. It was shown here that MISR-simulated cloud area is sensitive to both of these assumptions, while simulated CloudSat radar reflectivity is sensitive primarily to the treatment of precipitation and to the subgrid-scale variability in condensate. These errors can be quite large regionally, and have significant consequences for the suitability of these simulators for model evaluation. In particular, the errors in CloudSat-simulated radar reflectivity that arise due to these assumptions appear to be on the order of errors indentified in models, and suggest that until these errors are corrected for, CloudSat radar reflectivities are not a suitable quantity for model evaluation.

The errors in simulated psuedo-retrievals that arise due to the generation of subcolumns from model gridbox-mean quantities can be significantly reduced with an improved subcolumn generator that accounts for both horizontal variability in condensate amount and more realistic overlap of clouds and precipitation. The performance of this improved subcolumn generator depends, however, on the specification of cloud and precipitation overlap and rank correlation statistics, as well as the subgrid-scale variance in condensate. These are all quantities which will need to be parameterized for implementing this improved subcolumn generator for use with global models. Using idealized overlap statistics and variance resulted in a significant reduction in errors, but more modest results where obtained using a simple parameterization of these quantities. Nonetheless, the improvements demonstrated using the idealized quantities shows that further work to better parameterize these quantities will be worthwhile, and that this framework can significantly improve comparisons between models and satellite retrievals.

[discuss path forward for parameterizing overlap and variance] The importance of overlap and condensate heterogeniety extend beyond just the simulation of psuedo-satellite retrievals. In particular, both of these characteristics of clouds are important in simulating radiative fluxes. This makes future work to improve the characterization of these quantities even more important. With the growing interest in statistical or PDF-based cloud schemes in large-scale models, it might ultimately make sense for subgrid-scale variance (and, perhaps, condensate probability distributions) to be specified by these schemes within the model, rather than by some external parameterization of the variance with an assumed distribution. Certainly, if such an assumption is made within the model, it makes sense for the same assumptions to be used on the diagnostic end. Regardless, it is clear that the representation (or implicit assumption) of cloud properties at scales below which are resolved by global climate models is in dire need of improvement.

[discuss subtlety of errors on diagnostic side vs errors in model formulation] It is important to note that the errors identified here are intrinsic to the model evaluation process itself, and not directly connected to inherent errors in the formulation of a particular model. In other words, these errors arise on the *diagnostic* side, not on the model side. This is significant, because it means that if these errors go unaccounted for, we may draw incorrect conclusions about the models we evaluate. 