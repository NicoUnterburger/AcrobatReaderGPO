# AcrobatReaderGPO
## Deployment of Adobe Acrobat Reader DC with Standard Active Directory Group Policy

1. Gathering Installation Files
   ```
    Latest EXE-Installer:   https://get.adobe.com/de/reader/enterprise/
    Latest MSP Updates:     https://www.adobe.com/devnet-docs/acrobatetk/tools/ReleaseNotesDC/index.html
   ```
3. Extract EXE File with 7-Zip
4. Run an admin install of the Enterprise installer extracted MSI.

    ```msiexec /a "extractedDirectory\AcroRead.msi" TARGETDIR="\\contoso.de\NETLOGON\acroread\new"```

### NOW YOU HAVE AN VALID MSI INSTALL-FILE, WITHOUT ANY UPDATES SINCE 2015! 

4. Run an admin install with a patch option specifying the MSP on the Admin install you created in step 3.
   
    ```msiexec /a \\contoso.de\NETLOGON\acroread\new\AcroRead.msi /update AcroRdrDCUpd2200120142.msp```

NOW ADOBE INSTALLER WILL SLIPSTREAM THE MSP UPDATES TO THE MENTIONED MSI 
DEPLOY "\\contoso.de\NETLOGON\acroread\new\AcroRead.msi" in GPO 

## More Informations
https://community.spiceworks.com/how_to/37467-how-to-create-a-slipstreamed-adobe-acrobat-reader-msi-for-gpo-deployment
