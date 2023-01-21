# TheHandyForUnity_APIv2

It's a SDK to add the ability to control TheHandy by HTTP request in a Unity project.

I based my work on https://github.com/defucilis/TheHandyUnity

You will need to install Text Mesh Pro to run UI Example

### What is TheHandy
TheHandy is male masturbator than can be controlled by remote command (HTTP or Bluetooth) : https://www.thehandy.com/

For blutooth, see : https://buttplug.io/

### HTTP requests
That Swagger show all HTTP request that can be send to TheHandy (API v2) : https://staging.handyfeeling.com/api/handy/v2/docs/#/

All request are in my SDK but maintenance. I think it's really a better idea to make firmware update update directly on TheHandy site :
https://www.handyfeeling.com/local-video

See also Handyfeeling Developer Documentation : https://sweettech.notion.site/Get-started-1704d1c1d205408999a3c005e0c06d8f

All commands are first send to https://www.handyfeeling.com/api/handy/v2/ then send to TheHandy.

### Upload file to the server
That Swagger that show how to upload/download script on handyfeeling server : https://staging.handyfeeling.com/api/handy/v2/docs/#/

I add both command in my 
