# CodeLlama quantisation weirdness

When messing around with quantisation to see what kind of models I could fit on an RTX 3090 I came across 
some strange behaviour.  I was comparing three sizes of CodeLlama model, with different quantisations:

* codellama/CodeLlama-7b-Instruct-hf in full-fat, 8-bit and 4-bit
* codellama/CodeLlama-13b-Instruct-hf in 8-bit and 4-bit
* codellama/CodeLlama-34b-Instruct-hf in 4-bit

The quality of the response to my test question was not too bad with any of these, apart from 
codellama/CodeLlama-34b-Instruct-hf in 4-bit, which was often (but not always) heavily glitched with 
missing tokens -- that is,  it was *worse* than codellama/CodeLlama-7b-Instruct-hf in 4-bit.  That 
surprised me!  In the case captured in this notebook, it generates Java instead of the requested Python, 
and I've also seen it output glitched JavaScript.

I was expecting quantisation to worsen the results, but not to make a larger model worse than a smaller one 
*at the same level of quantisation*.  I've put this repo up to see if anyone can repro these results, and to 
find out if anyone has any idea why it's happening.