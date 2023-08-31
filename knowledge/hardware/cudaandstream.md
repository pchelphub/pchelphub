---
layout: default
title: NVIDIA's CUDA Cores & AMD's Stream Processors
parent: Hardware
---
Written by @temptd

If you've been around the internet long enough and have read into Nvidia's graphics cards at least once or twice, you've probably heard the term "CUDA cores". CUDA means Compute Unified Device Architecture and these are responsible for, well, computing. Specifically, graphics. AMD's are called Stream Processors. CUDA cores and Stream Processors are what are known as  "parallel processors."

Parallel processing is the act of processing a *lot* of information simultaneously, such as tackling the geometry as well as lighting of a scene in a game at the same time, rendering it for you to see. Why a CPU is poor at this is because CPUs process one thing after another, but have fewer, stronger, cores.

The difference between these cores and CPU cores is they're real, real weak when you use them singularly. Nvidia and AMD use (nowadays) thousands of them to keep up with the demand of gaming (among other things, such as AI, etc).

While CUDA cores and Stream Processors are *pretty much* the same thing, the performance you get from them is different between different games and applications. This is where the marketing comes into it. CUDA cores are talked about like they're *very* special, whereas Stream Processors, nobody talks about.

CUDAs and Stream Processors behave, for the most part, exactly the same way. The problem is that with certain applications, namely software in the 3D rendering world, Nvidia's architecture has just simply been the one that was worked with more and longer. So "CUDA cores are better for productivity" is, for the moment, true. But, that's not saying Stream Processors are *useless* in the productivity world; they just haven't been developed for as long as Nvidia's, nor used as much in-industry as Nvidia's.

AMD GPUs are starting to gain some traction in the productivity world though as OpenGL/Vulkan gains wider adoption. This is huge as OpenGL and Vulkan are both open source, and as such, have a much, much wider pool of people to develop the APIs.

Developing OpenGL/Vulkan further allow for GPUs on all sides, whether that be Nvidia's, AMD's, or Intel's, to run on more programs that are not specifically built for one single manufacturer's Architecture. (Hint: Nvidia)

A good exmaple of this is the 7900xtx matching the 2080 ti in Blender 3.3.0 in GPU mode, the 3080 in UE4.26, and even *beating* the 4090 in some things in DaVinci Resolve.
(See PugetSystems for these comparisons for a more in-depth view and for what I did not include)

There's also the case of:

More cores *does not* mean more power.

For instance: the 7900xtx and the 3070 ti *both* have 6,144 cores. But the 7900xtx is leaps and bounds a better GPU than the 3070 ti. The 3090 has twice as many cores as the 6900xt but their performance in gaming is pretty close together.

So what does this mean for the average consumer?

Take the amount of cores AMD and Nvidia state their GPUs have with a grain of salt, and don't assume that more = better across the board. As the architectures for each are developed, the cores themselves get more efficient. As does the interface that makes using them possible, as does the software that utilizes them, etc.

I will not be diving into Tensor cores, as these are also cores of the GPU, but used for *vastly* different things. They are more for matrix multiplication-accumulate operations, whereas CUDA is GPU accelerated code in general.

As always, feel free to dive in yourself on Google or Google Scholar and do some reading yourself as in the process of simplifying information, there is plenty of information left out that complicates it more than a simple writeup can handle.
