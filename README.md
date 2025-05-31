# rcplang

A cooking recipe language for sharing & documentation.


## goals & constraints

- writable with any text editor
- readable also without compiler
- option to add "plugins" which can extend the model


## specification

The specification is heavily leaning towards markdown and is using some of the elements,
so that it can be used with a markdown reader, but this language is using just a minor
subset of markdown and should not be confused with it.


### header

Is enclosed by "---" (3 dashes) and can contain key-values.

Example:
```
---
title: Honey Salad Dressing
description: A heavy, flavorfull salad dressing, great for an evening with red wine and cheese.
author: John Doe
---
```


### steps

Each step consists of 3 sections. Multiple inputs, one output and the instructions how 
to transform the inputs to the output.


#### output

The output is a place holder of the end result of a specific step. For now I defined
it as "$..." where the dots can be lower-case letters and numbers.

Example:
```
$step1
```


#### inputs

inputs can be ingrediences, but also the outputs from other steps.

Example:
```
- Mustard
- Honey
- $step1
- Salt
- Pepper
- Vinegar
```

#### instructions

Instructions are just the description on what you have to do in this step

## example (with possible extension)

```rcplang
---
title: Honey Salad Dressing
description: A heavy, flavorfull salad dressing, great for an 
evening with red wine and cheese.
author: John Doe
---
- Mustard {amount:"1 EL", calories:"100"}
- Honey {amount: "1 tsp"}
- Salt {amount: "1 pinch"}
- Pepper
- Vinegar
$step1
Add all water solubles in a bowl and mix.

- $step1
- Olive oil {amount: "3 tsp"}
$step2
Mix in very slowly the olive oil.

- $step2
- Herbs optional
- Water
$honeySaladDressing
Add herbs as desired.
Usually it is quite thick at that point.
Add water to thin it until desired.      
```
