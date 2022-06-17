# Welcome to thesillyhome addon
[![Open your Home Assistant instance and show the add add-on repository dialog with a specific repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/lcmchris/thesillyhome-addon-repo)

- This repository is an addo-on that tries to help apply ML to your homeassistance.
- This aims to act as a proof of concept that applying ML to homeautomation works and a future with J.A.R.V.I.S is closer than we thought.
- This is opensource but a wider vision is to apply this to all homeautomation platforms (think APIs and centralised AI models). This is the tenet of <a href="https://thesillyhome.com/about-us/#our-mission">The silly home</a>.


# Addon Setup
In this setup, we have a pip installable repo that hosts all the code https://github.com/lcmchris/thesillyhome-addon-repo. This is installed onto the addon container and is built onto the addon-image.
This addon uses the Appdaemon to control devices. This decision was made due to the simplicity of its implementation


# How this works
<h2> ML design </h2>

Terminology used :
actuators = Any entity's state you want to create a model and predict for. ie. living_room_light_1.state, living_room_light_2.state
sensors = Any entities that act as the triggers and conditions. ie. sensor.occupancy
devices = actuators + sensors

Intuition:
With a new device state change, predict if any other actuators need to change.
1 Model per actuator

1) Data extraction
2) Learning model
3) Appdaemon Execution


<h2> Data extraction </h2>
Homeassistant stores state data. This step extracts and parses this data into a ML trainable format (hot encoded of categorical values, constant status publish vs state changes etc..). 

The end output frame is munged to show for each state published for an actuator, the state of other sensors and actuators.

The data is strucutred in a csv and looks like this:
actuators, states, created, duplicate, senor1, sensor2, sensor3, sensor4...

<h2> Learning model </h2>
As a phase one, our focus will be to predict lights using motion sensors, light sensors, other lights, device location, weather as inputs.
Only sklearn Decision Tree model is used.

<h2> Appdaemon Execution </h2>
For ease of deployment, the decision was made to leverage Appdaemon in order to use the prediction models created in real time!
For each sensor change there is a request to predict the new states for actuators and performs them.


Add-on documentation: N/A



## Feature suggestions

<h3> Routine extraction? </h3>
There is an open thought that having these untrained, underperforming models (at this stage) to directly manage your home is a bad idea. A perhapes better one is to make it predict your required routines.

<h2> Model Performance dashboard? </h2>
Having a black box is probably not ideal for The silly home, adding some visibility on the models giving performance will help let you pick and choose the models to activate.

## Add-ons

This repository contains the following add-ons

### [Example add-on](./example)

![Supports amd64 Architecture][amd64-shield]
![Supports arm64 Architecture][arm64-shield]
![Supports armv7 Architecture][armv7-shield]


<!--

Notes to developers after forking or using the github template feature:
- While developing comment out the 'image' key from 'thesillyhome-addon/config.yaml' to make the supervisor build the addon
  - Remember to put this back when pushing up your changes.
- When you merge to the 'main' branch of your repository a new build will be triggered.
  - Make sure you adjust the 'version' key in 'thesillyhome-addon/config.yaml' when you do that.
  - Make sure you update 'thesillyhome-addon/CHANGELOG.md' when you do that.
  - The first time this runs you might need to adjust the image configuration on github container registry to make it public
- Adjust the 'image' key in 'thesillyhome-addon/config.yaml' so it points to your username instead of 'home-assistant'.
  - This is where the build images will be published to.
- Rename the example directory.
  - The 'slug' key in 'thesillyhome-addon/config.yaml' should match the directory name.
- Adjust all keys/url's that points to 'home-assistant' to now point to your user/fork.
- Share your repository on the forums https://community.home-assistant.io/c/projects/9
- Do awesome stuff!
 -->

[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[arm64-shield]: https://img.shields.io/badge/arm64-yes-green.svg
[armv7-shield]: https://img.shields.io/badge/armv7-yes-green.svg
