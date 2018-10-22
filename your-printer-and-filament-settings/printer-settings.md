# Printer Settings \(Default\)

## CoreXY Motion Settings

{% hint style="warning" %}
Because the printer uses a CoreXY Motion setup, X and Y motion settings _**Must Be Identical.**_
{% endhint %}

### Feedrate \(Speed\)

X Motion: 9000 mm/min

Y Motion: 9000 mm/min

Z Motion: 2300 mm/min

#### Input Code:

```text
M203 X# Y# Z#
```

### Acceleration

X Acceleration: 3000 mm/s^2

Y Acceleration: 3000 mm/s^2

Z Acceleration: 75 mm/s^2

#### Input Code:

```text
M201 X# Y# Z#
```

### Jerk

X Jerk: 350 mm/min

Y Jerk: 350 mm/min

Z Jerk: 50 mm/min

#### Input Code:

```text
M566 X# Y# Z#
```

## Compound Mixing: Extruder Motor Settings

{% hint style="info" %}
E parameter format: E \[ Left Motor Value \] : \[ Right Motor Value \]
{% endhint %}

### Feedrate \(Speed\)

Left Motor: 5000 mm/min

Right Motor: 5000 mm/min

#### Input Code:

```text
M203 E#:#
```

#### Example:

I want to set different rates between motors:

 Left motor feedrate \(speed\): 9000 mm/min 

Right motor feedrate \(speed\): 6000 mm/min

Input Code:

```text
M203 E#:#
```

### 

### Acceleration

Left Motor: 150 m/s^2

Right Motor: 150 m/s^2

#### Input Code:

```text
M201 E#:#
```

#### Example

I want to set different rates between motors:

 Left motor acceleration: 2000 mm/sec^2 

Right motor acceleration: 3000 mm/sec^2

Input Code:

```text
M201 E#:#
```



### Allowable Instantaneous Speed Change \(Jerk\)

Left Motor: 60 mm/min

Right Motor: 60 mm/min

#### Input Code:

```text
M566 E#:#
```

#### Example

I want to set different rates between motors:

 Left motor Jerk: 900 mm/min

Right motor Jerk: 600 mm/min

Input Code:

```text
M566 E#:#
```

## Single K'Tana: Extruder Motor Settings

{% hint style="info" %}
E parameter format: E \[ Left Motor Value \] : \[ Right Motor Value \]
{% endhint %}

### Feedrate \(Speed\)

Left Motor: 5000 mm/min

Right Motor: 5000 mm/min

#### Input Code:

```text
M203 E#:#
```

#### Example:

I want to set different rates between motors:

 Left motor feedrate \(speed\): 9000 mm/min 

Right motor feedrate \(speed\): 6000 mm/min

Input Code:

```text
M203 E#:#
```

### 

### Acceleration

Left Motor: 150 mm/s^2

Right Motor: 150 mm/s^2

#### Input Code:

```text
M201 E#:#
```

#### Example

I want to set different rates between motors:

 Left motor acceleration: 2000 mm/sec^2 

Right motor acceleration: 3000 mm/sec^2

Input Code:

```text
M201 E#:#
```



### Allowable Instantaneous Speed Change \(Jerk\)

Left Motor: 60 mm/min

Right Motor: 60 mm/min

#### Input Code:

```text
M566 E#:#
```

#### Example

I want to set different rates between motors:

 Left motor Jerk: 900 mm/min

Right motor Jerk: 600 mm/min

Input Code:

```text
M566 E#:#
```



## Bed Probe Settings:

### XY Offsets

X Offset: - 43.0

Y Offset: 25.0

#### Input Code:

```text
G31 T4 X-43 Y24
```

These values do not change. Do Not Change.



### Z Height Offset

This varies between each printer due to two reason:

1. The flatness of your bed directly affects the Z height offset. This will vary between each printer.
2. The absolute position of the bed probe \(as a whole\) can shift up and down, if not fixated.

#### Input Code:

```text
G31 Z#
```

## Z Limit Switch Settings:

### Height Value

This varies between each printer due to two reason:

1. The flatness of your bed directly affects the Z height offset. This will vary between each printer.
2. The absolute position of the Z Limit Switch can vary between printers.

#### Input Code:

Open up machine\_zendstop.g \(located under the sys folder\). Follow instructions inside the file.

```text
G92 Z#
```

## Temperature Settings

### PID Parameters

For Compound:

Proportional value \(Kp\): 22.1

Integral Value \(Ki\): 1.154

Derivative Value \(Kd\): 54.1

Maximum PWM: 1



For K'Tana:

Proportional value \(Kp\): 10.7

Integral Value \(Ki\): 0.477

Derivative Value \(Kd\): 38.8

Maximum PWM: 0.75



#### Input Code:

{% hint style="warning" %}
Changing these values can cause unexpected fluctuations in temperature. Proceed with caution.
{% endhint %}

For Compound Mixing:

```text
M301 H2 P# I# D# S1
```



For Left, Single K'Tana:

```text
M301 H1 P# I# D# S0.75
```



For Right, Single K'Tana:

```text
M301 H2 P# I# D# S0.75
```



### Maximum, Allowable Temperature

Maximum Temperature: 320 C

#### Input Code:

{% hint style="warning" %}
If changing this value, allow for a + 15 C buffer between your intended maximum, allowable temperature.
{% endhint %}

For Compound:

```text
M143 H2 S#
```



For Left, Single K'Tana:

```text
M143 H1 S#
```



For Right, Single K'Tana:

```text
M143 H2 S#
```



