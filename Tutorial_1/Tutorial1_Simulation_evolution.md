# Simulating evolution
# MBLS-207 - Bioinformatics
## 1 Setup
In this tutorial, you will simulate a simple model of evolution to introduce you with concepts from bioinformatics using a (Jupyter) notebook. This model will describe mutating DNA sequences, but we simplify what mutations occur and how they occur. But first, we need to set up the stage. Imagine a DNA sequence that has evolved over time, accumulating mutations, and thus diverging into two different sequences. Let’s think about how to compare these sequences now.
### Exercise 1
Open a new notebook. Define a function that takes two sequences as input and compares how identical they are. On what percentage of indices do they have matching entries? Assume that your inputs are of equal length.
### Exercise 2
One of the simplifications we will use is that we will always use sequences of the same length. Why is this a simplification?
### Exercise 3
Next, define another function that will mutate a given DNA sequence. The input is a DNA sequence, and the function randomly selects one of the bases, and mutates it. The DNA sequence with the mutation is returned. Python’s random package comes in handy for this function.

## 2 Simulating the evolution of a single sequence
We now have the basis of our model: the ability to mutate sequences. Next, we are going to simulate evolution by taking a sequence and letting it mutate in a number of time steps. Then, we are going to compare how identical the mutating sequence is with the original sequence.
### Exercise 4
In a new cell, generate a (random) DNA sequence of 50 nucleotides. Then, write a loop that will:
1. Mutate the sequence
2. Compare the mutated sequence with the original sequence
3. Store the identity scores in a list, for 600 time/mutation steps
### Exercise 5
Now we have a list with similarity scores over a series of time/mutation steps. Make a plot of these data to show similarity scores as a function of time/mutation steps.
### Exercise 6
What do you notice on the similarity score over time? Can you explain this?
### Exercise 7
What will this plot look like if instead of comparing the original sequence with mutated versions of itself, we compare the original sequence with a mutating sequence that initially has no base in common with the original sequence, like the complementary sequence?
### Exercise 8
What is the effect of the sequence length? Compare the identity scores over time of a short and long sequence.

## 3 DNA versus protein sequences
DNA sequences are not the only sequences of interest in bioinformatics, also protein sequences are frequently studied.
### Exercise 9
Define (or look up) a function that translates a DNA sequence into a protein sequence
### Exercise 10
In the cell from the previous section, also create a list that stores the identity scores comparing the translated mutated sequences with the translated sequence of the original.
### Exercise 11
Now, in the same plot as before, also plot the identity scores of the protein sequence over time. How do the identity scores of the protein sequence change over time in comparison with the score of the DNA sequence? Does that make sense to you?

## 4 Reflecting exercise
Some additional exercises to let you think about some of your or other’s programming choices and how/if they affect the model.
### Exercise 12
In your mutating function, once you’ve selected a base, did you choose to only allow true mutations, or did you also allow a “mutation” to the original base? I.e., if you had selected an A to be mutated, did you only allow it to turn into a C, G or T, or was A also an option? What difference do these two options make on how time is perceived?
### Exercise 13
We have now compared the mutating sequence with a set original sequence. What does this original sequence represent biologically? How would the plots have looked like if looked at two identical copies that each mutate independently as can happen in speciation?
### Exercise 14
Besides the simplification of equal length sequences, what other assumptions or simplifications are in this model?
