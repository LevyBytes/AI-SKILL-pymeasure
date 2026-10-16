# pymeasure.instruments.hp.hp856Xx.HP856Xx.set_auto_couple

HP856Xx.set_auto_couple()

Put center frequency step-size, sweep time, input attenuation, resolution bandwidth, and video bandwidth back into coupled mode.

These functions may be recoupled one by one or together. The spectrum analyzer selects suitable values for them. Video bandwidth and resolution bandwidth follow the coupled ratios kept in `resolution_bandwidth_to_span_ratio` and `video_bandwidth_to_resolution_bandwidth`. If ratios have not been selected, the default ratios are 1.0 and 0.011, respectively.
