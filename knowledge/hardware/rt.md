---
layout: default
title: Raytracing Performance Differences Between NVIDIA and AMD Cards
parent: Hardware
---
Written by @temptd

The basic idea of ray-tracing is that it's supposed to accurately display light by following rays of light and calculating what they hit, *and don't*, and how that would bounce light in the real world. In theory this sounds amazing but in practice the performance has been subpar at best, and literally impossible at worst.

Sure, there's the RTX craze that Nvidia has been pushing, but what exactly does this mean? Because "RTX" was originally *GTX* but then they just.. focused on RT. And changed the name to.. RTX. Nice!

But for some reason, this has left people that don't know any better the impression that AMD isn't even capable of ray-tracing, which is extremely untrue.

RDNA 2 + 3 and Turing/Pascal/Ampere has been a confusing thing for a lot of people and without reading more into it, you may not exactly understand why RT performance/development has gone the way it has. For starters, it's not as simple as "Nvidia does it better." Sure, that may be true *sometimes*, but it's not outright the case. AMD is absolutely capable of raytracing and it's not half bad at it at that.

The difference between RT and normal lighting performance is both simple and compelx to explain. RT calculates light values by taking each pixel's distance to lights sources into account and trying to calculate what the correct level of shading is based on that. Now multiply, and then multiply again, and again, etc etc, and you get the point. It is *a ton* of calculations at once. Each singular pixel takes multiple rays being sent off to even calculate what *that pixel's* lighting should be. Multiple that by the amount of pixel on screen, the values each individual pixel *should* be, say for instance the light value of a raytraced piece of metal laying on the floor versus a table cloth, in the same scene, and it paints a picture of *an absolute ton* of pixels that need to be calculated. It then tests for each intersection on every piece of geometry in the scene, to top it all off.

This is where BVH comes in, or bounding volume hierarchy. 

Think of the BVH as somewhat like a building. Each BVH has a bunch of nodes that correct to smaller nodes. When you're using RT, your GPU collects all the data and computes what it needs to do at the very tip-top of the building, the beginning node, and then bounces to each individual smaller node to see if the singular *ray* intersects with that node. Then, think of there being thousands, if not millions, of smaller nodes per node in the scene. Every smaller node represents a tiny area that makes up the bigger area. After alllll these nodes are checked to see if it's hitting something, it then checks the *very bottom* node to see if a ray is *actually* hitting it. This bottom node contains the primitive geometry, triangles. 

The difference in Nvidia's architecture and AMD's architecture is how they actually build their BVHs. AMD builds it more like the empire state building, or Eifle Tower, whereas Nvidia builds it like a big rectangle that's not very tall. Think: pyramid vs rectangle.

AMD likes to do things by adding lots of intersection tests to see if the rays are actuall hitting something, over and over. This is then handed back to the shader computation and if it intersects, it changes. If not, it doesn't. RDNA 3 made this faster by implementing special LDS (local data share) instructions that overall sped up the process of bouncing the data back and forth to calculate the rays that intersected with the geometry/texture.

Using DirectX Raytracing, the API developed by Microsoft that tons of games use, BHVs are defined by two structures: top level acceleration structures, and bottom level acceleration structures, or TLAS/BLAS for short. How it's calculated is going through the TLAS, then the BLAS, then the geometry of the object in the scene.

This is where you can get pretty math heavy if you feel so inclined, but overall once you started getting to the BLAS is when cache and memory latency will be important

It takes multiple jumps to get from TLAS to BLAS, and then BLAS to the geometry. 

If you don't know much about memory and pointers, this is where I'd recommend you going and reading about it because it is very important on the design and architecture of computer systems and software. It affects everything from browsing your desktop to gaming and programming.

To continue:

AMD uses a ton of subdividing. It results in less demanding intersection tests, but a lot more intersection tests overtime. But this is also a downside as this is where memory and cache have an impact. Each new subdivision has to wait for the previous subdivision to be finished before it can start. The way RDNA handles it, is it has to keep a lot more going at once to ensure that there's a "seamless" experience, and to hide overall latency. Unfortunately, it may not always result in that because the architecture of RDNA is built in a stacked manner. Note: RDNA *3* does a better job of this, and has higher accuracy over RNDA *2*, but not so much that it's a fix to the problem.

Next, there's also more than one way to actually calculate raytracing.

There is Inline and indirect.

Inline basically means that the shader program itself handles both the traversal of data, and also the calculation of appropriate lighting, and whether it's a hit or a miss.

Indirect raytracing means there are separate shader programs going at once and they calculate accuracy of the rays being detected as a hit or a miss on the geometry/texture *at the same time.*

Different game engines use different methods to calculate raytracing and that's why some developers consistently have better RT performance than others.

How Nvidia likes to handle their BVH is by making it like a wide, wide building with fewer floors and less height than the Empire State building or the Eifle Tower. The second it hits that first node, it shows a *ton* of nodes to calculate next, as opposed to jumping between a bunch like AMD's. Then each of those nodes point directly to the BLAS mentioned before, skipping over tons of calculations to move data before it can continue. Where AMD can only point to a certain amount of nodes at once, Nvidia doesn't seem to have a limit to the amount that can be calculated at a single given time. Seems like there's too much going on at once, yeah?

Wrong. GPUs are designed to take into account things like "wow, lots of intersection tests. Time to knock them out."

That's kind of their *thing*.

Nvidia also has the benefit of having a much larger cache at the very beginning. Remember LDS? Nvidia's version is called Shared Memory, and it's blocked out out of SRAM. Neither AMD's LDS or Nvidia's Shared Memory are bad by any means, but Nvidia's Shared Memory is currently designed better. 

A direct comparison with more sexy GPU science:

AMD cards with RDNA 2 lacked dedicated BVH traversal hardware, instead having the BVH traversal handled by other parts of the GPU that are already doing other calculations, effectively making it to where RDNA 2 GPUs had to RT right alongside all the other stuff a GPU normally does, leading to much slower traversals. RDNA2 also had "Ray Accelerators" that could only do ~4 ray->node intersection tests per clock, and only 1 intersection test per triangle of geometry.

Nvidia's Ampere can do two ray->triangle intersection tests per clock, while Ada Lovelace can do ~4 ray->triangle intersection tests per clock. Each of these are *per dedicated RT core.* When you look at the Ampere 3090ti, it has 84 RT cores. So multiple 84 by 2 and that means the top of the line Ampere card could run 168 ray->triangle intersection tests per clock, with 1560mhz base clock speed, that's 262,080 ray->triangle intersection tests per *second*. Ada Lovelace's  is capable of 4 ray->triangle tests per RT core, and at 128 RT cores, and a much higher base clock speed, it ends up coming out to 1,144,320 intersection tests *per second*. 

Using the same "top of the line" vs "top of the line" for RDNA 2 and RDNA 3:

The 6950xt is capable of 1 intersection test per triangle of geometry, and has 80 cores. Using the same calculations at the 6950 xt's base clock of 1860mhz, it comes out to 148,800 clocks per second. The 7900 xtx has 96 RT cores and, *theoretically* is capable of 178,080 intersection tests per second.

Unfortunately, with RDNA 3, we do not have the exact amount of intersection tests possible on RDNA 3 GPU per second. What we do know is that RDNA 3 actually *has* dedicated BVH traversal hardware on the GPUs now so the development of their RT process is going to happen faster now that they got that situated. No longer does RT have to be processed and calculated right alongside everything else, they have their own thing now.

The problem with making an absolute direct comparison with the numbers above:

Remember that these architectures are designed to handle RT completely differently. One handles it like a tall slender building, and one handles it like a wide, flatter building. Nvidia is currently able to start the process of calculating where their rays are going and what they're hitting on a wider sample first, albeit stretched across a lot more nodes at once. Whereas AMD, starts the process at the tip-top and calculates it's way down. How this is handled in the next few years, we will have to see, but the performance differences between RDNA 2 and 3 are impressive.

But Nvidia is pushing RT really hard so I have my doubts that AMD will ever end up "beating" them, at least not anytime soon.

Also, keep in mind that the calculations above are made using GPU's base clocks, nothing more, and in perfect condition. Normal wear and tear, as well as actual clock in-activity, will change the amounts around. This is merely a *theoretical* calculation based on what is known and what is readily available.
