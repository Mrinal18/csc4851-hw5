1.

L0 reconstruction favors precise/binary properties, as the results it gives are exact, with ones for present elements and zeroes for nonpresent elements.

L1 reconstruction norm is a sum of the absolute differences between predicted and target values in each dimension, and tends to be sparse (meaning mostly zeroes or near-zeroes) with a few high, notable values. This is useful if you need distinct feature selection.

L2 reconstruction norm is a sum of the direct distances between predicted and target values, as a straight line through all dimensions. It is less precise but favors speed of calculation.

2. I would use L0 reconstruction norm ||x||\_0 = (sigma\_i(x\_i^0))^(1/0) or similar here because we are looking for precise outputs, and L0 effectively returns 1 for matches and 0 for non-matches. We can be that precise because we have those hard pixel edges and could use filters appropriately sized to analyze by these sections.

3. I would use L1 reconstruction norm ||x|| = sigma\_i(|x\_i|) or similar because it promotes feature selection, allowing for strong decisions. You could use L2 if you wanted the model to output more varying confidence guesses for each image.

4.
    a.<br>
    b. I would set P to one side of the equation, then set it to zero. Then we would need to find the values of θ which would bring Q closest to zero. I think in this case the equation shouldn't be multiplicative or the parameters will end up all zero.

5. [InfoGAN](https://arxiv.org/pdf/1606.03657.pdf)

Information Maximizing Generative Adversarial Networks (InfoGAN) is made to use GAN for unsupervised learning, which is very useful as it would widely expand the amount of data that we can make use of - otherwise we are limited to data that has been labeled. Normally, GAN has a generator network attempt to find and mimic the real data distributions while its 'adversary,' a discriminator network, attempts to discern the real data from the generated.

In order to do this, they create a single formulation for latent code distribution (noise generator) and attempt to maximize the mutual information shared between these latent codes and the generated images. They experiment with the digit shape MNIST dataset, finding that the latent categorical code on its own can be used to classify the digits without labels with high accuracy.

InfoGAN can also differentiate between features of an image, such as different aspects of a chair, and finding the numbers through distracting noise in the SVHN dataset. It can even generate 3D rotations of faces despite never seeing multiple angles of the same face, preserving features such as elevation and lighting.

InfoGAN is a very promising, impressive, and useful algorithm, allowing for a lot of very impressive unsupervised learning - sure to be useful for many categorizational and generative networks in the future.