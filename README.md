<img src="./docs/assets/images/theoretical_framework.svg" alt="ch1"> 
## Vector Boson Scattering (VBS)
VBS takes place when quarks from different protons radiate vector bosons, which in turn interact:
- It is an ideal place for searches for new physics because it is **sensitive to modifications of the EWK sector**.
- We used MC generations @LO, @parton-level of **Same Sign WW scattering(SSWW)** with fully leptonic final state:

<img src="./docs/assets/images/ssww.png" alt="ssww">
<img src="./docs/assets/images/feynman.svg" alt="feynman">

## SM Effective Field Theories (SMEFT)
The SM is seen as a **low energy approximation of an unknown theory** and BSM effects are parametrized as additional terms to the SM lagrangian through operators of order larger than four:

<img src="./docs/assets/images/LEFT.svg" alt="LEFT">

This stuy is focused on 15 dim 6 operators chosen from the Warsaw Basis, which modify the distributions of the variables as follows:
<img src="./docs/assets/images/EFTcontrib.png" alt="EFTcontrib">


<img src="./docs/assets/images/chapter_vaes.svg" alt="ch2">
## Variational AutoEncoders (VAEs)
**VAEs are trained to reconstruct an input**: the input is mapped as a distribution in the latent space, from which a point is sampled an decoded.  
The model is trained minimizing two loss functions:
- **Kullback-Leibler divergence** (KLD) - regularization of the latent space
- **Mean Squared Error** (MSE) - reconstruction of the input

<img src="./docs/assets/images/vae_mechanism.png" alt="vae_mechanism">

### Anomaly detection:
The VAE model is **trained to reconstruct a sample that comprises SM events**. When it is fed anomalous data (EFT events), those are badly reconstructed and can be singled out:
<img src="./docs/assets/images/inout.png" alt="inout">

Therefore,**anomalies are expected to lie in the tail fo the loss function**
<img src="./docs/assets/images/lossAD.png" alt="lossAD">

<img src="./docs/assets/images/chapter_boh.svg" alt="ch3">
## Optimizing for discrimination: VAE + DNN


