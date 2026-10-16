# pymeasure.instruments.hp.HP8561B.unlock_harmonic_number

[Owning PyMeasure class, adapter and connection contract](overview.md)

unlock_harmonic_number()

Release harmonic-number lock so frequencies and spans outside the locked harmonic number's range can be selected.

After HNUNLK is executed, a sweep across the desired span can use more than one harmonic. For example, sweeping 18 GHz to 40 GHz makes the analyzer sweep automatically using 6Ч first and then 8Ч.
