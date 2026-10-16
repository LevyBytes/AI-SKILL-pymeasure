# pymeasure.instruments.hp.hp856Xx.HP856Xx.protect_state_enabled

HP856Xx.protect_state_enabled

Enable or disable protection against writing new data to state or trace registers. When set to ‘True’, the registers are “locked”; existing data can still be recalled, but it cannot be erased or overwritten. To unlock the registers for new storage, set ‘protect_state_enabled’ off by passing ‘False’.

Type: `bool`
