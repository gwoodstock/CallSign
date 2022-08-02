# CallSign Technical Assessment
Presented by Gene Woodstock, Data Scientist

## Problem [^bignote]
Our client is a ski company. At one of their ski parks, they are facing long queues at the ski lifts. They would like us to <u>reduce the amount of time their customers spend waiting.</u> In order to do so, the company would like us to investigate two ski lift alternatives.

1.	Install a faster ski lift; replacing existing setup.
2.	Install a second ski lift, identical to the ski lift currently in operation.
3.  Keep exisiting setup as is. Make no changes.

<br>

## Data
| Lift Type      | Queue Rate      | Time on Lift | Time on Slopes |
| -------------- | --------------- | ------------ | -------------- |
| Faster Lift    | 5 riders / min  | 5 min        | 5 min          |
| Second Lift    | 10 riders / min | 10 min       | 5 min          |
| Existing setup | 5 riders / min  | 10 min       | 5 min          |

<br>

## Assumptions

-  Three components to the ski park.

    1. Queueing at the Mountain Base (Queue Rate):
        - Riders at the base of the mountain prepare to be transported to the mountain top via a ski lift.
    2. The Ski Lift (Time on Lift)
        - Riders utilize a ski lift to ascend to the top of the mountain.
    3. The Mountain Slopes (Time on Slopes)
        - Riders ski/board down the side of the mountain

<br>

- All customers must be in one of the above 3 locations.

<br>

- Customers wait in the queue, go up the lift, and ski down the slope. This cycle is repeated.
    - Queue, lift, slope, queue, lift, slope, etc.


## Solution

The proportion of skiers at each location on the mountain will be constant at all times. The expected number of skiers will be the product of the number of skiers per minute whom are ascending the mountain and the time spent (in minutes) at each location. The ski lift is "bottle necking" the flow of skiers. Therefore, the rate of travel will be constant across all locations, with a queue forming at the base of the mountain as the bottle neck is cleared.

skiers will always be in 1 of 3 ordinal locations: queueing for a ski lift, riding a lift, or skiing down the slopes. The rate and time spent at 2 of the 3 locations have been given for each of the 3 lift options. Therefore, the number of skiers at the 3rd location (the queue) will always be the total number of skiers minus the sum of skiers at the other 2 locations (the lift and the slopes).

<br>

## Formulas
Skiers on the lift = Time on lift * Lift Rate \
Skiers on the slopes = Time on slopes * Lift Rate

Skiers in queue = (Total Skiers - (Skiers on Lift + Skiers on Slopes)) \
Time in Queue = Skiers in queue / Lift Rate

<br>

## Visualize
![Wait times](/Assets/wait-times.png "Wait times by option")

[^bignote]: Case study question has been adapted to the above format for clarity of message. An unedited version can be found linked below. \
[Unedited Prompt .docx](./Case-Study/Original_Case_Study_Question.docx) \
[Unedited Prompt .pdf](./Case-Study/Original_Case_Study_Question.pdf)