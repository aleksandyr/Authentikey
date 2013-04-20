Authentikey
=======

Google Two-Step Authenticator for Pebble

This is very much a WIP.  Why?

-There's no way to enter your secret phrase without recompiling the application

-...and the Pebble only reports local time, not GMT, so you have to enter an offset in the source

-...which means you have to download the source, make changes to src/twostep.c, and recompile for a .pbw specific to your account

-...and if you cross time zones or there's a DST change you'll need to rebuild the app again

-I don't have a base32-to-base64 conversion function yet, so you'll need to do that yourself

-I may or may not be a shady character intent on destroying your rare and valuable smart watch

-It works for me but might not for you

To use:
-check out from the github below & follow directions on the SDK site to build an existing application

-get your base32 encoded secret:

  - go to your two step setup page

  - choose to set up an iPhone application

  - click the link for "can't scan QR code"

  - cut the 16-character key

  - DO NOT CLOSE THE GOOGLE TWO FACTOR WINDOW (You need the enter the generated key and click verify and save)

  - Convert the key from base32 to HEX somehow (I used http://tomeko.net/online_tools/base32.php?lang=en)

  - take the value and put it bytewise into sha1_key, ex. expand AABBCC into 0xaa, 0xbb, 0xcc, ... 

-edit src/twostep.c and modify the defines under "CONFIGURE THIS"

-build, install

-the app ends up in the main menu.  It will update the key every 30 seconds

-test the key in the window you left open


Thanks to WhyIsThisOpen for posting his Unix Time source necessary for deriving seconds since epoch and time zone correction (without working mktime()).  Uses the public domain sha1.c from liboauth.
//pokey9000

Thanks to pokey9000 For providing the skeleton code I've just improved the Aesthetics.