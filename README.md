![Capture](https://github.com/samuelolteanu/esphome-midea-pid-power-control-via-ir-folowme/assets/85267083/10bc9cdf-92fc-46f6-b4f8-98cdeeccad76)
With this ESPHome ir tranmitter, it is possible to trick a Midea split air conditioner into lowering or increasing power consumption by periodically sending a certain room temp via "folowme" feature. This is taken care of by a pid controller that sends a range of temps for heating mode like this:
- max power: set temp - 5
- min power: set temp + 2.

Example: if the ac is set at 17, sent temp for max power will be 12 degrees. For minimum power (should be zero) 19 degrees will be sent. This does not work without a home assistant compatible power meter.

The way to use this feature is to enable folowme switch, set the pid (climate) controller to a certain W (will display degrees but it's watts) and wait for change. It takes around 10 minutes for change to occur, sometimes way more, depending of defrost status or other unknowns, example the appliance may have a different maximum power level depending on outside temp). Feel free to experiment with faster temp report interval, lower a output_averaging_samples and of course, alternative pid controls (kp ki kd).

Disclaimer: This may lower the ac efficiency.

Use case: matching photovoltaic power to have "free" heating with a home assistant automation.
