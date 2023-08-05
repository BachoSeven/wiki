### The instructions

1. Install VSCodium and Copilot extension (you can download the vsix here https://marketplace.visualstudio.com/items?itemName=GitHub.copilot)
2. Edit `VSCODIUM_FOLDER/resources/app/product.json`. Find the `GitHub.copilot` and insert the following permission:

> ["inlineCompletions","inlineCompletionsNew","inlineCompletionsAdditions","textDocumentNotebook","interactive","terminalDataWriteEvent"]

3. Open a terminal and send a request to begin Github authorization

> curl https://github.com/login/device/code -X POST -d 'client_id=01ab8ac9400c4e429b23&scope=user:email'

4. You'll see `device_code` and `user_code` in the response
5. Go to https://github.com/login/device/ in any browser and enter the `user_code`
6. Return to the terminal and send this (replace `YOUR_DEVICE_CODE` with the `device_code` you got in the step 4):

> curl https://github.com/login/oauth/access_token -X POST -d 'client_id=01ab8ac9400c4e429b23&scope=user:email&device_code=YOUR_DEVICE_CODE&grant_type=urn:ietf:params:oauth:grant-type:device_code'

7. You'll see your `access_token` in the response (`gho_...`). Paste it in VSCodium when the Copilot extension requires authorization.
8. Enjoy your freedom!

### Possible paths for the `product.json`:

* `/opt/vscodium-bin/resources/app/product.json`
* `/usr/share/codium/resources/app/product.json`
* `/Applications/VSCodium.app/Contents/Resources/app/`
