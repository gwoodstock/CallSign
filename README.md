# CallSign

## Problem [^bignote]
Our client is a ski company. At one of their ski parks, they are facing long queues at the ski lifts. They would like us to reduce the amount of time their customers spend waiting. In order to do so, the company would like us to investigate two ski lift alternatives.

1.	Installing a Faster Ski Lift; replacing existing setup
2.	Installing a 2nd Ski Lift, which is exactly like the current ski lift
3.  Keep exisiting setup as is. Make no changes.

<br>

## Data
| Lift Type      | Queue Rate      | Time on Lift | Time on Slopes |
| -------------- | --------------- | ------------ | -------------- |
| Faster Lift    | 5 riders / min  | 5 min        | 5 min          |
| 2nd Lift       | 10 riders / min | 10 min       | 5 min          |
| Existing setup | 5 riders / min  | 10 min       | 5 min          |

<br>

## Additional Information

-  Three components to the ski park

    1. Queueing at the Mountain Base (Queue Rate):
        - Riders at the base of the mountain prepare to be transported to the mountain top via a ski lift.
    2. The Ski Lift (Time on Lift)
        - Riders utilize a ski lift to ascend to the top of the mountain.
    3. The Mountain Slopes (Time on Slopes)
        - Riders ski/board down the side of the mountain

<br>

- All customers must be in one of the above 3 locations

<br>

- Customers wait in the queue, go up the lift, and ski down the slope. This cycle is repeated.
    - Queue, lift, slope, queue, lift, slope, etc


[^bignote]: Case study question has been adapted to the above format for clarity of message. An unedited version can be found linked below \
[Unedited Prompt .docx](./Original_Case_Study_Question.docx) \
[Unedited Prompt .pdf](./Original_Case_Study_Question.pdf)