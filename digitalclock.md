# Digital Clock and Seven-Segment Display

This expression projects a skeuomorphic seven-segment display digital clock. In fact, its digits can be customized to whatever single-digit numbers the user may desire with `diga`, `digb`, `digc`, and `digd` (left to right). Currently, it displays your local time.

<details>
<summary>View code</summary>

```
brightness = 0.7;

timen = time + 0;

h = lerp(fraction,120,240);

s = 1;

diga = if(((time%43200) < 3600)|(time%43200 > 35999), 1, 0);
digb = floor(((((time + 39600)%43200)/3600)+1)%10);
digc = floor((time%3600)/600);
digd = floor((time%600)/60);

###########################################################

mindex = index % 63;

xf = if(index == 252 | index == 253, -5, if(mindex < 27, (mindex % 9) - 4, if(mindex < 45, -6, if(mindex < 63, 6, 100))) - if(index < 63, 26, if(index < 126, 10, if(index < 189, -10, if(index < 252, -26, 100))))-5;

yf = if(index == 252, 6, if(index == 253, -6, if(mindex < 27, 12*floor(((mindex/27) * 3) - 1), if(mindex < 36, 2 + mindex - 27, if(mindex < 45, -(2 + mindex - 36), if(mindex < 54, 2 + mindex - 45, if(mindex < 63, -(2 + mindex - 54), 100))))))));

x' = xf

y' = yf

v = brightness*(if(index == 252 | index == 253, ceil(sin(tau*timen)), if(index < 63,

if(diga == 0 | diga == 10 & mindex < 63, 0, 

if(diga == 1 & mindex < 45, 0, 

if(diga == 2 & ((mindex - 9) % 27) > 17 & mindex < 63, 0,

if(diga == 3 & mindex > 26 & mindex < 45, 0,

if(diga == 4 & mindex % 18 < if(mindex < 50, 9, -1), 0,

if(diga == 5 & 35 < mindex & mindex < 54, 0,

if(diga == 6 & 44 < mindex & mindex < 54, 0,

if(diga == 7 & (mindex % 27) < if(mindex < 50, 18, -1), 0,

if(diga == 8 & mindex < 0, 0,

if(diga == 9 & 35 < mindex & mindex < 45, 0, 1

)))))))))),

if(index < 126,

if(digb == 0 | digb == 10 & mindex > 8 & mindex < 18, 0, 

if(digb == 1 & mindex < 45, 0, 

if(digb == 2 & ((mindex - 9) % 27) > 17 & mindex < 63, 0,

if(digb == 3 & mindex > 26 & mindex < 45, 0,

if(digb == 4 & mindex % 18 < if(mindex < 50, 9, -1), 0,

if(digb == 5 & 35 < mindex & mindex < 54, 0,

if(digb == 6 & 44 < mindex & mindex < 54, 0,

if(digb == 7 & (mindex % 27) < if(mindex < 50, 18, -1), 0,

if(digb == 8 & mindex < 0, 0,

if(digb == 9 & 35 < mindex & mindex < 45, 0, 1

)))))))))),

if(index < 189,

if(digc == 0 | digc == 10 & mindex > 8 & mindex < 18, 0, 

if(digc == 1 & mindex < 45, 0, 

if(digc == 2 & ((mindex - 9) % 27) > 17 & mindex < 63, 0,

if(digc == 3 & mindex > 26 & mindex < 45, 0,

if(digc == 4 & mindex % 18 < if(mindex < 50, 9, -1), 0,

if(digc == 5 & 35 < mindex & mindex < 54, 0,

if(digc == 6 & 44 < mindex & mindex < 54, 0,

if(digc == 7 & (mindex % 27) < if(mindex < 50, 18, -1), 0,

if(digc == 8 & mindex < 0, 0,

if(digc == 9 & 35 < mindex & mindex < 45, 0, 1

)))))))))),

if(index < 252,

if(digd == 0 | digd == 10 & mindex > 8 & mindex < 18, 0, 

if(digd == 1 & mindex < 45, 0, 

if(digd == 2 & ((mindex - 9) % 27) > 17 & mindex < 63, 0,

if(digd == 3 & mindex > 26 & mindex < 45, 0,

if(digd == 4 & mindex % 18 < if(mindex < 50, 9, -1), 0,

if(digd == 5 & 35 < mindex & mindex < 54, 0,

if(digd == 6 & 44 < mindex & mindex < 54, 0,

if(digd == 7 & (mindex % 27) < if(mindex < 50, 18, -1), 0,

if(digd == 8 & mindex < 0, 0,

if(digd == 9 & 35 < mindex & mindex < 45, 0, 1

)))))))))), 0

### Parameters

`brightness` determines, well, you know.

`timen` allows the user to shift the input time (Unix time) by any amount of seconds.
))))));
```
<details>
