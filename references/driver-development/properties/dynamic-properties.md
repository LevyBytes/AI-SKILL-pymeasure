# Dynamic properties

Earlier sections show that Python properties are a compact way to model an instrument's programming interface. PyMeasure adds dynamic property behavior, so subclasses or individual instances can adjust property definitions. This supports several useful cases with little syntax.

To turn on dynamic behavior for a property, set its `dynamic` parameter to `True`.

Once `dynamic` is enabled, specially named attributes, declared on either a class or an instance, can override parameters from the original property definition. Define an attribute named &lt;property name&gt;_<property_parameter> and assign the desired value. Avoid accidentally creating class or instance attributes that match this pattern, because such names may change property behaviour unintentionally.

Note

Because these special attributes should not be confused with ordinary class or instance attributes, they support assignment only and cannot be read.

This dynamic mechanism applies to every property parameter except `dynamic` and `docs`; see [`Instrument.control`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.control), [`Instrument.measurement`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.measurement), and [`Instrument.setting`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.common_base.CommonBase.setting).
