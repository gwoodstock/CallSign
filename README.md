# CallSign Technical Assessment
Prepared by Gene Woodstock, Data Scientist

## Problem [^bignote]
Our client is a ski company. At one of their ski parks, they are facing long queues at the ski lifts. They would like us to <u>reduce the amount of time their customers spend waiting.</u> In order to do so, the company would like us to investigate two ski lift alternatives.

1.	Speed up existing or install faster ski lift.
2.	Install a second ski lift, identical to the ski lift currently in operation.
3.  Keep existing setup as is. Make no changes.

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

<br>

## Solution

The proportion of skiers at each location on the mountain will always be constant. 

The expected number of skiers will be the product of the number of skiers per minute whom are ascending the mountain and the time spent (in minutes) at each location. 

The ski lift is "bottle necking" the flow of skiers. Therefore, the rate of travel will be constant across all locations, with a queue forming at the base of the mountain as the bottle neck is cleared.

Skiers will always be in 1 of 3 ordinal locations: queueing for a ski lift, riding a lift, or skiing down the slopes. 

The rate and time spent at 2 of the 3 locations have been given for each of the 3 lift options. Therefore, the number of skiers at the 3rd location (the queue) will always be the total number of skiers minus the sum of skiers at the other 2 locations (the lift and the slopes).

<br>

## Formulas

Skiers on the lift = Time on lift * Lift Rate \
Skiers on the slopes = Time on slopes * Lift Rate

Skiers in queue = (Total Skiers - (Skiers on Lift + Skiers on Slopes)) \

Time in Queue = Skiers in queue / Lift Rate

<br>


y = time in queue \
x = total skiers on the mountain

### Existing Lift
**Skiers:** \
Lift: 10 min * 5 skiers/min = 50 skiers \
Slopes: 5 min * 5 skiers/min = 25 skiers \
Queue: (x skiers - 75 skiers) ) / (5 skiers/min) 
<br>

**Time:**
Queue: y = 0.2x - 15

### Faster Lift
**Skiers:** \
Lift: 5 min * 5 skiers/min = 25 skiers \
Slopes: 5 min * 5 skiers/min = 25 skiers \
Queue: (x skiers - 50 skiers) / (5 skiers/min)
<br>

**Time:**
Queue: y = 0.2x - 10

### Second Lift
**Skiers:** \
Lift: 10 min / 10 skiers/min = 100 skiers
Slopes: 5 min * 10 skiers/min = 50 skiers
Queue: (x skiers - 150 skiers) / 10 skiers/min
<br>

**Time:** \
Queue: y = 0.1x - 15


## Findings

| Option | Formula |
| ------ | ------- |
| Existing |  y = 0.2x - 15 |
| Faster | y = 0.2x - 10 |
| Second | y = 0.1x - 15 |

The functions for calculating queue wait time are linear. Given the number of skiers on the mountain can never be negative, the wait time for Second will always be less than Existing. Existing will always be less than Faster.

Installing a second lift will reduce wait times more than increasing the speed of the existing lift or keeping the existing system.

Further questions remain regarding the business decision to do so. Discussed below...

<br>

## Tableau Dashboard

Explore the data yourself on an [interactive dashboard](https://public.tableau.com/shared/B6MZBBSQR).


![Preview Image](/Assets/tableau.png "Preview Image. Click link above to explore!")

<br>

## Presentation Slides

A more [comprehensive walkthrough](./Ski%20Lift%20Case%20Study.pdf) of the project via Google Slides in .pdf form.

<br>

## Discussion

### Second Lift
- Relative to a faster lift, additional time is spent sitting on a lift chair traveling up the mountain. 
    - Is this better?
- Skiers may avoid long lines during peak hours by spending more time in the lodge gift shop or dining at the restaurant.
- How much does a second ski lift cost?
    - Is loss from customer churn greater than the construction cost, staff to operate, and maintenance for a new lift?
- Will slopes time descending the mountain be identical for both lifts?

### Existing Lift, Adjusted
- Does risk of injury increase when speeding up the ski lift?
Are less experienced skiers more likely to be intimidated by the increase in speed? 
- Will additional maintenance be required?
    - Will down time increase due to additional maintenance?
- Will the rate of skiers reaching the peak double due to the increase in speed?
- Would shorter wait times from slowing down the existing lift accomplish the same objective?
- On days where wait times will always be 0, would increasing lift speed increase enjoyment for high volume skiers?

<br>

## Thank you!
I hope you enjoy reviewing this project half as much as I had making it! More of my work can be found on my [portfolio](https://www.GeneWoodstock.com).

<br>
<br>

[^bignote]: Case study question has been adapted to the above format for clarity of message. An unedited version can be found linked below. \
[Unedited Prompt .docx](./Case-study/Original_Case_Study_Question.docx) \
[Unedited Prompt .pdf](./Case-study/Original_Case_Study_Question.pdf)