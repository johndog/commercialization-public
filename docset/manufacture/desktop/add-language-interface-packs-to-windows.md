---
author: Justinha
Description: Add Language Interface Packs to Windows
MS-HAID: 'p\_adk\_online.add\_language\_interface\_packs\_to\_windows'
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: Add Language Interface Packs to Windows
---

# Add Language Interface Packs to Windows


Language Interface Packs (LIPs) include Windows user interface text for a region. LIPs must be used with a valid parent language.

For example, the Catalan (ca-ES) LIP can be installed only if one of the following languages is already installed: English US (en-US), Great Britain (en-GB), Spanish (es-ES), or French (fr-FR).

To add a LIP to an offline Windows image, you must verify that the supported parent language pack is installed to the Windows image first.

For a list of the LIPs and their parent languages, see [Available Language Packs for Windows](available-language-packs-for-windows.md).

The version of the LIP must match the version of Windows. For example, you can't add a Windows 10 LIP to a Windows 8 image, or a Windows 8 LIP to a Windows 10 image.

For Windows 10, language packs and LIPs are also available to download from Windows Update. You can add additional languages by using the Control panel. This process requires internet access and access to Windows Update. IT Professionals and end-users can use Windows Update to add additional languages to their Windows installations.

Not all LIPs are currently available for Windows 10.

-   OEMs can view and download LIPs from the [Microsoft OEM site](http://go.microsoft.com/fwlink/?LinkId=131359).
-   System Builders can view and download LIPs from the [OEM Partner Center](http://go.microsoft.com/fwlink/?LinkId=131358)
-   IT Professionals can view and download LIPs from the [Local Language Program](http://go.microsoft.com/fwlink/?LinkId=262343).
-   Users can get language or LIPs from Windows Update. Click **Windows Control Panel** &gt; **Clock, Language, and Region** &gt; **Language** &gt; **Add Language**. Chose the language that you want to add and follow the instructions in the Control Panel to configure the language as the default.

## <span id="Install_LIPs"></span><span id="install_lips"></span><span id="INSTALL_LIPS"></span>Install LIPs


**To install a LIP using audit mode (used for manufacturing PCs)**

1.  Download the appropriate LIP (and if necessary, its base language), and save it to removable media.
2.  Boot the destination computer to audit mode. For example at the OOBE screen, press CTRL+SHIFT+F3. To learn more, see [Boot Windows to Audit Mode or OOBE](boot-windows-to-audit-mode-or-oobe.md).
3.  Insert the removable media and copy the LIP (and base language, if necessary) to the destination computer.
4.  If the base language isn't already installed, install it: Navigate to the .cab file and double-click it. Follow the instructions to complete the installation.
5.  Install the LIP: Navigate to the .cab file and double-click it. Follow the instructions to complete the installation.
6.  Exit audit mode and prepare the PC for image capture or deployment, for example:

    From a command line, run **sysprep /oobe /generalize**. To learn more, see [Sysprep (Generalize) a Windows installation](sysprep--generalize--a-windows-installation.md).

**To install a LIP to an offline Windows image**

1.  Download the appropriate LIP (and if necessary, its base language).
2.  Open a command prompt with elevated permissions.
3.  Mount the Windows image that you want to install the LIP to.

    ``` syntax
    md "C:\mount\windows"

    Dism /Mount-Image /ImageFile:C:\images\Win10\sources\install.wim
      /Index:1 /MountDir:"C:\mount\windows"
    ```

4.  If the base LP isn't in the image already, add it.

    ``` syntax
    Dism /Image:C:\mount\windows /Add-Package /PackagePath:C:\Languages\es-ES\lp.cab
    ```

5.  Add the LIP.

    ``` syntax
    Dism /Image:C:\mount\windows /Add-Package /PackagePath:C:\Languages\ca-ES\lp.cab
    ```

6.  If you're creating Windows Setup media or using a distribution share, recreate the lang.ini file.

    ``` syntax
    Dism /Image:C:\mount\windows /Gen-LangIni 
           /Distribution:C:\images\Win10\sources
    ```

    The lang.ini file in C:\\images\\Win10\\sources should look similar to the following:

    ``` syntax
    [Available UI Languages]
    ca-ES = 2
    es-ES = 3
     
    [Fallback Languages]
    es-ES = en-us
    ```

7.  Optional: Change the default language, locale, and other international settings to the local language.

    ``` syntax
    Dism /image:C:\mount\windows /set-allIntl:ca-es
    ```

    Optional: Review the default international settings.

    ``` syntax
    Dism /image:C:\mount\windows /get-intl
    ```

    For example, you should see output similar to the following:

    ``` syntax
    Reporting offline international settings.
     
    Default system UI language : es-ES
    System locale : ca-ES
    Default time zone : Romance Standard Time
    User locale for default user : ca-ES
    Location : Spain (GEOID = 217)
    Active keyboard(s) : 0403:0000040a
    Keyboard layered driver : PC/AT Enhanced Keyboard (101/102-Key)
     
    Installed language(s): ca-ES
      Type : Partially localized language, LIP type.
    Installed language(s): es-ES
      Type : Fully localized language.
     
    Reporting distribution languages.
     
    The default language in the distribution is:
    es-ES
    ```

8.  Unmount the image, committing the changes.

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount\windows /Commit
    ```

    Your Windows image is ready to be deployed.

## <span id="related_topics"></span>Related topics


[Add Language Packs to Windows](add-language-packs-to-windows.md)

[Available Language Packs for Windows](available-language-packs-for-windows.md)

[Language Pack Default Values](http://go.microsoft.com/fwlink/?LinkId=206622)

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_adk_online\p_adk_online%5D:%20Add%20Language%20Interface%20Packs%20to%20Windows%20%20RELEASE:%20%284/11/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



