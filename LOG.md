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

## 2026-11-05 balanced (Track A)
- changed: draw every city equally often — in sample_weights, weight each photo 1 over its city's count
- why: from my baseline guess: I think that the score for busan, osaka, and toyko will change since toyko has over 13 thousand photos while busan only has a little over 5 thousand.
- validation: 0.507 (balanced mean of seeds 0.5047, 0.5096; baseline mean 0.491 of seeds 0.4948, 0.4881)
- what it means: both balanced seeds (0.5047, 0.5096) had higher scores than the baseline seeds (0.4948, 0.4881). Addtionally the mean increased by (0.016)  from 0.491 to 0.507. This confirms my guess that if each city had an equal chance of getting drawn the scores would change with tokyo's score going down and busan and okasa's score rising.

Plan: try noflip next (remove left-right flips).
tne reason why I picked this was to see the model will be affected if it saw the images facing the way they actually are. Such as, the cars driving on the correct side or the writing being read correctly.
the result: the validation score was :0.502 
comparing it to my balanced rate of 0.5047 the difference is 0.0027 is less than my luck range of 0.007 I got from my baseline. This means nothing really changed. So i will be using the balanced recipe with the flip


Step 3:
while looking at the mistakes that the model made i noticed that it was having a hard time with historical buildings. Another thing that was common throughout these images were cars. These images of cars/vehicals were taken from a side profile so the model had no idea where it was actually taken.

Step 7: 
Rule: I will drop pictures that were taken inside and those that pictures of humans, food, and misc things (plants, and animals). the reason why is because the model will have a hard time guessing the right city by using these types of images.
Guess: by dropping these the model will have an easier time guessing than it has so far and score higher than the balanced mean of 0.5071.