# pymeasure.instruments.hp.hp856Xx.HP856Xx.video_average

HP856Xx.video_average

Enable or configure video averaging. Video averaging smooths the displayed trace without requiring a narrow bandwidth. ‘video_average’ puts the IF detector in sample mode (see the DET command) and smooths by averaging successive traces together. The detector mode can still be changed during video averaging. This feature works only on trace A, and trace A must be in clear-write mode before ‘video_average’ can run. After ‘video_average’ runs, the analyzer screen shows the number of averaged sweeps at the top. Video averaging can reveal changes across the whole trace much faster than narrow video filters. Narrow video filters require long sweep times, which may be undesirable. Although video averaging uses more sweeps, those sweeps are faster; in some cases it can smooth a trace as quickly as a video filter.

Type: `str, int`
