# pymeasure.instruments.hp.hp856Xx.HP856Xx.do_fft

HP856Xx.do_fft(*source*, *destination*, *window*)

Compute and display a discrete Fourier transform.
The FFT command runs a discrete Fourier transform on the source trace array, then writes logarithmic magnitude values into the destination array. Any trace is limited to 601 points. Use FFT to convert zero-span amplitude-modulation data into the frequency domain; applying it to a frequency sweep does not produce time-domain information. The spectrum analyzer presents FFT output with a logarithmic amplitude scale. Along the horizontal axis, the left edge represents 0 Hz, while the right edge is Finax-; Fmax equals 300 divided by sweep time. For example, a 60 ms analyzer sweep time gives an Fmax of 5 kHz. The FFT algorithm models the sampled signal as periodic and assumes the analyzer sweep time contains an integral number of periods. With that assumption, the transform corresponds to an infinite-duration waveform made by concatenating time records. Actual measurements may contain a nonintegral number of periods in the record. In that case, the repeated records meet at step discontinuities. Those discontinuities create measurement error, including amplitude uncertainty, where small frequency changes seem to alter signal level, and reduced frequency resolution caused by filter shape factor and sidelobes. Windows are weighting functions applied to the input data so the record ends taper smoothly toward zero, which reduces the discontinuity and the resulting measurement errors.

Parameters:

- **source** (*str*) – Trace selector; provide a `Trace` value, or use ‘TRA’ for Trace A or ‘TRB’ for Trace B

- **destination** (*str*) – Trace selector; provide a `Trace` value, or use ‘TRA’ for Trace A or ‘TRB’ for Trace B

- **window** (*str*) – Trace selector; provide a `Trace` value, or use ‘TRA’ for Trace A or ‘TRB’ for Trace B
