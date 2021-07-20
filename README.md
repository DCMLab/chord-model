# Towards a Unified Model of Chords in Western Harmony
## Supplementary Material

Hentschel, J.; Moss, F. C.; McLeod, A.; Neuwirth, M. & Rohrmeier, M. (2021). Towards a Unified Model of Chords in Western Harmony. Paper presented at the [Music Encoding Conference 21](https://music-encoding.org/conference/2021/), Alicante, Spain.

### Poster

The file `MEC21_chord_model_poster.pdf` contains a short summary of the
conference paper as well as the supplementary material.

### Model specification

| Variable   | Definition                                                                                                                             |
|------------|------------------------------------------------------------------------------------------------------------------------------------|
| CHORD      | <POS, HARMONY>                                                                                                                     |
| POS        | <[_bar_: (_int_ \| _int-int_)], [_beat_: (_int_ \| _int-int_)], [_time_: _float_]>                                                                 |
| HARMONY    | <NOTE*, [KEY], [(CHORDFUNC [_of_: THEORY])*], [CHORDTYPE], [INV], [ENH], [FORTE], ...>                                               |
| NOTE       | <PITCH, [(NOTEFUNC [_of_: THEORY])*], [ENH], [IMP], ...>                                                                             |
| PITCH      | (PC \| INTERVAL \| SD) [OCTAVE]                                                                                                    |
| PC         | GPC \| SPC \| EPC                                                                                                                  |
| GPC        | _A_ \| _B_ \| _C_ \| _D_ \| _E_ \| _F_ \| _G_                                                                                                    |
| SPC        | GPC [ACCIDENTAL]                                                                                                                   |
| ACCIDENTAL | _b_* \| _#_*                                                                                                                           |
| INTERVAL   | GIV \| SIV \| EIV                                                                                                                  |
| EPC, EIV   | {_0_.._11_}                                                                                                                            |
| SIV        | (_Perfect_ \| _Maj_ \| _Min_ \| _Aug_* \| _Dim_*) GIV                                                                                        |
| SD         | GSD \| SSD                                                                                                                         |
| GIV, GSD   | {_1_.._7_}                                                                                                                             |
| SSD        | GSD [ACCIDENTAL]                                                                                                                   |
| OCTAVE     | _int_                                                                                                                                |
| NOTEFUNC   | _Suspension_ [_of_: (NOTEFUNC \| PITCH)] \| _Root_ \| _Bass_ \| _Melody_ \| _UpperLeadingTone_ \| _CentralTone_ \| _Ornament_ \| ...               |
| THEORY     | _Riemannian_ \| _Tonfeld_ \| _FigBass_ \| _RomanNumeralAnalysis_ \| _Forte_ \| ...                                                           |
| ENH        | _Enharmonic_: (_True_ \| _False_)                                                                                                        |
| IMP        | _Implicit_: (_True_ \| _False_)                                                                                                          |
| FORTE      | _Forte No_: _String_                                                                                                                   |
| KEY        | <_tonic_: PITCH, _mode_: MODE, [_type_: KEYTYPE], [KEY]>                                                                                 |
| MODE       | _Maj_ \| _Min_ \| _Dor_ \| ... \| INTERVAL*                                                                                              |
| KEYTYPE    | _Global_ \| _Local_ \| _Secondary_                                                                                                       |
| CHORDFUNC  | _Tonic_\| _Subdominant_ \| _Dominant_ \| ...                                                                                             |
| CHORDTYPE  | _Maj_ \| _Min_ \| _Dim_ \| _Aug_ \| _MajMaj7_ \| _MajMin7_ \| _MinMaj7_ \| _MinMin7_ \| _Dim7_ \| _HalfDim7_ \| _AugMaj7_ \| _AugMin7_ \| ... \| INTERVAL* |
| INV        | {_0_.._N_}
