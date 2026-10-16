# pymeasure.instruments.hp.hp856Xx.HP856Xx.video_bandwidth

HP856Xx.video_bandwidth

Set video bandwidth. This control is normally coupled and chosen from the ratio set by the VBR command; if none is selected, default ratio 1.0 applies. Video bandwidth filters, or smooths, post-detected video information. Manual selection is also available over 1 Hz to 3 MHz. If requested video bandwidth falls below 300 Hz while resolution bandwidth is at least 300 Hz, the IF detector switches to sample mode. For the same total measurement time, lowering video bandwidth or increasing video averages generally smooths the trace by a similar amount. When video averages exceed 25, video bandwidth at one-third or less of resolution bandwidth is preferred. With very high averaging and video bandwidth equal to resolution bandwidth, internal math limits can produce about 0.4 dB noise overresponse on the logarithmic scale. Narrower video bandwidths make that overresponse negligible, less than 0.1 dB.

Type: `int`
