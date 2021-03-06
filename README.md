# device-type.myautomatic

Author:             Yves Racine

linkedIn profile:   ca.linkedin.com/pub/yves-racine-m-sc-a/0/406/4b/

Date:               2015-08-08


**************************************************************************************************

/*********************************************************************************************

please take note of the following statement:**

**http://thingsthataresmart.wiki/index.php?title=My_Automatic_Device#Notes_to_MyAutomatic_Device_Users_-_Contribution_is_now_require**

/*********************************************************************************************

You can now download the code at 

<b>
http://www.maisonsecomatiq.com/#!store/tc3yr 
</b>

P.S. Technical support packages are also available.

Setup time: About 10-15 minutes (with real time processing) depending on your ST skills.

=====================
PREREQUISITES
=====================

- Basic information about your car entered in the Automatic app or at the Automatic portal
    (ex.  model, submodel, color, etc)
- Your Automatic connected vehicle fully operational
- Your Automatic credentials (username/password)
- Developer access to SmartThings (http://graph.api.smartthings.com/)
- Location set for your ST account 

Under the ST mobile app, click on the 3-horizontal lines- "hamburger"- menu in the upper right corner, and then the "gear'" icon to review your location review your location and save it.

- Determine your shard, please consult this thread:

https://community.smartthings.com/t/faq-how-to-find-out-what-shard-cloud-slice-ide-url-your-account-location-is-on/53923

Or the SmartThings documentation here:

http://docs.smartthings.com/en/latest/publishing/index.html#ensure-proper-location


If you are on a different shard, you need to change the links below for your right shard. 
As an example, in North America,

replace https://graph.api.smartthings.com/ide/devices by https://graph-na02-useast1.api.smartthings.com


=====================
INSTALLATION STEPS
=====================


/**************************************************************************************************/

<b>1) Create a new device handler (My Automatic Device) for your device(s)</b>
/**************************************************************************************************/

a) Go to https://graph.api.smartthings.com/ide/devices

b) Hit the "+New Device Handler" at the top right corner

c) Hit the "From Code" tab on the left corner

d) Copy and paste the code of the device type from the source file

After you purchase the code at my store, it is sent to your paypal verified email address by the sellfy e-commerce solution

e) Hit the create button at the bottom

f) Hit the "publish/for me" button at the top right corner (in the code window)

/**************************************************************************************************/

<b>2) Create a new smartapp (MyAutomaticServiceMgr)</b>
/**************************************************************************************************/

a) Go to https://graph.api.smartthings.com/ide/apps

b) Hit the "+New SmartApp" at the top right corner

c) Hit the "From Code" tab on the left corner

d) Copy and paste the code from MyAutomaticServiceMgr from the source file

After you purchase the code at my store, it is sent to your paypal verified email address by the sellfy e-commerce solution

e) Hit the create button at the bottom

f) <b>Make sure that enable OAuth in Smartapp settings is active</b> 

* Goto app settings (top right corner, click on it)
* Click on Oauth (middle of the page), and enable OAuth in Smart app
* Hit "Update" at the bottom

g) Go back to the code window, and hit the "publish/for me" button at the top right corner 

h) Keep the smartapp open in your IDE for the next step

/**************************************************************************************************/

<b>3) Create/login to your Automatic Developer account</b>
/**************************************************************************************************/

a) Open a new browser tab, and go to http://developer.automatic.com and create your developer account if needed

b) Go to https://developer.automatic.com/my-apps

c) Create a new app and name it "SmartThings"

d) Copy and paste your Automatic client id to the MyAutomaticServiceMgr smartapp at the bottom of the file where "insert Automatic Public Key here!" is indicated

e) Copy and paste your Automatic secret id to the MyAutomaticServiceMgr smartapp at the bottom of the file where "insert Automatic private Key here!" is indicated

Examples of keys, not valid at Automatic:

def getSmartThingsClientId() { "kjPlS3AAQtaUGlmB30IU9g" }

def getSmartThingsPrivateKey() { "6Qg0niXeQDSk-dkfU475og" }

f) Using the ST IDE, save and Publish the MyAutomaticServiceMgr smartapp with your credentials.


/**************************************************************************************************/

<b>4) Activate live logging for more tracing</b> 
/**************************************************************************************************/


Go to 

https://graph.api.smartthings.com/ide/logs

Note: In the next step, as Automatic does not presently support wildcard URL redirection to many ST users, you'd need to copy and paste the redirect URL generated by the smartapp at the Automatic portal.


/**************************************************************************************************/

<b>5) Under the ST app, execute MyAutomaticServiceMgr</b>
/**************************************************************************************************/


<b>a) Under the ST app, click on the Smartapps link in the upper section of the following Marketspace screen (last icon at the bottom), and then MyApps (last item in the list).</b>

b) The smartapp will ask you to authenticate on the Automatic portal (by pressing Next on the first page)

c) Press on MyAutomatic in the middle of the login page

d) The Automatic login page will appear with the following error message:

<i>Error: invalid request</i>

e) In the IDE, under https://graph.api.smartthings.com/ide/logs or under the device's list of events, you should see
the following trace:

<i>buildRedirectUrl,redirectURL=https://graph.api.smartthings.com/api/token/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/smartapps/installations/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/swapToken</i>
 
f) Copy and paste the redirect URL to the Automatic Developer portal under OAuth Redirect URL 

g) Save the URL redirect value at the Automatic Developer Portal

h) Press back on your device to re-login by pressing again on MyAutomatic in the middle of the page 

i) The Automatic login page should re-appear without any error message, enter your Automatic credentials

j) After being authenticated and pressing 'done' and 'next', the smartapp will show you the list of device(s) under your Automatic Account

If you get a blank screen after pressing 'Next or you get the following error: " Error - bad state. Unable to complete page configuration", you'd need to enable oAuth as specified in step 2f) above.

k) You may then select the Automatic device(s) to be exposed to SmartThings.

After pressing 'Done' on the last page, the smartapp will instantiate the MyAutomatic device object under 

https://graph.api.smartthings.com/device/list


/**************************************************************************************************/

<b>7) Under the SmartThings app (on your tablet or smartphone), you should then
see the new Automatic Object(s) under the 'myHome/Things' shortcut on the dashboard</b>

/**************************************************************************************************/

Click on it  and press refresh several times to populate its fields


/**************************************************************************************************/

<b>8) (optional) After instantiation of MyAutomatic object, you can edit its preferences and set your home
address for presence detection purposes</b>

/**************************************************************************************************/

Edit the preferences of MyAutomatic device(s) to set your home address or enable more tracing

Go to https://graph.api.smartthings.com/device/list
- Click on the My Automatic object in the list
- Edit the preferences by clicking on 'edit' (middle of the page) 
- Set the homeAddress parameter to your zipcode or street name (minimum information for presence detection) 
- Set the trace input parameter to true (for debugging purposes only)
- Edit the localFuelCostPerVolUnit parameter to reflect the local fuel cost per gallon/liter
- Save the changes by clicking 'Save' at the bottom.

 You only need to edit the above parameters

 P.S. Don't enter any values the vehicleId or for the appKey as the values are only
    used for the PIN authentication method.  If you do it, you may
    experience authentication issues when used with MyAutomaticServiceMgr smartapp.
    
/**************************************************************************************************/

<b>9) <i>NEW:</i> To enable near real-time automatic events processing in SmartThings</b>

/**************************************************************************************************/

a) At the Automatic Developer portal, copy the OAuth Redirect URL field entered in step 5f)

The field's value should be similar to:

<i>https://graph.api.smartthings.com/api/token/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/smartapps/installations/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/swapToken</i> 
 
b) Paste the redirect URL to the Automatic Developer portal under Webhook URL field

<b>c) Substitute "swapToken" by "procEvent" in the field (at the end)</b>

The field value should now look like:

<i>https://graph.api.smartthings.com/api/token/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/smartapps/installations/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/procEvent</i> 

d) Make sure that the Event Delivery Preference field is set to "WEBHOOK"

e) Save the URL value at the Automatic Developer Portal



/**************************************************************************************************/

<b>10) (optional) Install some of my SmartApp(s)</b>
/**************************************************************************************************/

See Under 

https://github.com/yracine/device-type.myautomatic/tree/master/smartapps

<b>a) MonitorAutomaticCar</b>

<b>Typical Use Case: Parents may want to closely monitor their kids' car driving abilities.</b>

The smartapp can detect any Speeding, Hard Acceleration, Hard Brake events after a trip has been completed and alerts parents of bad driving behaviors.

Parents may want to set a minimum Speeding Score or Events Score and if the kids' scores go below these thresholds, the parents will be notified ASAP.

The monitoring could be even more tight during the wet/snow season. Based on weatherStation, it can automatically switch to a monitoring cycle interval in minutes instead of hours when it's raining or snowing outside.....

See the virtual weather station at

https://github.com/yracine/device-type.weatherstation


<b>b) automaticReport</b>

The smartapp allows a ST user to generate daily reports on Automatic Connected vehicle's events such as Hard Acceleration,Hard Brake and Speeding.

<b>c) automaticCarHA</b>

The smartapp allows a ST user to create their own home automation scenarios based on the following list of real-time Automatic events.
It can turn on/off/flash some switch(es) and/or execute a routine.

The list of RT Automatic events are:

- 'ignition:on',
- 'ignition:off',
- 'trip:finished',
- 'notification:speeding',
- 'notification:hard_brake',
- 'notification:hard_accel',
- 'region:changed',
- 'mil:on',  (check engine light On)
- 'mil:off', (check engine light Off)
- 'hmi:interaction',
- 'location:updated',


