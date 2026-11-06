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

My request to agent: 
Drop photos 3,7,9,13,14,16,18,24,29,32,34,35,36,38,39,41,48 from suspects_balanced_seed0_seoul_00,
reason "indoors, people, food, plants or animals, no street".

Drop photos 2,3,5,6,10,12,13,19,20,21,23,24,25,27,28,31,34,36,39,40,44,46,48 from suspects_balanced_seed0_busan_00, same reason.
Drop photos 1,2,3,5,19,12,13,16,21,25,26,27,33,34,39,42,43,48 from suspects_balanced_seed0_osaka_00, same reason.
Drop photos 4,5,8,11,18,27,28,30,31,33,40,41,42,43,44,45,48 from suspects_balanced_seed0_taipei_00, same reason.
Drop photos 4,5,7,9,10,11,13,14,15,17,19,20,22,26,29,30,32,33,35,36,37,38,42,44,47,48 from suspects_balanced_seed0_tokyo_00, same reason.
Then show me how many photos were dropped per city, and queue the
balanced recipe with this selection for Colab with the tag dropped,
seed 0.

the result: I orginally thought that the score will be higher than the balanced score . But it turns out after checking seed 0 that it scored 0.497 which is lower than the balanceds seed 0 score of 0.5047.
the reason why: I only dropped 101 images which is only 0.2% of the total 44,257 images in total. This is not enough dropped images to really change anything, i would need to go though and hand pick thousands of images for there to be a major change. Therefore, cleaning this small amount of images did not work. I ran seed 1 to confirm. Seed 1 0.502 was also below balances' score. The avg between of the dropped seeds is 0.007 lower than the balanced which is right in the luck range for the model. 

Track B: 
first run: scored 0.487
although this is lower than the inital score for track A there are similarties in that osaka and busan are the lowest scoring cities while tokyo is again the highest. I ran this again and got 0.481

Track B 1 change: 
Im using balance again since this change showed the most change in track A and I want to see how it will fair in track B as well. I expect osaka and busan to go up again while tokyo goes down. I also think that this change will increase the scorse of 0.487
The results: as expected the results were similar to Track A as tokyo went down while busan and osaka went up. I ran two balanced runs with scores of 0.497 and 0.494 which both beat the starter runs.

Track B 2 Change: 
Im going with MobileNetV3. The reason why im picking this as my second change is beacuse while reading the "readme" section of the assignment it stated that MobileNetV3 is a smaller model but it uses a bigger image size (448). This made me think that the image will be clearer since the images are bigger. This would mean that the model will have a clear look at each image and could have a higher score than the balanced score. I also switched to MobileNetV3 since with bigger images sizes ResNet18 will go over the 2 billion limit unlike MobileNetV3.