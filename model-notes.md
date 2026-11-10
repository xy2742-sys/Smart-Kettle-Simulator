# Smart Kettle Simulator — Model Notes

## What it models
A simplified electric kettle that heats water to a user-selected target temperature, then maintains that temperature.

## States
- **Idle:** Waiting for the user to start heating.
- **Heating:** Current temperature rises toward the selected target.
- **Keeping Warm:** The target is reached, or the user pauses heating; the kettle maintains the current temperature.

## Inputs and transitions
- Choose **50°C, 80°C, 90°C, or 100°C**: updates the target temperature while idle.
- Click **Start Heating**: moves from Idle to Heating, or directly to Keeping Warm if the water is already at or above the target.
- Temperature reaches the target: moves from Heating to Keeping Warm.
- Click **Pause & Keep Warm** during heating: stops the temperature rise and maintains the current temperature.
- Click **Cancel**: stops the simulation and returns to Idle.

## State variables
`current` tracks current water temperature, `target` stores the selected temperature, `warmTarget` stores the temperature currently being maintained, and `mode` stores the current state. A timer advances the simulation and the interface redraws from those values.

## Simplifications
The animation is accelerated. The water level stays visually fixed; only the temperature readout and progress bar change, so the animation does not imply that the amount of water is changing. Keeping Warm is represented by a small temperature dip followed by reheating, rather than a detailed thermostat or energy model.
