# jazzChords2DB
 Read jazz chord changes and store them into a database.
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
 In some cases that is easy to fix, in others not. Therfore currently for every song a 
 plausibility check is called and if it's not obvious that the nuber of accidentals are correct,
 an editor is called with the current song loaded, giving the option to edit this info. But the changes will not effect before the next run.
 Currently the next run stores the song a second time, there is no update implemented. So it may be a good idea to delete the chord database before running a second time.
 There is option to skip the plausibilit check and one to skip until the filename starts with a letter greater than a given reference letter. This is because you'll unlikely edit all changes in doubt at a time.
 
 ParseLeadSheetFile.check_plausibility(ParseLeadSheetFile.number_of_accidentals,
                                                          roman_numeric_interpretation)

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
 
