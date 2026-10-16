# pymeasure.instruments.hp.hp856Xx.HP856Xx.adjust_if

HP856Xx.adjust_if

Enable or disable automatic IF adjustment. This function is normally on. Because the IF is adjusted continuously, the IF alignment routine rarely needs to be run. When IF adjustment is inactive, an “A” appears on the left side of the display.

- “FULL” performs IF adjustment across all IF settings.

- “CURR” performs IF adjustment only for the IF settings currently on display.

- False disables continuous IF adjustment.

- True enables continuous IF adjustment again.

Type: `bool, str`
