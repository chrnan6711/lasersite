# Create projections with more than 400 lasers

Tower Unite laser projectors are limited to displaying 400 lasers at one time; fortunately, there are a few different workarounds for this. This page explains how to create and display expressions that use more than 400 lasers.

### Step 1: Coding

Write your expression as if the laser projector *could* actually display more than 400 lasers. That's right, it's pretend time! Of course, your projection won't look right at first; don't worry about this, as it will soon.

### Step 2: Prepare your expression

Now that the expression has been written, a few things must be done to it in order to prepare it for proper projection.

First, replace all instances of the word `index` in your code with `sindex`.

Next, declare a new variable `shift = 0` at the beginning of the code.

Last, declare another new variable `sindex = index+shift*400`.

### Step 3: Usage

There are a couple ways to go about using this new modified expression, each with their positives and negatives. Method 1 creates a perfect image, but uses more than one projector. Methods 2 and 3 use just one projector, but do not produce a perfect image. In all different methods, the number `x` refers to the lowest whole number such that 400x is greater than the amount of lasers you coded your expression to use. For example, if you coded your expression to use 1000 lasers, `x` should be 3.

#### Method 1: Projector Layering (multiple projectors)

Procure `x` projectors. Paste and run the expression on each, but change the shift value in each projector to a different number ranging from 0 and `x-1`. Turn them all on and use Q+click to place them in the exact same location. While this method creates a perfect image, it is somewhat high maintenance and also laggier.

#### Method 2: Discrete shifting (single projector)

Set the value of `shift` to `floor(25time%x)`.

This method works by quickly switching all lasers between different shift values. While it mostly preserves the look of continuous lines of lasers, it begins to look bad when `x` is over 2.

#### Method 3: Random shifting (single projector)

Set the value of `shift` to `floor(x*rand())`.

This method works by making each laser choose a random shift value every frame. While it does not preserve the look of continuous lines of lasers, it does work well up to an `x` of around 4.
