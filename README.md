# Reconstruction Attack on Cifar-10 Dataset

## Motivation
I did a course called Dependable and Secure AI-ML, here I learned about this unique possibility of extracting class information using an ML model. This attack can extract representatives if done to a face verification model.
I wanted to try how such an attack can ruin the anonymity of public datasets(Ex: Cifar-10).

## Standard Reconstruction attack
First I trained a standard ResNet model with decent performance. The attack was carried(freeze all layers and make only input trainable) out by standard reconstruction Loss[1-p(c)+threshold_factor] for a class c. 
Even though loss became near zero the trained input image was a noisy one. This could be because our naked eye can't make out any pattern of a 32by32 pixel image. But the model was actually overfitting. Next, I trained
with L2 Regularization, even though model slightly improved with overfitting the produced image was noisy, with much more difficult loss convergence.

## Trying to regenerate from obfuscated image
Obfuscation is when some gaussian noise is added to input image. Then using this reconstruction attack procedure, we try to regenerate input image using class information. Although it seemed highly successful for lower
percent of obfuscation it was very less feasible for higher percentages(which is more common). And for robust models this technique is less feasible.

## Conclusion
In conclusion, a reconstruction attack can successfully take place on lightly and moderately obfuscated images, but on heavily obfuscated ones the standard algorithm is not strong enough to reconstruct the original image, instead we end up with a noisy image that is biased towards that particular class.
This could be because the trained model is weak and overfits the data, so there is no constricted input space for each class. It could also be because of the small number of output classes.
