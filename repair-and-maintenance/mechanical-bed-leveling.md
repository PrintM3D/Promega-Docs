# Mechanical Bed Leveling

### Leveling the Bed

As covered in the [Bed Leveling & Probing](../advanced-setup-guides/bed-leveling-and-probing.md) guide, bed leveling compensation will work for differences of about 3mm across the entire bed. Leveling your bed can be done by skipping teeth on the bed in specific corners. If your bed is extremely un-leveled, it will not be movable by hand.

Look at your bed and determine if one side is visibly higher than the other side.

Remove the binder clip if you have placed one on the Z-motor belt.

Gently pull up on the corner that you want to skip. Apply pressure until you feel the corner give with a loud click. 

{% hint style="warning" %}
Do not skip the bed near the belt clamps as it can break your belt clamps.
{% endhint %}

![](../.gitbook/assets/skippingthebed%20%281%29.gif)

Once the bed is level enough to the point where it drops by itself, move the bed up to the nozzle by hand. The bed is best lifted up from the points pictured below. 

![](../.gitbook/assets/wheretoholdbed%20%282%29.jpg)

Lift slowly or you will skip the bed. 

{% hint style="warning" %}
Moving the bed too fast can also fry your Duet board, so be careful.
{% endhint %}

When the bed is touching the nozzle, determine the offset of the Z-sliders to the top belt clamps to determine whether the bed is level. This will give you a good enough estimate to level the bed.

{% hint style="info" %}
Bed leveling compensation with `G29` can take care of the rest.
{% endhint %}

![Comparing the Distance in Each Corner](../.gitbook/assets/zvlnwj7ervnsrbpg-distancebedcorners.jpg)

{% hint style="info" %}
The bed can be leveled more accurately by using a caliper to measure the distance between the bed and the top of the Z-slider rails and comparing the corners.
{% endhint %}

