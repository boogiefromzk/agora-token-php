# agora-token-php
Agora token generation library for PHP

As Agora support declined my feature request to do that, had to make Agora Tools for PHP repository folder available as a package, installable with Composer.

https://github.com/AgoraIO/Tools/tree/master/DynamicKey/AgoraDynamicKey/php/src

## License

ISC license is not confirmed, but inherited from agora-chat npm package:

https://www.npmjs.com/package/agora-chat

## Usage

Install the package.

```
composer require boogiefromzk/agora-token
```

Create the app token for using REST API to register users.

```
use BoogieFromZk\AgoraToken\ChatTokenBuilder2;

$appID = ... // App ID from Agora client area.
$appCertificate = ... // App Certificate from Agora client area.
$expiresInSeconds = ... // For how many seconds this token is kept valid.

$appToken = ChatTokenBuilder2::buildAppToken($appID, $appCertificate, $expiresInSeconds);
```

Then use it for authentication in Agora Chat REST API and register a user.

https://docs.agora.io/en/agora-chat/restful-api/user-system-registration

You will use some field as username when registering a user, save it in a user.

Now you can create a token for this user:

```
use BoogieFromZk\AgoraToken\ChatTokenBuilder2;

$appID = ... // App ID from Agora client area.
$appCertificate = ... // App Certificate from Agora client area.
$expiresInSeconds = ... // For how many seconds this token is kept valid.
$agoraUsername = ... // Username used for user registration above.

$token = ChatTokenBuilder2::buildUserToken($appID, $appCertificate, $agoraUsername, $expiresInSeconds);
```

More examples you can find in samples folder of Agora Tools project:

https://github.com/AgoraIO/Tools/tree/master/DynamicKey/AgoraDynamicKey/php/sample

In order to set and retrieve user's presence in Agora Chat please ensure that the feature is enabled from your Agora Chat Console. In order to enable it, from your Agora Chat Console menu, click on Features -> Overview -> Under "Message Feature Configuration" look for "Others" and ensure that Presence is set to enabled.

## Update files script

This script is for internal use, - it updates files in /src folder.

```
rm -rf ./src
svn export https://github.com/AgoraIO/Tools/trunk/DynamicKey/AgoraDynamicKey/php/src
cd ./src
sed -i 's/<?php/<?php\n\nnamespace BoogieFromZk\\AgoraToken;/' *
```

## Useful links
* Agora Use cases https://github.com/AgoraIO-usecase
* Agora examples https://gist.github.com/digitallysavvy

* Broadcasting RTC demo https://github.com/digitallysavvy/agora-web-broadcast-demo
* Subscribing RTC channels https://github.com/AgoraIO/API-Examples-Web/blob/main/Demo/joinMutlipleChannel/joinMultipleChannel.js
* RTC event descriptions https://gist.github.com/digitallysavvy/4ef54c791fe88c668cfe3420d7f6558f

* Agora RTM tokens https://docs.agora.io/en/signaling/develop/authentication-workflow
* RTM example https://github.com/AgoraIO/RTM/blob/master/Agora-RTM-Tutorial-Web/src/rtm-client.js

* Agora Chat REST API https://docs.agora.io/en/agora-chat/restful-api/user-system-registration
* Agora Chat Presence https://docs.agora.io/en/agora-chat/restful-api/presence#path-parameter
https://docs.agora.io/en/agora-chat/restful-api/presence#status-codes
* Agora Chat subscription to events example https://github.com/AgoraIO-Usecase/AgoraChat-web/blob/main/src/utils/WebIMListen.js
* Agora Chat send message example https://docs.agora.io/en/agora-chat/client-api/messages/send-receive-messages#send-a-customized-message
