# pymeasure.instruments.hp.hp856Xx.HP856Xx.create_fft_trace_window

HP856Xx.create_fft_trace_window(*trace*, *window_mode*)

Create a trace-window array for the fast Fourier transform (FFT) function.

The trace-window function builds a trace array using one of three built-in algorithms: UNIFORM, HANNING, or FLATTOP. With the FFT command, these algorithms produce passband shapes that trade off amplitude uncertainty, sensitivity, and frequency resolution. See the FFT command description for details.

Parameters:

- **trace** (*str*) – Trace selection, either from `Trace` or ‘TRA’ for Trace A or ‘TRB’ for Trace B

- **window_mode** (*str*) – Window selection, either from `WindowType` or ‘HANNING’, ‘FLATTOP’ or ‘UNIFORM’
