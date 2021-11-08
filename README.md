# Towards a Unified Model of Chords in Western Harmony

Hentschel, J.; Moss, F. C.; McLeod, A.; Neuwirth, M. & Rohrmeier, M. (2021). Towards a Unified Model of Chords in Western Harmony. Paper presented at the [Music Encoding Conference 21](https://music-encoding.org/conference/2021/), Alicante, Spain.

## Abstract

Chord-based harmony is an important aspect of many types of Western music, across genres, regions, and historical eras. However, the consistent representation and comparison of harmony across a wide range of styles (e.g. classical music, Jazz, Rock, or Pop) is a challenging task. Moreover, even within a single musical style, multiple theories of harmony exist, each relying on its own (possibly implicit) assumptions and leading to harmonic analyses with a distinct focus (e.g. on the root of a chord vs. its bass note) or representation (e.g. spelled vs. enharmonic pitch classes). Cross-stylistic and cross-theory comparisons are therefore even more difficult, particularly in a large-scale computational setting that requires a common overarching representation. To address these problems, we propose a model which allows for the representation of chords at multiple levels of abstraction: from chord realizations on the score level (if available), to pitch-class collections (including a potential application of different equivalences, such as enharmonic or octave equivalence), to pitch- and chord-level functions and higher-order abstractions. Importantly, our proposed model is also well-defined for theories which do not specify information at each level of abstraction (e.g., some theories make no claims about harmonic function), representing only those harmonic properties that are explicitly included and inducing others where possible (e.g., deriving scale degrees from root and key information). Our model thus represents an important step towards a unified representation of harmony and its various applications.

## Poster

The file `MEC21_chord_model_poster.pdf` contains a short summary of the
conference paper as well as the supplementary material.

## Model specification

Our proposed model represents chords as graphs, where the chord label and its position in a piece form a central node, and properties of the chord are labeled edges and attached nodes. In the following table we show the formal definition of our model as a grammar, where terminal symbols are listed in _italics_. `...` indicates that custom properties and values may be defined and added for flexibility.

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


## Overview of some references with harmonic features

| Reference                       |             Absolute Root             | Relative Root | Bass Note | Chord Type | Chord Inversion | Chord Extension | Suspensions | Harmonic Function | Pitch Classes | Pitch-Class Sets | Key or Mode |
|---------------------------------|:-------------------------------------:|:-------------:|:---------:|:----------:|:---------------:|:---------------:|:-----------:|:-----------------:|:-------------:|:----------------:|:-----------:|
| Broze & Shanahan (2013)         |                   ✓                   |               |     ✓     |      ✓     |                 |        ✓        |      ✓      |                   |               |                  |             |
| Burgoyne et al. (2011)          |                   ✓                   |               |           |      ✓     |                 |        ✓        |             |                   |               |                  |             |
| Cambouropoulos et al. (2014)    |                                       |               |           |            |                 |                 |             |                   |       ✓       |         ✓        |      ✓      |
| Harte (2005)                    |                   ✓                   |               |     ✓     |      ✓     |                 |        ✓        |      ✓      |                   |               |                  |             |
| Huron (2002)                    |                                       |       ✓       |           |      ✓     |        ✓        |        ✓        |      ✓      |                   |               |                  |             |
| Moss et al. (2020)              |                                       |       ✓       |     ✓     |      ✓     |                 |        ✓        |             |                   |               |                  |      ✓      |
| Nápoles Lopes & Fujinaga (2020) |                                       |       ✓       |           |      ✓     |        ✓        |        ✓        |             |                   |               |                  |      ✓      |
| Neuwirth et al. (2018)          |                                       |       ✓       |           |      ✓     |        ✓        |        ✓        |      ✓      |                   |               |                  |      ✓      |
| Rohrmeier (2008)                |                                       |       ✓       |           |            |                 |                 |             |                   |       ✓       |         ✓        |             |
| Rohrmeier (2011)                |                   ✓                   |       ✓       |     ✓     |      ✓     |        ✓        |        ✓        |      ✓      |         ✓         |               |                  |      ✓      |
| Rohrmeier (2011)                |                   ✓                   |       ✓       |     ✓     |      ✓     |        ✓        |        ✓        |      ✓      |                   |               |                  |      ✓      |
| Selway et al. (2020)            |                   ✓                   |               |           |      ✓     |                 |                 |             |         ✓         |               |                  |             |
| Temperley (2009)                |                                       |       ✓       |           |            |                 |                 |             |                   |               |                  |             |
| Temperley & deClerq (2013)      |                                       |       ✓       |           |            |                 |                 |             |                   |               |                  |             |
| Tymoczko et al. (2019)          |                                       |       ✓       |           |      ✓     |        ✓        |        ✓        |             |                   |               |                  |      ✓      |
| White & Quinn (2016)            |                                       |               |           |            |                 |                 |             |                   |       ✓       |         ✓        |      ✓      |
|                                 | Career Development Plan               | D2            |           |            |                 |                 |             |                   |               |                  |             |
|                                 | Research Data Management Plan         | D3            |           |            |                 |                 |             |                   |               |                  |             |
|                                 | 1st year report                       |               |           |            | D4              |                 |             |                   |               |                  |             |
|                                 | Final report                          |               |           |            |                 |                 |             |                   | D5            |                  |             |
| WP5: Communication              |                                       |               |           |            |                 |                 |             |                   |               |                  |             |
| T13                             | Expert workshop                       |               |           |            |                 |                 |             |                   |               |                  |             |
| T14                             | Event for wider public                |               |           |            |                 |                 |             |                   |               |                  |             |
| T15                             | Conference presentation + proceedings |               |           |            | D6              |                 |             |                   |               |                  |             |
| T16                             | Blog posts                            |               |           |            |                 |                 |             |                   | D7            |                  |             |
| T17                             | Scientific Article                    |               |           |            |                 |                 |             | D8                |               |                  |             |
| Milestones                      |                                       |               | M1        |            | M2              |                 | M3          |                   |               |                  |             |



