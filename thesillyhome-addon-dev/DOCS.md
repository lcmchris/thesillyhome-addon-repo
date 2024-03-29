This is using the latest branch.

# Home Assistant Add-on: TheSillyHome add-on

Setting the right routines is hard, let thesillyhome help you!
ML simplified of Homeassistant.

## How to use

Step 1:
Define your sensors and lights. This currently requires the entity IDs to be listed:

- Set sensors
- Set lights

Step 2:
Define your DB. Currently either the default sqlite, mariadb and postgres is supported.

For Sqlite, just set the db_database to your sqlite db filename and db_type to `sqlite`. The other variables can be left blank.
For mariadb and postgres, set the db config to your connection urls.

To have this work well, 90 purge_keep_days is recommended or even better remove auto_purge: false.
If your Rasphberry Pi is not happy, please use an external db.
Checkout the recorder documentation https://www.home-assistant.io/integrations/recorder/ for setting this up.

- Set DB Url
- Set DB login and password

Step 3:

Run Data Extraction

Step 4:
Run Model Training

Enable Model predictions

- Routine predictions
- Dry run mode
- Live mode

Step 5:
Continuous teaching using Alexa
