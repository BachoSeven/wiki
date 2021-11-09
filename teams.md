# Use Native Window Decorations

It's possible to have native window decorations (e.g. title bar, window borders, etc.) back, with a bit of fiddling.

You will need to have the node.js utility asar installed (e.g. `npm install -g asar` given you have `npm` on your system, or `sudo pacman -S asar` if you are on Arch).

## Instructions

1. Find the Teams `app.asar` file, on Ubuntu and Arch it's located at `/usr/share/teams/resources`
2. Unpack the `app.asar` file :
``` sh
sudo mkdir app && sudo asar extract app.asar app
```

### New Version (works for sure with 1.4.00.26453)
- Run this command as root:
``` sh
sed -i 's/frame:!1/frame:!0/g' app/main.bundle.js
```

### Old Version
1. If your version has the file `app/lib/appStart.js`, edit it as root and locate the following snippet
``` js
const options = {
            webPreferences: webPreferences,
            show: false,
            frame: false,
            titleBarStyle: 'hiddenInset',
            minWidth: constants.windowMinimumSize.width,
            minHeight: constants.windowMinimumSize.height
        };
```
(it should be around line 550)
2. Set the frame property to true and save the file

### Optional
If after doing the above you don't see window decorations next time you start Teams, try renaming the `app.asar` file to something else (e.g. `app.asar.bak`).

### Conclusion
Unfortunately, this will need to be repeated every time the app is updated but until a proper fix is released it should help.

#### Source
> view-source:https://web.archive.org/web/20211030224842/https://microsoftteams.uservoice.com/forums/555103-public/suggestions/39231850-native-window-borders-and-header-in-linux-app
#### Forum thread
> https://feedbackportal.microsoft.com/feedback/idea/2be896a4-4e3e-ec11-a81a-6045bd78d291
