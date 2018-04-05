Stochastic Program Optimization
====

## General Information

Link: https://static.googleusercontent.com/media/research.google.com/en//archive/large_deep_networks_nips2012.pdf

Presented By: Ajay Jain and Justin Chen

Date: 2/14/18

## Notes

## Discussion

**How useful is this?**

Initial thoughts make it seem limited. Essentially it only works on basic blocks, so no control flow can be tolerated and requires fairly solid test cases to be sure of execution.

However, after discussion some interesting points came up. The paper is focused on assembly, particularly x86 assembly. There are 100s of instructions so running it on small code segments can allow for the benefits of the superoptimization.

**Is the exhaustive testing really a limitation?**

Theres a lot of work on automated testing and symbolic/concolic execution that could provide many advantages when coupled with this system. They wouldn't be able to directly feed into one another, but basically you could superoptimize against a weak set of tests. Then use the new code to come up with a stronger set of tests and continue on.

See papers on test: (1) Why Automated Testing Works In Practice - https://people.mpi-sws.org/~fniksic/popl2018/paper.pdf (2) Directed Automated Testing - http://css.csail.mit.edu/6.858/2018/readings/dart.pdf

**It's mentioned that a random start point in the code is better than starting with the gcc compiled version. Why?**

The answer lies in the Metropolis-Hastings Monte Carlo search used. We can think of the gcc compiled version as a sort of local optima. So to get to a better optima, the algorithm has to make a serious of highly unprobable steps as it may need to mess more up to find the more optimal solution. Unlike SGD, in MHMC this means the global optima will be reached in limit, for efficiency purposes it is better to start with random code. Interesting...

**Well if you can start with random code isn't this code synthesis?**

This is where it got a bit confusing. But the idea is an interesting one. Code synthesis is the idea that by simply constructing a suite of test cases, an algorithm can effectively reverse engineer a program that satisfies those test cases. I'm not sure this is the same thing and by random they probably meant unoptimized. But still an interesting thought.
