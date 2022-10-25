# agora-token-php
Agora token generation library for PHP

As Agora support declined my feature request to do that, had to make Agora Tools for PHP repository folder available as a package, installable with Composer.

https://github.com/AgoraIO/Tools/tree/master/DynamicKey/AgoraDynamicKey/php/src

ISC license is not confirmed, but inherited from agora-chat npm package:

https://www.npmjs.com/package/agora-chat

Update files script:
```
rm -rf ./src
svn export https://github.com/AgoraIO/Tools/trunk/DynamicKey/AgoraDynamicKey/php/src
cd ./src
sed -i 's/<?php/<?php\n\nnamespace BoogieFromZk\\AgoraToken;/' *
```
