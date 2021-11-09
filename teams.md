## Use Native Window Decorations

It's possible to add the title bar back in with a bit of fiddling. It relies on having the the node.js utility asar installed (e.g. npm install -g asar).
1. Find the Teams app.asar file, for me on Ubuntu it is at /usr/share/teams/resources
2. Unpack the app.asar file : `sudo mkdir app && sudo asar extract app.asar app`
3. Edit app/lib/appStart.js
4. Find the code like
const options = {
            webPreferences: webPreferences,
            show: false,
            frame: false,
            titleBarStyle: 'hiddenInset',
            minWidth: constants.windowMinimumSize.width,
            minHeight: constants.windowMinimumSize.height
        };
it's around line 550
5. Set the frame property to true and save the file
6. Rename the app.asar file to something else e.g. app.asar.bak


Unfortunately, this will need to be repeated every time the app is updated but until a proper fix is released it should help.
