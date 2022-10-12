
<img src="./docs/assets/images/ch1.png" alt="ch1"> 
VBS takes place when quarks from different protons radiate vector bosons, which in turn interact:
- It is an ideal place for searches for new physics because it is **sensitive to modifications of the EWK sector**.
- We used MC generations @LO, @parton-level of **Same Sign WW scattering(SSWW)** with fully leptonic final state:

<img src="./docs/assets/images/ssww.png" alt="ssww">
<img src="./docs/assets/images/feynman.png" alt="feynman">
    
<img src="./docs/assets/images/ch2.png" alt="ch2"> 
The SM is seen as a **low energy approximation of an unknown theory** and BSM effects are parametrized as additional terms to the SM lagrangian through operators of order larger than four:

<img src="./docs/assets/images/LEFT.png" alt="LEFT">

This stuy is focused on 15 dim 6 operators chosen from the Warsaw Basis, which modify the decay amplitudes (and therefore the distributions of the variables) as follows:
<img src="./docs/assets/images/EFTcontrib.png" alt="EFTcontrib">

    
<img src="./docs/assets/images/ch3.png" alt="ch3"> 
**VAEs are trained to reconstruct an input**: the input is mapped as a distribution in the latent space, from which a point is sampled an decoded.  
The model is trained minimizing two loss functions:
- **Kullback-Leibler divergence** (KLD) - regularization of the latent space
- **Mean Squared Error** (MSE) - reconstruction of the input

<img src="./docs/assets/images/vae_mechanism.png" alt="vae_mechanism">

## Anomaly detection:
The VAE model is **trained to reconstruct a sample that comprises SM events**. When it is fed anomalous data (EFT events), those are badly reconstructed and can be singled out:
<img src="./docs/assets/images/inout.png" alt="inout">

Therefore, **anomalies are expected to lie in the tail of the loss function**:
<img src="./docs/assets/images/lossAD.png" alt="lossAD">
    
<img src="./docs/assets/images/ch4.png" alt="ch4"> 
## Simple VAE
- built via subclassing on TensorFlow and Keras libraries
- deeply connected NN layers
- optimizer: Adam
- Epochs: up to 200 (convergence $\simeq$ 100)
- Batch size: 32/64
- Different dimensions of the latent space  
<img src="./docs/assets/images/simple_vae.png" alt="simple_vae">


## VAE + DNN binary classifier
Even though the ultimate aim is isolating EFT contributions, **the VAE model is solely trained to recontruct a SM sample**. However, the choices that improve SM reconstruction are not always optimal for discrimination (e.g. dimension of the latent space).  
Therefore, we built a model that optimizes both reconstruction and discrimination during training:
<img src="./docs/assets/images/full_model.png" alt="full_model">  
- the **VAE** part is trained to reconstruct **a pure SM sample**
- the classifier is trained to discriminate between **SM and EFT contributions from a single operator**, based on the VAE output
- Losses: MSE, KLD, **binary cross entropy** (for classification)
  
The optputs we obtained are the following:
<img src="./docs/assets/images/out_result.png" alt="out_result"> 
    
<img src="./docs/assets/images/ch5.png" alt="ch5">
To assess whether a model is able to discriminate between SM and BSM events we defind the significance as:
<img src="./docs/assets/images/sigma.png" alt="sigma">
  
Here we show the results for sigmamax $\sigma_{max}(c_{W}) = \max_{k}{\{\sigma(k,c_{W})\}}$ against $c_{W}$:
<img src="./docs/assets/images/sigmamax.png" alt="sigmamax"> 
  
We call a model sensitive to an operator if $\sigma_{max} \geq 3$. The values of $c_{op}$ such that $\sigma_{max}(c_{op}) = 3 $ for different operators:
<img src="./docs/assets/images/cop.png" alt="cop"> 

