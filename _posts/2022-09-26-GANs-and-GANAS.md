# The Story of GANAS

If you have watched stand and deliver then you would know Jaime Escalante's words that all we need is Ganas, which is roughly translated to desire to do something, having zeal and passion to do something despite having the odds against us.

Now, the actual transation has been disputed but it sits very well with the movie. One of the best when it comes to education and student teacher relationships.

GAN and Ganas don't have anything in common except similar sounding words but it definitely makes me think about this course I took on deep learning and the instructor Jeremy Howard. No, I won't elevate him to status of Jaime Escalante but definitely he has done the work of bringing a topic to the world for which universities are charging an exorbitant amount of money and the subject is more or less commoditised in today's world.


I have discussed it with many friends of mine who are in deep learning and they would say that he has ulterior motives, he wants to be famous as someone who is locking horns with big corps in the field of deep learning, some say his API is half baked, a few have good words to say about him, one of them said that he has become a millionaire through affiliations and what not.


I don't know whether there is merit in them or not but I do apprecaite the fact that he has broguht this course that people can benefit greatly from. People talk about democracy but in real sense, provision of knowledge for  all is the real democratisation of the AI.

It bridged many gaps in my knowledge, the things that I had just taken for granted for I couldn't understand or come up with an explanation for their existence, I understood the reason behind them. I don't want to make a comparison with any other courses out there but this one was just right up my alley of top down approach than the bottom up which I detest for many reasons.


Overall, I found his course quite helpful and it doesn't really matter what others say, at least his' is open source.

# The story of GANs
I don't have to educate the masses on what GANs are, these small posts are for my perusual as they help in crystallise my understanding and also act as a quick reference for future use. If anyone else finds them useful, then that's an added cherry on the top.

Ok, about GANs.

If you have a low resolution photograph and you want to make it high resolution, then a simple neural network that uses the MSE/RMSE/MAE as the loss functions won't be able to perform well as the output image would be quite close as far as the pixels are concerned and thus the loss would not be really high. To mitigate this problem, we need to form a different question - Is this a good quality image of the object under consideration? e.g. Is this a good quality image of a cat?


Earlier, the question was how far off we are from the original image which is supposed to be good quality but because pixels don't really mismatch a lot, the loss is not very high despite having a low resolution image at hand.

These issues are solved by something called GAN - Generative Adversarial Network. A GAN is something that has two parts. A usual loss function that will check how far off you are from the real object and the other one is called a critic or a discriminator that will ascertain whether the geenrated/cleaned image is a good/high resolution image of the thing.

The loss function calls the critic/discriminator.

The discriminator will take all the generated/cleaned images and take the high resluton images and will try to classify them in binary bucket of high res vs generated/cleaned. The idea is to fool the discriminator to a degree that it will start classifying the generated/cleaned images as the high res images.

[![SCR-20221019-w9e.png](https://i.postimg.cc/qv4CbFcR/SCR-20221019-w9e.png)](https://postimg.cc/BX76tMV9)


It is more of a ping pong process. You train the predictor and then ask the discriminator how am I doing and then train the predictor more and then go back to discriminator and so on.

You train the generator for a while and then ask the discriminator how did you do and once you got the results then you train the generator again, after a while your generator will be quite good and will start fooling the discriminator. So, you stop training the generator and train the discriminator with the newly geenrated/cleaned image, now your discriminator is strong. You go back again and train the generator. This keeps going on till you are satisfied with the results.

They take a long time to train as generator and discriminator are dependent on each other. If neither is trained then it is the case of the blind leading the blind.
