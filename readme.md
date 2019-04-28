 # Resurrecting Shakespeare with LTSM recurrent neural networks
 Graeme West - 2019-04-28
 
 ![Shakespeare Meme](https://i.pinimg.com/236x/f6/11/27/f611272ef416195a7726a037d4394de4.jpg "Shakespere Meme")
 
This notebook contains an version of the 'Generating Text in the Style of an Example' chapter from Douwe Osinga's [Deep Learning Cookbook](http://shop.oreilly.com/product/0636920097471.do) (O'Reilly, 2018).

*[View the notebook HERE](shakespeare_dnn_ltsm.ipynb)*
 
The notebook imports the Complete Works of Shakespeare from Project Gutenberg, builds a recurrent neural network model with LTSM layers. The resulting text is somewhat convincing to a casual observer, as long as they aren't a paying too much attention:


> Thou smother'st honesty, thou murther'st troth;
>
> Thou foul abettor! thou notorious bawd!
>
> Thou plantest scandal and displacest laud:
>
> Thou ravisher, thou t#he more subject of thy love,
>
> And therefore thou art a soldier to the state,
>
> And therefore we have seen the strange seasons,
>
> And therefore we have seen the streets of the world,
>
> And therefore we have seen the state of men,
>
> And therefore we have seen the state of men,
>
> And therefore we have seen the state of men,
>
> And therefore we have seen the state of men,
>
> And therefore we have seen 

As you can see, the results can sometimes contain amusingly Elizabethan profanities! Because it's a character-level network, and it's trained on Shakespeare's plays, there are definitely oddities creeping in. Notably, characters used for dramatic prompts (such as the hashmark, used to precede the names of characters in the play, and stage directions), are replicated in the middle of prose.

Also, the output gets more repetitive the longer it freestyles from the 'seed' text (the starting point in the real corpus).

The training process took around 20 hours to run 12 epochs through the training data on my MacBook Pro 2016 Core i7. Just for fun, I also tried out the [TensorFlow Cloud TPU demo for a very similar Shakespeare-generating RNN](https://colab.research.google.com/drive/1DWdpYrgDB9cAMj4o2lTjROGLiXxzUFFf). Training on the TPUs took something like four minutes! I guess this shows the power of massively-parallel vector processing.