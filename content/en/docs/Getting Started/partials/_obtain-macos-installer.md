There are multiple ways to obtain the installer .app file for Mac OSX that we'll detail for you below:

1. If you have a pending upgrade to the next minor or patch version of Mac OS:
    - Within `Preferences -> Software Update -> Advanced`, make sure `Download new updates when available` is checked but `Install macOS updates` is not. While you're still within `Software Update`, click `Update Now` but do not install the next version (Restart) until after you've created the Anka VM or the Install .app under /Applications will be deleted.
    - You can also use the App Store to download the installer.
2. On Catalina, you can use `softwareupdate`: `sudo softwareupdate --fetch-full-installer --full-installer-version 10.15.6`
3. Have your local IT department provide a network volume or download links.
4. On any Mac OS version you can use the [installinstallmacos.py](https://github.com/munki/macadmin-scripts) script (requires python):

    > This method doesn't consistently work and can throw errors like `uses a deprecated pre-10.2 format`

    - Download and run the script:  
      ```shell
      curl --fail --silent -L -O https://raw.githubusercontent.com/munki/macadmin-scripts/main/installinstallmacos.py
      sudo chmod +x installinstallmacos.py
      sudo ./installinstallmacos.py --raw
      ```

    - The script downloads an image to the location of the .py script, so further steps are necessary to unpack the .app:
      ```shell
      mkdir -p /tmp/app
      hdiutil attach "<installinstallmacos.py image path>" -mountpoint /tmp/app
      cp -r "/tmp/app/Applications/Install Mac OS Catalina.app" /Applications/
      hdiutil detach /tmp/app -force
      rm -f "<installinstallmacos.py image path>"
      ```
3. Have your local IT department provide a network volume or download links.
