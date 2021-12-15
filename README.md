# CS596 Final Project: Machine Learning based study of drug diffusion in intravitreal drug delivery
This is a project for CS596
## Abstraction
The liquefaction of vitreous humor has a significant effect on the diffusion of drug in the process of intravitreal drug delivery. Considering that the liquification geometry varies from person to person, it would be helpful if we can predict the drug diffusion process and further more give suggestion on the injection point and frequency for each individual. This requires a model for each individual, and a well trained deep learning model will significantly improve the efficiency comparing with doing meshing and numerical analysis for each specific case. So, in this model, the input will be the 2D liquefaction geometry of the vitreous detected by untrasound images of vitreous and the injection point, output will be the time interval that the drug is in effect, or in other words, the time interval that the concentration at the retina is within the expected range. For output, since there isn't a good indicator in clinical practice, we are planning to calculate the output based on numerical models for the limited number of cases and get the result based on the numerical simulation.

## For Presentation
Intravitreal drug injection

<img src="https://user-images.githubusercontent.com/93456391/144202513-03998c5f-e115-40a9-9b3b-bec6d0440eb7.png" width="200">
Liquification with aging

![41433_2008_Article_BFeye200821_Fig4_HTML](https://user-images.githubusercontent.com/93456391/143964305-a6d86037-ac46-4bcd-9f37-cae1860e3c84.jpg)

We have studied and got most of the important parameters for vitreous and drugs including hydraulic conductivity, diffusion coefficient and so on. This means we are able to create numerical models for simulating the diffusion of drug after injection. __Time consuming__

![V9`YV46GV)P24@U{)I}UDO](https://user-images.githubusercontent.com/93456391/144206647-50874187-a408-4434-bb41-a55339fe7873.png)

Ultrasound imaging for vitreous

![PIC1](https://user-images.githubusercontent.com/93456391/144332264-8fd5629c-bdbc-4123-b0d0-ec76a249bb57.jpg)

In clinical practice, although MRI can give 3D image of the eye structure, it's high cost make it impossible for daily treatment. Ultrasound has it's strength in eazy to access and showing the liquifaction structure inside the eye. Besides, there isn't a good indicator in clinical practice that tells how long the drug is in effect.

So the approach that we are planning to take is:
1. Use ultrasound images to reconstruct 3D numerical model
2. Calculate the time period that the drug is within the effective range based on the numerical model
3. Use the ultrasound images as input and time period as output to train the machine learning model
4. Other factors including: age, diabetes, PVD (Posterior Vitreous Detachment)
