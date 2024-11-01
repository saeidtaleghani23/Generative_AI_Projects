# General description of CycleGAN Model
- <small> The model contains two generator models: </small>
     - <small> Generator A: Generates images for the first domain. </small>
    - <small> Generator B: Generates images for the second domain. </small>
- <small> Inputs to generators come from the other domain: </small>
     - <small> Domain1 ➡ Generator A ➡ Domain2 </small>
     - <small> Domain2 ➡ Generator B ➡ Domain1 </small>

- <small> Each generator has a corresponding discriminator model (Discriminator A and Discriminator B): </small>
     - <small> Domain2 ➡ Discriminator A ➡ real/fake </small>
     - <small> Domain1 ➡ Generator A  (Generates image in Domain 2) ➡ Discriminator A ➡ real/fake </small>
     - <small> Domain1 ➡ Discriminator B ➡ real/fake </small>
     - <small> Domain2 ➡ Generator B  (Generates image in Domain 1) ➡ Discriminator B ➡ real/fake </small>

- <small> Cycle consistency: Generator models are trained to reproduce the original source image. </small>
     - <small>Use generated image as input to the corresponding generator model and compare the output image to the original image. </small>
      <small> Domain1 ➡ Generator A  (Generates image in Domain 2) ➡ Generator B (Generates image in Domain 1) </small>
      <small> Domain2 ➡ Generator B  (Generates image in Domain 1) ➡ Generator A (Generates image in Domain 2) </small>

- <small> Generator is trained via the combined model to minimize 4 different losses</small>
    - <small> Adversarial loss (L2- MSE): Minimize the loss predicted by the discriminator for generated images marked as "real"</small>
    - <small> Identity loss (L1- MAE): Output the source image as-is without translation.</small>
    - <small> Cycle loss forward (L1- MAE): Regeneration of a source image when used with the other model.</small>
    - <small> Cycle loss backward (L1- MAE): Regeneration of a source image when used with the other model.</small>

    