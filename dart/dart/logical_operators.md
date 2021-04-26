---
title: "Logical Operators"
description: "Logical Operators"
lead: ""
date: 2021-04-22T16:49:02+02:00
lastmod: 2021-04-22T16:49:02+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 9
toc: true
---

Logical operators are used to create complex logical conditions. For example, if we would want to make sure that someone is older than 18 but younger than 25, we can use the `and` logical operator to combine these two conditions. A logical operator evaluates to a [Boolean]({{< ref "/dart/dart/data_types#boolean" >}} "Dart Boolean").

There are three logical operators: 

- && `and`
- || `or`
- ! `not`

## && - and

Example:

```dart
if (age >= 18 && age <= 25) {
  ...
}
```

The `&&` operator returns `true` only if the conditions on both sides are `true`. If one of the conditions is `false` the entire expression will become `false`.

If `age` would be 20, the left side would be `true` and the right side would be `true`, thus the value of the entire expression would be `true` and the `if` conditions body would run. If `age` would be 40, the left side would be `true` but the right side would be `false`, thus the entire expression would be `false` and the `if` conditions body would *not* run.

## || - or

Example:

```dart
if (age < 25 || age > 60) {
  ...
}
```

The `||` operator returns `true` if one, or both of the conditions on each side is `true`. If both of the conditions are `false` the entire expression will become `false`.

If `age` would be 20, the left side would be `true` and the right side would be `false`, thus the value of the entire expression would be `true` and the `if` conditions body would run. If `age` would be 40, the left side would be `false` and the right side would be `false`, thus the entire expression would be `false` and the `if` conditions body would *not* run.

## ! - not

Example:

```dart
if (!age == 40) {
  ...
}
```

The `!` operator only has one condition. If the condition is `true` the entire expression will be `false` and if the condition is `false`, the entire expression will be `true`. It flips `true` to `false` and `false` to `true`.

If `age` would be 40, the condition would be `true` (`40 == 40`) and the `!` operator would flip this into `false` so the value of the entire expression would be `false` and the `if` conditions body would not run. If age would be 45, the condition would be `false` (`45 == 40`) and the `!` operator would flip this into `true` so the value of the entire expression would be `true` and the `if` conditions body would run.

## Combining Logical Operators

Logical operators can be combined with other logical operators to form even more complex expressions. Let's look at an example:

```dart
var age = 20;
var favoriteColor = "orange";

if ((age >= 18 && age <= 25) || favoriteColor == "green") {
  ...
}
```

Parenthesis have the highest priority so we have to start evaluation the expression inside them. `age >= 18 && age <= 25` would be `20 >= 18 && 20 <= 25` and would evaluate to `true` since both sides of the `&&` operator are `true`. That would leave us with `true || favoriteColor == "green"` and since only one side of the `||` operator must be `true` the right side isn't evaluated and the value of the entire expression would be `true` and the `if` conditions body would run.

If `age` would be 40 instead, the expression inside the parenthesis would be `40 >= 18 && 40 <= 25` and would evaluate to `false`. That would leave us with `false || favoriteColor == "green"`) and we have to evaluate the right condition too since only one side of the `||` operator must be `true`. The right condition (`"orange" == "green"`) will evaluate to `false` so both sides of the `||` operator would be `false`, thus the value of the entire expression would be `false` and the `if` conditions body would not run.
