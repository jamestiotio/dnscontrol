---
name: LOC_BUILDER_DMM_STR
parameters:
  - label
  - str
  - alt
  - ttl
parameter_types:
  label: string
  str: string
  alt: float32
  ttl: int
---

`LOC_BUILDER_DMM({})` actually takes an object with the following properties:

  - label (optional, defaults to `@`)
  - str
  - alt
  - ttl (optional)

A helper to build [`LOC`](../domain/LOC.md) records. Supply three parameters instead of 12.

Internally assumes some defaults for [`LOC`](../domain/LOC.md) records.


Accepts a string with decimal minutes (DMM) coordinates in the form: 25.24°S 153.15°E

Note that the following are acceptable forms (symbols differ):
* `25.24°S 153.15°E`
* `25.24 S 153.15 E`
* `25.24° S 153.15° E`
* `25.24S 153.15E`

{% code title="dnsconfig.js" %}
```javascript
D("example.com","none"
  LOC_BUILDER_STR({
    label: "tasmania",
    str: '42°S 147°E',
    alt: 3,
  })
);

```
{% endcode %}


Part of the series:
 * [`LOC()`](../domain/LOC.md) - build a `LOC` by supplying all 12 parameters
 * [`LOC_BUILDER_DD({})`](../record/LOC_BUILDER_DD.md) - accepts cartesian x, y
 * [`LOC_BUILDER_DMS_STR({})`](../record/LOC_BUILDER_DMS_STR.md) - accepts DMS 33°51′31″S 151°12′51″E
 * [`LOC_BUILDER_DMM_STR({})`](../record/LOC_BUILDER_DMM_STR.md) - accepts DMM 25.24°S 153.15°E
 * [`LOC_BUILDER_STR({})`](../record/LOC_BUILDER_STR.md) - tries the cooordinate string in all `LOC_BUILDER_DM*_STR()` functions until one works