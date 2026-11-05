# Log

One entry for each recipe, selection or Track B model you train, newest at
the bottom. The numbers come from `experiments.csv`. "Why" and "what it means"
are in your own words: your agent asks you for them and does not make them up.
End the log with your plan for what to try next.

<!-- The form of an entry:

## <date> <tag> (Track A or B)
- changed: what is different from the run before
- why: your reason
- validation: 0.000 (before: 0.000)
- what it means: what you think the result says
-->

## 2026-11-05 baseline (Track A)
- changed: nothing — this is the starter recipe
- why: I think some ways that the model will use to differeiate which city is which is by the languages of written on signs or billboards, ect. Another way is to tell would be the architecture between each city, as tokyo and seoul have more skyscrapers than busan and osaka. Busan has a lot of ocean view pictures compaired to the other cites. Taipei has a lot of scooters. I also noticed that Osaka has a lot of neon billboards which could help the model guess that its osaka.
- validation: 0.495 (seed 0), 0.488 (seed 1)
- what it means: Strongest city: Tokyo. Weakest cities: Busan and Osaka. Guess for balanced: I think that the score for busan, osaka, and toyko will change since toyko has over 13 thousand photos while busan only has a little over 5 thousand. This could mean that if the model can see the same amount of pictures for each city the scores for each would change a lot.

Plan: try balanced next (draw every city equally often).

