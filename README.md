# jazzChords2DB
 read jazz chord changes into a database
 Many even longer chord patterns in jazz standards are widely reused in other songs.
 I want to be able to identify those similarities regardless of the original key of the score.
 For that I reduce the color and complexety of the chords in the scores and store them in simpler 
 key independent versions inspired by Roman Numeral Notation in addition to the original changes.

 Input is currently a directory with community maintained lead sheets in IMPROVISOR's ls format.
 see https://www.cs.hmc.edu/~keller/jazz/improvisor/
 There are roughly tree thousand songs at the moment.

 Slash idler get replaced by the preceding chord.
 Repeated chords in one measure get skipped.
 Sadly the number of accidentals that leads to the songs key is not alway filled reliably.
 In some cases that is easy to fix, in others not.

# Search for similarities:
 quite good examples:
 Ladybird - Half Nelson
 
 or
 
 Rose Room - In a Mellow Tone
# instructive example queries:
 select Title, Composer from jazz_changes where    sri like  "%I Idim | IIm V7 | IIm V7 | I |%";
 
 select Title, Composer from jazz_changes where ssri1l like  "%IIm | V7 | I | IV |%";
 
 select Title, Composer from jazz_changes where ssri1l like  "%I | IIIm | IIm | IIm |%";
 
 select Title, Composer, changes from jazz_changes where ssri1l like  "%I | I | Vm | I7 | IV | IV | bVII7 | bVII7 | I | I | II7 | II7 | IIm | VI7 | IIm | V7 |%";
 
