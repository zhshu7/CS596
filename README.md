# CS596 Final Project
This is a project for CS596
## Abstraction
The liquefaction of vitreous humor has a significant effect on the diffusion of drug in the process of intravitreal drug delivery. Considering that the liquification geometry varies from person to person, it would be helpful if we can predict the drug diffusion process and further more give suggestion on the injection point and frequency for each individual. This requires creating a simulation model for each individual based on the 3D imaging of the liquefaction structure of patients and doing numerical simulations based on the model. A well trained machine learning model will significantly improve the efficiency comparing with doing meshing and numerical analysis for each specific case. So, in this machine learning model, the input will be the liquefaction geometry of the vitreous and the injection point, output will be the time interval that the drug is in effect, or in other words, the time interval that the concentration at the retina is within the expected range. To train the model, we are planning to make use of the 2D untrasound images of eye structure with liquefaction parts identifiable (practical cases or random generated cases) as input. For output, since there isn't a good indicator in clinical practice, we are planning to calculate the output based on numerical models for the limited number of cases and get the result based on the numerical simulation.

## For Presentation
Intravitreal drug injection

<img src="https://user-images.githubusercontent.com/93456391/144202513-03998c5f-e115-40a9-9b3b-bec6d0440eb7.png" width="200">
Liquification with aging

![41433_2008_Article_BFeye200821_Fig4_HTML](https://user-images.githubusercontent.com/93456391/143964305-a6d86037-ac46-4bcd-9f37-cae1860e3c84.jpg)

We have studied and got most of the important parameters for vitreous and drugs including hydraulic conductivity, diffusion coefficient and so on. This means we are able to create numerical models for simulating the diffusion of drug after injection. __Time consuming__

![V9`YV46GV)P24@U{)I}UDO](https://user-images.githubusercontent.com/93456391/144206647-50874187-a408-4434-bb41-a55339fe7873.png)

In clinical practice, although MRI can give 3D image of the eye structure, it's high cost make it impossible for daily treatment. Ultrasound has it's strength in eazy to access and showing the liquifaction structure inside the eye. Besides, there isn't a good indicator in clinical practice that tells how long the drug is in effect.

So the approach that we are planning to take is:
1. Use ultrasound images to reconstruct 3D numerical model
2. Calculate the time period that the drug is within the effective range based on the numerical model
3. Use the ultrasound images as input and time period as output to train the machine learning model
