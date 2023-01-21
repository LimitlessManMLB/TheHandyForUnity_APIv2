# TheHandyForUnity_APIv2

It's a SDK to control TheHandy by HTTP request in a Unity project
 by using API v2 of Handyfeeling. *(API Support will be at least through 2024)*

I based my work on https://github.com/defucilis/TheHandyUnity

## What Is TheHandy
TheHandy is a male masturbator than can be controlled by remote commands (HTTP or Bluetooth) : https://www.thehandy.com/

For blutooth, see : https://buttplug.io/

## HTTP Requests
That Swagger show all HTTP request that can be send to TheHandy (API v2) : https://staging.handyfeeling.com/api/handy/v2/docs/#/

All request are in my SDK but maintenance. I think it's really a better idea to make firmware update directly on TheHandy site :
https://www.handyfeeling.com/local-video

See also Handyfeeling Developer Documentation : https://sweettech.notion.site/Get-started-1704d1c1d205408999a3c005e0c06d8f

All commands are first send to https://www.handyfeeling.com/api/handy/v2/ then send to TheHandy.

If a set of data are send to / receive from TheHandy, I made an enum or a struct for it.

### Modes And Commands

API v2 give 5 modes with there specific command and some general command.

HAMP, HDSP and HSSP mode must be set prior to send their commands. Otherwise, an error will by throw by the server.

There is the listing as given in my class HandyHTTPConnection.cs :

- Handy Alternate Motion Protocol (HAMP) operations :
    -   HAMP_Start
    -   HAMP_Stop
    -   HAMP_GetVelocity
    -   HAMP_SetVelocity
    -   HAMP_GetState

- Handy Direct Streaming Protocol (HDSP) operations :
    -   HDSP_Set_xava (absolute position (xa), and the absolute velocity (va))
    -   HDSP_Set_xpva (percent position (xp), and the absolute velocity (va))
    -   HDSP_Set_xpvp (percent position (xp), and the percent velocity (vp))
    -   HDSP_Set_xat  (absolute position (xa), and duration (t))
    -   HDSP_Set_xpt  (percent position (xp), and duration (t))

- Handy Synced Stream Protocol (HSSP) operations : It's with that mode that you can play script (See **HSSP, All the details** below)
    -   HSSP_Play
    -   HSSP_Stop
    -   HSSP_Setup
    -   HSSP_GetLoop
    -   HSSP_SetLoop
    -   HSSP_GetState

- Handy Buffered Streaming Protocal (HBSP) (Not yet implemented - 2023-01)

- Handy Simple Timing Protocol (HSTP) : Available in all mode, it's mainly for HSSP uses. (See **HSSP, All the details** below)
    -   HSTP_GetDeviceTime
    -   HSTP_GetOffset
    -   HSTP_SetOffset
    -   HSTP_GetRtd
    -   HSTP_GetSync (Could be just Sync)

- General commands
    -   GetServerTime
    -   GetMode
    -   SetMode
    -   GetConnected (This is the fastest way to check device connectivity)
    -   GetInfos
    -   GetSettings (2022-01 :Swagger said include offset and velocity but TheHandy return only slideMin and slideMax)
    -   GetStatus
    -   GetSlide (Min/Max stroke)
    -   SetSlide (Min/Max stroke)

### HSSP, All the details

To use the handy on HSSP mode, some command must be send to work properly:
1.   Send HSTP_GetSync to made TheDandy synchronize his clock with the server. (Optional)
2.   Upload a File to the server and get the returned url.
3.   Send HSSP_Setup with this url to make TheHandy download the script.
4.   Send HSTP_GetDeviceTime to get the deviceTime.
5.   Send HSSP_Play with the deviceTime to make TheHandy play downloaded script.

## Upload File To The Server
That Swagger that show how to upload/download script on handyfeeling server : https://scripts01.handyfeeling.com/api/script/hosting/v0/docs/#/

File are uploaded on a different address : https://scripts01.handyfeeling.com/api/script/hosting/v0/

- Commands
    -   UploadScript
    -   DownloadScript

## Install This SDK in Your Unity Project
That realy simple, install the TheHandyForUnity_APIv2.unitypackage on your project.

There all you realy need :
- SimpleJSON (Exept AsLong, it's a copy from https://github.com/defucilis/TheHandyUnity)
- HandyConnectionAPIv2 : (I keeped some basic function but almost all are new or modified)
- StructsAndEnums (Exept LogMode, all is new)

To run the UI Example You will need to install Text Mesh Pro.
