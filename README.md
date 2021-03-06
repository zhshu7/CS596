# CS596 Final Project: Machine Learning Based Study of Drug Diffusion in Intravitreal Drug Delivery
Proposal
## Abstract
The liquefaction of vitreous humor has a significant effect on the diffusion of drug in the process of intravitreal drug delivery. Considering that the liquification geometry varies from person to person, it would be helpful if we can predict the drug diffusion process and further more give suggestion on the injection point and frequency for each individual. This requires a model for each individual, and a well trained deep learning model will significantly improve the efficiency comparing with doing meshing and numerical analysis for each specific case. So, in this model, the input will be the 2D liquefaction geometry of the vitreous detected by untrasound images of vitreous and the injection point, output will be the time interval that the drug is in effect, or in other words, the time interval that the concentration at the retina is within the expected range. For output, since there isn't a good indicator in clinical practice, we are planning to calculate the output based on numerical models for the limited number of cases and get the result based on the numerical simulation. Another option of the output is visual acuity 

## Introduction
##### Intravitreal drug delivery
The retina is the light-sensitive nerve layer that senses light inside eye. It has macula at the center with high concentration of optical nerves that facilitates fine, detailed vision [[1]](#1). Since most of the age-related eye diseases are concerned with the retina, it is important that therapeutic drugs are targeted to that region. In this regard, intravitreal drug delivery has gained primacy among clinicians over topical delivery. Since only a fraction of a drug makes it to the retina, it is both wasteful and risky in spreading unnecessary toxicity in healthy tissue. However, in clinical practice, the injection position and frequency are totally based on doctor’s own judgement. In this regard, it is important to establish a model that can provide a reliable prediction for the intravitreal drug delivery process and give reasonable suggestions for the injection position and frequency for a better outcome.

The intravitreal drug delivery has vitreous as the media for delivering the drug after injection. The vitreous humor is a gel-like material that is 99% water in a meshwork of collagen and hyaluronic acid [[2]](#2)-[[5]](#5), encased by the hyaloid membrane, thus can be treated as a fully saturated porous medium. While during aging, pockets of liquid appear within the central vitreous that gradually coalesce and eventually progress to posterior vitreous detachment (PVD) [[7]](#7)[[8]](#8) as shown in [Fig. 1](#Fig1). The liquid when separated from the fiber appears almost Newtonian [[9]](#9). With measurements of the hydraulic conductivity of vitreous [[9]](#9)[[10]](#10) and diffusion coefficient of drugs with different molecular weights in the vitreous [[11]](#11), the drug transport in the partially liquified vitreous body can be simulated with numerical models with spherical partial liquefaction region by treating the gel part as a Darcy-type porous media and liquified part also a porous medium but with a much higher permeability [[12]](#12). With a working simplified model, it is possible to simulate the drug transport of individuals with 3D scan of the liquefaction geometry of vitreous. 

<a name="Fig1"/>![Fig  1](https://user-images.githubusercontent.com/93456391/146285436-6cc679c2-9377-4f3b-9cbe-6b67c3fe757b.png)

Fig. 1 Age-related vitreous liquefaction and PVD.

##### Detection of liquefaction region
The problem becomes imaging and detection of the liquefaction region of vitreous. Among the imaging techniques for in vivo vitreous body, ultrasonography has its advantage in low cost, easy to access and with data big enough for analysis. The frequency of ultrasound used in ophthalmology are generally in the range of 8-10 MHz, which produced wavelengths as short as 0.2mm. However, since it’s still not short enough for even the posterior vitreous cortex, the utility of this technique results from the fact that strong echoes are produced at ‘acoustic’ interfaces found at the junctions of media with different densities and sound velocities. Thus, age-related or pathologic phase alterations within the vitreous body is detectable by ultrasonography[[6]](#6). Walton et al. published a method for quantifying the relative vitreous liquefaction by detecting the speckle density (hyperreflective areas on ultrasound) and tracking the speckles movements on a polar grid relative to the angle travelled by the eye [[13]](https://user-images.githubusercontent.com/93456391/146285542-910c4dcf-0c83-4c55-9ede-28dde6f919ad.png). Although this approach has not yet been independently validated [[14]](#14), it gives a good approach for the detection of liquefaction using ultrasound, and validation can be done with the help of magnetic resonance imaging for an accurate detection. The detection to this extends is enough for detection of the position and size of ‘liquified’ pockets but the limitation lies in the fact that it’s only a 2D image. The approaches to resolve this limitation will be discussed in the following part.
![Fig  2](https://user-images.githubusercontent.com/93456391/146285542-910c4dcf-0c83-4c55-9ede-28dde6f919ad.png)

Fig. 2 Speckles detected in the dark vitreous cavity with a polar grid used to record the coordinates of the speckles. [13]


## Method
Creating and a numerical model for each individual based on the ultrasound image is computational expensive. In this case, a machine-learning (ML) model is a good solution given the fact that it will give a quick prediction after training with a large data set. Deep-learning (DL) method is more applicable for the purpose compared with conventional ML methods with it’s advantage in processing complex and large datasets. For training purpose, the thousands of ultrasound image of patients are enough as the input. However, without an indicator to evaluate each injection process, the output remains a problem to solve.

##### Approach1: Creating 3D numerical model to analyze the drug concentration at the retina and use it as the output with meshless method and parallel domain decomposition.
After validating the reliability of kinetic B scan ultrasound recording for detecting the liquefied region, and axial-symmetric vitreous geometry can be obtained from the 2D image for each eye scanned. A numerical model can be created for each model. Considering the large number of datasets needed for the training, meshing generation for each model for the analysis based on finite element methods (FEM) or finite volume methods (FVM) would require significant effort. Meshless methods reduced the effort devoted to model preparation by doing calculation based on 
nodal or points that are not required to be uniform in their spatial distribution due to the fact that most rely on global radial-basis functions (RBF) [[18]](#18). A localized meshless RBF method developed by Divo et al. will fits the need for this project with a parallel domain decomposition implementation that can accelerate the solution process if needed [[19]](#19).

##### Approach2: Visual acuity improvement or other indirect indicators as input
Visual acuity and central retinal thickness (CRT) measured by optical coherence tomography are two indicators for the evaluation of intravitreal Bevacizumab, a recombinant monoclonal antibody that inhibits human vascular endothelial growth factor (VEGF) for treating VEGF-mediated diseases [[20]](#20). Clinical measurable indicators like visual acuity and CRT can help skip the part for getting ground truth with numerical model for the training

## References

<a name="1"/>[1] Remington, L. A., and D. Goodwin. Clinical Anatomy of the Visual System E-Book. Amsterdam: Elsevier Health Sciences, 2011.

<a name="2"/>[2]	Mains, J. & Wilson, C. G., 2013. The Vitreous Humor As a Barrier to Nanoparticle Distribution, DOI: 10.1089/jop.2012.0138. J. Ocular Pharm. Therapeutics, 29(2), pp. 143-150.

<a name="3"/>[3] Balazs, E. & Flood, M., 1978. Age-related changes in the physical and chemical structure of the human vitreous.. Osaka., Third International Congress of Eye Research

<a name="4"/>[4]	Sharif-Kashani, P., Hubschman, J., Sassoon, D. & Kavehpour, H., 2011. Rheology of the vitreous gel: Effects of macromolecule organization; DOI: 10.1016/j.jbiomech.2010.10.002. Journal of Biomechanics, Volume 44, p. 419–423.

<a name="5"/>[5]	Nickerson, C. S., Park, J., Kornfield, J. A. & Karageozian, H., 2008. Rheological properties of the vitreous and the role of hyaluronic acid. J. Biomech. , Volume 41 , p. 1840–1846.

<a name="6"/>[6]	Sebag, J. "Imaging vitreous." Eye 16.4 (2002): 429-439.

<a name="7"/>[7]	Foos, Roberty Y., and Noel C. Wheeler. "Vitreoretinal juncture: synchysis senilis and posterior vitreous detachment." Ophthalmology 89.12 (1982): 1502-1512.

<a name="8"/>[8]	Le Goff, M., Bishop, P. Adult vitreous structure and postnatal changes. Eye 22, 1214–1222 (2008). https://doi.org/10.1038/eye.2008.21

<a name="9"/>[9]	Penkova, Anita N., et al. "Measurement of the Hydraulic Conductivity of the Vitreous Humor." Journal of porous media 23.2 (2020).

<a name="10"/>[10]	Xu, J., Heys, J., Barocas, V. & Randolph, T., 2000. Permeability and diffusion in vitreous humor: implications for drug delivery.. Pharm. Res. , Volume 17, 
pp. 664-669.

<a name="11"/>[11]	Penkova, Anita, et al. "Diffusive Transport in the Vitreous Humor: Experimental and Analytical Studies." Journal of Heat Transfer 141.5 (2019).

<a name="12"/>[12]	Khoobyar, Anahid, et al. "Mathematical Model of Macromolecular Drug Transport in a Partially Liquefied Vitreous Humor." Journal of Heat Transfer (2021).

<a name="13"/>[13]	Walton, Kelly A., et al. "Age-related changes in vitreous mobility as measured by video B scan ultrasound." Experimental eye research 74.2 (2002): 173-180.

<a name="14"/>[14]	Beebe, David C., Nancy M. Holekamp, and Ying-Bo Shui. "Oxidative damage and the prevention of age-related cataracts." Ophthalmic research 44.3 (2010): 155-
165.

<a name="15"/>[15]	LeCun, Yann, Yoshua Bengio, and Geoffrey Hinton. "Deep learning." nature 521.7553 (2015): 436-444.

<a name="16"/>[16]	Schmidhuber, Jürgen. "Deep learning in neural networks: An overview." Neural networks 61 (2015): 85-117.

<a name="17"/>[17]	Belytschko, Ted, Yun Yun Lu, and Lei Gu. "Element‐free Galerkin methods." International journal for numerical methods in engineering 37.2 (1994): 229-256.

<a name="18"/>[18]	Buhmann, Martin D. Radial basis functions: theory and implementations. Vol. 12. Cambridge university press, 2003.

<a name="19"/>[19]	Divo, Eduardo, and Alain J. Kassab. "An efficient localized radial basis function meshless method for fluid flow and conjugate heat transfer." (2007): 124-
136.

<a name="20"/>[20]	Pai, Sivakami A., et al. "Clinical, anatomic, and electrophysiologic evaluation following intravitreal bevacizumab for macular edema in retinal vein occlusion." American journal of ophthalmology 143.4 (2007): 601-606.
