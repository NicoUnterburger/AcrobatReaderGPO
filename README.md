# AcrobatReaderGPO
Deployment of Adobe Acrobat Reader DC 

1. Gathering Installation Files
    Latest EXE-Installer:   https://get.adobe.com/de/reader/enterprise/
    Latest MSP Updates:     https://www.adobe.com/devnet-docs/acrobatetk/tools/ReleaseNotesDC/index.html
2. Extract Exe File with 7zip
3. Run an admin install of the Enterprise installer extracted MSI. Give it a new path name for the end resulting patch version.
    =>  msiexec /a "extractedDirectory\AcroRead.msi" TARGETDIR="\\hugo\netlogon$\acroread\new"

NOW YOU HAVE AN VALID MSI INSTALL-FILE, BUT WITHOUT ANY UPDATES SINCE 2015! 

4. Run an admin install with a patch option specifying the MSP on the Admin install you created in step 3.
    =>  msiexec /a \\hugo\netlogon$\acroread\new\AcroRead.msi /update AcroRdrDCUpd2200120142.msp

NOW ADOBE INSTALLER WILL SLIPSTREAM THE MSP UPDATES TO THE MENTIONED MSI 
DEPLOY "\\hugo\netlogon$\acroread\new\AcroRead.msi" in GPO 

MORE: https://community.spiceworks.com/how_to/37467-how-to-create-a-slipstreamed-adobe-acrobat-reader-msi-for-gpo-deployment
        
