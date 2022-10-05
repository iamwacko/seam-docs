# Creating Intercom CRUD Endpoints

## Overview
Intercom CRUD endpoints Seam to list intercoms owned by an Intercom Owner and trigger the intercom to open a door.

### Listing Intercoms
After an Intercom Owner logs in, Seam lists all the intercoms they own and allows them to enable delivery on them. Your Intercom system should return a JSON list of intercoms.

### Getting an Intercom
Seam may request intercom information to display information about the intercom to the connecting user.

### Unlocking an Intercom Door
Seam unlocks doors to let in delivery people. If a door is disconnected or you're unable to unlock the door, return HTTP status code `500` with some details.

### Other Intercom Features
You may want to include additional features for your intercom, such as configuring settings that are useful for delivery or apartment management. If you add additional endpoints, you should keep a similar URL format `/intercoms/<INTERCOM_ID>/<SOME_PROPERTY_OR_FUNCTION>`
