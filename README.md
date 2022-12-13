# data-sim
We need to stress test the app with lots of data. Since it's unlikely that we will enter lots of data every time during QA, we need to automate/simulate this. This will provide us insights into the app's performance and the correctness.

Let's add a button called Generate Data on the settings page. Every time the user presses this button, data is generated using the following method. Please note that this feature is only for debug purposes and will not ship with the final app.

## Generate data
Generate data from the current date until child's birthdate. If birthday was 4 months ago, then generate data for 4 months.

## Settings for generating data
For each day generate data using the min/max values provided in: https://divya-clicksie.github.io/data-sim/settings.json.
The idea is that we could change the statistics online and generate new data with variable statistics. 

## Events

Pee: Generate `min` to `max` number of events per day at random time. 

Poo: Generate `min` to `max` number of events per day at random time. 

Formula and Pumped: Generate `min` to `max` number of events per day at random time. For each event, add a random volume between `min` and `max` in steps of `0.5`. If the baby's profile is in `ml`, then multiple the generated volume by `30`.

Breast feeding: Generate `min` to `max` number of feeding events per day at random time. For each event, add an event for left and right breasts. Let each breast event last for `min` to `max` *seconds*. Ensure that the various events do not overlap.

Sleep: Generate `min` to `max` number of sleep events per day at random time. Each event lasts `min` to `max` *minutes*. Ensure that the various events do not overlap.
