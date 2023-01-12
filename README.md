# **T11 - Database Model Handler**

## **Descripton**
This is a component that is part of the Dentistimo distributed system. More information about the whole system can be found [here](https://github.com/T-11-Dentistimo/T11---Project-documentation).

This component is connected to the Mongo database and it is the only component in this distributed system that will persist entries in it. It works in close collaboration with the [Booking validator](https://github.com/T-11-Dentistimo/T11-Booking-Validator), receiving bookings for dental appointments to be saved in the database, and the [Web application](https://github.com/T-11-Dentistimo/T11-Web-Application), publishing information about the dentist clinics. 


## **Responsibilities**

- Publish data about the dentist clinics, so that the web application can display their info on the website
- Persist new bookings in the database
    - Publish confirmation message if it was successful
    - Publish error message if it was unsuccessful

## **Data flow**

### **<ins>Input Data</ins>**

The **input data** of this component includes the bookings received by the booking validator and requests to send dentist clinic information to the web application. 

>Example Booking request
```
{
  "userid": "bob@gmail.com",
  "dentistid": 1,
  "issuance": 1602406766314,
  "date": "2020-12-14",
  "name": "Bob",
  "time": "13:00-13:30"
}

```
### **<ins>Output Data</ins>**

The **output data** of this component is the information about the dentist clinics, booking confirmations and potential error messages in case the booking could not be persisted in the database. 
>Example Booking confirmation
```
{
    "userid": "bob@gmail.com",
    "date": "2020-12-14",
    "name": "Bob",
    "time": "13:00-13:30",
    "sessionId": "JJo0J-xkqrRsqqGvU3lF3EJxWFhiAKv3",
    "dentistId": 1,

}
```

## **Tools**

>  Eclipse Mosquitto broker <br>[Download here](https://mosquitto.org/download/)

>NodeJS <br>[Download here](https://nodejs.org/en/download/)

>Javascript IDE<br> Some alternatives: [Visual Studio Code](https://visualstudio.microsoft.com/downloads/) , [WebStorm](https://www.jetbrains.com/webstorm/download/)

>MongoDB Atlas<br> [Sign up here](https://www.mongodb.com/cloud/atlas/register?utm_content=rlsapostreg&utm_source=google&utm_campaign=search_gs_pl_evergreen_atlas_general_retarget-brand-postreg_gic-null_emea-all_ps-all_desktop_eng_lead&utm_term=&utm_medium=cpc_paid_search&utm_ad=&utm_ad_campaign_id=14412646473&adgroup=131761130372&gclid=CjwKCAiAs8acBhA1EiwAgRFdw_MoFEx8Y7bvZ8bKQR8DbT6RHJv631vx70_2J4uu3SXaXUo16lQYNxoClNQQAvD_BwE)

### **Libraries**  
- [NPM](https://www.npmjs.com/)
- [MQTT.js](https://www.npmjs.com/package/mqtt#api)
- [Mongoose](https://mongoosejs.com/)





### **<ins>SetUp</ins>**

| Description | Command |
|-------|---|
| Clone this repository | <ins>Option 1.</ins><br> Download as a zip file<br> <ins>Option 2.</ins><br>`git clone git@git.chalmers.se:courses/dit355/dit356-2022/t-11/t11-database-model-handler.git`|
|Create a `.env` file in the root folder. Create a new environment variable called `MONGO_ATLAS_URI` inside it where you will store the Mongo Atlas cluster URI |`MONGO_ATLAS_URI`= < atlas-cluster-URI-here >|
| Open a terminal and navigate to the mosquitto root folder. On Windows the default path is: <br> `C:\Program Files\mosquitto` |  `mosquitto -c mosquitto.conf -v ` |
|Open the repo in a javascript IDE and open the terminal in the IDE.  | `npm install` |
|The component is ready to be launched|`npm run dev`|


## Error-Handling
The Mosquitto broker is normally automatically running in the background after you install it. A common error is therefore, when trying to run the `mosquitto -c mosquitto.conf -v ` command, that it will say that an instance of the broker is already running, and the process will terminate. To fix this (on Windows), got to services and stop the Mosquitto broker from there, and try the command again. 











