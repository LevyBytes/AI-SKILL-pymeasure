# pymeasure.instruments.hp.hp856Xx.HP856Xx.store_short

HP856Xx.store_short()

Average the currently displayed trace A data with the previously saved open data, then store the averaged result in trace B.

This command is paired with `store_open()` and must be run after `store_open()` for correct behavior. See the `store_open()` command description for details. The open/short average trace state is kept in state register #8.
