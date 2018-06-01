###  Working with Chrome Group Policies

 Group Policies are designed to manage Chrome settings from central location and make it easier to deploy and use this browser in corporate networks. 

 There are two types of group policy templates for Windows OS provided by Google: 
 * ADM and ADMX (the latter is supported in the OS since Windows Vista / 2008 and above).
 * ChromeOS/HTML based templates

 
 ### Downloading

 Download and unpack an archive with ADM/ADMX templates of Group Policies for Google Chrome `http://dl.google.com/dl/edgedl/chrome/policy/policy_templates.zip` the file size is about 15 MB [right now]).


### Installation


**Quick explanation:**

* Download [latest Google Chrome Group Policy templates from Google](https://dl.google.com/dl/edgedl/chrome/policy/policy_templates.zip).
* Extract the .zip file
* Copy policy_templates\windows\admx\chrome.admx to \\your.domain\SYSVOL\your.domain\Policies\PolicyDefinitions
* Copy policy_templates\windows\admx\en-US\chrome.adml to \\your.domain\SYSVOL\your.domain\Policies\PolicyDefinitions\en-US
en-US may be different depending on your locale.
* Open Group Policy Management and Create a new Group Policy Object. Google Chrome options will be located under Computer Configuration > Policies > Administrative Templates


**Long explanation:**

Copy the files of an administrative template to the directory where they are to be stored. If you want group policy templates to be localized, don’t forget to copy the corresponding template file.

**Note**: Local administrative GPO templates are stored in `C:\Windows\PolicyDefinitions`, but if you are going to use policy templates for Chrome in the Active Directory domain environment, you can save them to the folder of a certain policy (not the best option) or to PolicyDefinitions directory in SYSVOL on the domain controller.


## Example

Suppose, we are going to use the ADMX format of the GPO template and centralized domain storage of policies. Copy chrome.admx file and localization directories to `\\chefkoch.loc\SYSVOL\chefkoch.loc\Policies\PolicyDefinitions`.

<p align="center"> 
<img src="https://raw.githubusercontent.com/CHEF-KOCH/Chromium-hardening/master/Chrome%20Policy/1.jpg">
</p>


Open the Group Policy Management Console (gpmc.msc) and edit any existing policy (or create a new one). Make sure that a new Google folder containing two subsections: Google Chrome and Google Chrome – Default Settings (users can override) appeared both in User and Computer sections of Policies -> Administrative Templates.

<p align="center"> 
<img src="https://raw.githubusercontent.com/CHEF-KOCH/Chromium-hardening/master/Chrome%20Policy/2.jpg">
</p>


If you are not using the centralized GPO storage, you can add the GPO template for Google Chrome manually. To do it, right-click Administrative Templates and select Add/Remove Templates. In the next window specify the path to chrome.adm file. It is better to specify the path in the UNC format, e. g., like this: \\chefkoch.loc\SYSVOL\chefkoch.loc\Policies\{60553A6F-2549-4C9E-B522-D3CF668E56B4}\Adm\chrome.adm

<p align="center"> 
<img src="https://raw.githubusercontent.com/CHEF-KOCH/Chromium-hardening/master/Chrome%20Policy/3.jpg">
</p>


So, we have copied GPO templates for Google Chrome browser. As we mentioned before, the new GPO section contains two subsections: Google Chrome and Google Chrome – Default Settings (users can override). The difference between them is that the settings of the latter section of policies can be changed by users in the browser settings on their computers. The settings of the first section are fixed and even the local administrator won’t be able to change them in the browser.

These administrative templates contain about 269+ of different manageable Google Chrome settings. You can explore them yourself and configure the browser settings that are needed in your environment.

<p align="center"> 
<img src="https://raw.githubusercontent.com/CHEF-KOCH/Chromium-hardening/master/Chrome%20Policy/4.jpg">
</p>

It doesn’t make any sense to consider all of them, we’ll only demonstrate basic Chrome settings that are often to be configured in the AD domain environment.


### Real World GPO examples

Among the useful Chrome settings that you should configure first, you can pay attention to the following policies (note that the **${local_app_data}** directory corresponds to the folder **%username%\AppData\Local**, and **${roaming_app_data}** – to **\%username%\AppData\Roaming**.

* **Set disk cache directory** – path to the Chrome disk cache (as a rule it is  “${local_app_data}\Google\Chrome\User Data”
* **Set disk cache size** – disk cache size (in bytes)
* **Set Google Chrome Frame user data directory** – **Chrome directory with user settings** “${local_app_data}\Google\Chrome\User Data”
Managed Bookmarks
* **Disable Chrome auto-update: Allow Installation**: Disable, Update Policy Override: Enable and in the Policy field specify Updates Disable
* Add certain sites to trusted sites **list – Policies HTTP Authentication -> Authentication server whitelist**


### Disallow Deleting Chrome History, Settings

Policies > Administrative Templates > Google > Google Chrome > Block access to a list of URLs

To block deleting of history, add these URLs:

* [chrome://settings/clearBrowserData](chrome://settings/clearBrowserData)
* [chrome://settings/clearBrowserData-frame](chrome://settings/clearBrowserData-frame)

To block viewing of history, add this URL:

* [chrome://history](chrome://history)

To block accessing of the Chrome settings, add this URL:

* [chrome://settings](chrome://settings)

To block access of the Chrome extensions, add this URL:

* [chrome://extensions](chrome://extensions)



#### Can I add a ad-blocking filter list subscriptions by policy?

Replace the extension UUID (in this example _gighmmpiobklfepjocnamgkkbiglidom_) with your ad-blocking UUID.

```bash
//Easy privacy List[HKLM\Software\Policies\Google\Chrome\3rdparty\extensions\gighmmpiobklfepjocnamgkkbiglidom\policy\additional_subscriptions]
"1" = "https://easylist-downloads.adblockplus.org/easyprivacy.txt"
```




#### Default Proxy Server and Home Page

Let’s configure a proxy server: we are interested in the following policy section Google Chrome -> Proxy Server

* Proxy server address: ProxyServer – 192.168.123.123:3128
* An exception list for proxy: ProxyBypassList – http://www.chefkoch.local,192.168.*, *.corp.chefkoch.local
Locate a home page: Home page -> HomepageLocation and set it to eg. – http://chefkoch.com

<p align="center"> 
<img src="https://raw.githubusercontent.com/CHEF-KOCH/Chromium-hardening/master/Chrome%20Policy/5.jpg">
</p>

Change the location of the download folder:

* Set **download directory** for example: `c:\temp\Downloads`

It remains to link the policy to the desired container (OU) of Active Directory. Apply the group policy to a client by running the command: `gpupdate /force`


Run the browser on the client and make sure that the GPO settings have been applied to its settings (in this screenshot, a user can’t change the values that were set by the administrator).

<p align="center"> 
<img src="https://raw.githubusercontent.com/CHEF-KOCH/Chromium-hardening/master/Chrome%20Policy/6.jpg">
</p>

To display all settings, set by the group policies directly in the Chrome, **go to the address Chrome://policy**.

<p align="center"> 
<img src="https://raw.githubusercontent.com/CHEF-KOCH/Chromium-hardening/master/Chrome%20Policy/7.jpg">
</p>

In the event that you prevented users from changing these Chrome settings, a message will appear in the browser window: This setting is enforced by your administrator.


<p align="center"> 
<img src="https://raw.githubusercontent.com/CHEF-KOCH/Chromium-hardening/master/Chrome%20Policy/8.jpg">
</p>

**Tip:** Although for the modern versions of Mozilla Firefox there are no ready Administrative Templates, but you can manage the browser settings using special configuration files that were copied with the help of Group Policy Preferences: How to Manage Firefox Settings using Group Policy.


### Install Chrome extension through GPO

With the help of these administrative templates, you can install certain Extensions of Google Chrome for all domain users. To do this, you need to know the ID of the extension and the URL from which the extension is updated.

The Google Chrome Extension ID can be found in the extension parameters in chrome://extensions (developer mode must be enabled).

<p align="center"> 
<img src="https://raw.githubusercontent.com/CHEF-KOCH/Chromium-hardening/master/Chrome%20Policy/9.jpg">
</p>

By ID, you need to find the extension folder in the user profile  C:\Users\%Username%\AppData\Local\Google\Chrome\User Data\Default\Extensions\{id_here}.

In the extension folder find and open the manifest.json file and copy the value of the update_url. Most likely, you will see the following URL: `https://clients2.google.com/service/update2/crx`.

<p align="center"> 
<img src="https://raw.githubusercontent.com/CHEF-KOCH/Chromium-hardening/master/Chrome%20Policy/10.jpg">
</p>

Now, in the GPO editor console, go to the Computer Configuration -> Policies -> Administrative Templates -> Google -> Google Chrome -> Extensions. Enable the policy Configure the list of force-installed extensions.

<p align="center"> 
<img src="https://raw.githubusercontent.com/CHEF-KOCH/Chromium-hardening/master/Chrome%20Policy/11.jpg">
</p>


Click the Show button and add a line for each extension that you want to install. Use the following format:

`{extension_id_here};https://clients2.google.com/service/update2/crx`

After applying to the user’s computers, all specified Chrome extensions will be installed in silent mode without interaction with the user.

<p align="center"> 
<img src="https://raw.githubusercontent.com/CHEF-KOCH/Chromium-hardening/master/Chrome%20Policy/12.jpg">
</p>


### Set Chrome to your default Browser

```bash
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\Chromium]
@="Chromium"

[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\Chromium\Capabilities]
"ApplicationDescription"="Chromium ist ein Webbrowser, der Webseiten und Apps in Sekundenschnelle lädt und dabei äußerst stabil und nutzerfreundlich ist. Dank des integrierten Malware- und Phishing-Schutzes können Sie bedenkenlos im Internet surfen."
"ApplicationIcon"="C:\\chromium\\chrome.exe,0"
"ApplicationName"="Chromium"

[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\Chromium\Capabilities\FileAssociations]
".htm"="ChromeHTML"
".html"="ChromeHTML"
".pdf"="ChromeHTML"
".shtml"="ChromeHTML"
".svg"="ChromeHTML"
".xht"="ChromeHTML"
".xhtml"="ChromeHTML"
".webp"="ChromeHTML"

[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\Chromium\Capabilities\Startmenu]
"StartMenuInternet"="Chromium"

[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\Chromium\Capabilities\URLAssociations]
"ftp"="ChromeHTML"
"http"="ChromeHTML"
"https"="ChromeHTML"
"irc"="ChromeHTML"
"mailto"="ChromeHTML"
"mms"="ChromeHTML"
"news"="ChromeHTML"
"nntp"="ChromeHTML"
"sms"="ChromeHTML"
"smsto"="ChromeHTML"
"tel"="ChromeHTML"
"urn"="ChromeHTML"
"webcal"="ChromeHTML"

[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\Chromium\DefaultIcon]
@="C:\\chromium\\chrome.exe,0"

[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\Chromium\InstallInfo]
"ReinstallCommand"="\"C:\\chromium\\chrome.exe\" --make-default-browser"
"HideIconsCommand"="\"C:\\chromium\\chrome.exe\" --hide-icons"
"ShowIconsCommand"="\"C:\\chromium\\chrome.exe\" --show-icons"
"IconsVisible"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\Chromium\shell]

[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\Chromium\shell\open]

[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\Chromium\shell\open\command]
@="\"C:\\chromium\\chrome.exe\""

[HKEY_LOCAL_MACHINE\SOFTWARE\RegisteredApplications]
"Chromium"="Software\\Clients\\StartMenuInternet\\Chromium\\Capabilities"
```


### Resetting 

Simply modify or create a Shortcut to Google Chrome/chromium which points  to: `"C:\Program Files (x86)\Google\Chrome\Application\chrome.exe" --restore-last-session` 


**Reference**

* [Policy Templates](https://www.chromium.org/administrators/policy-templates)
* [Adding a default site to CHROME and IE via GPO - Microsoft](https://social.technet.microsoft.com/Forums/en-US/7f0832f1-4540-45f1-a48b-e8428b348ed2/adding-a-default-site-to-chrome-and-ie-via-gpo?forum=winserverGP)
* [Set device-level Chrome policies for PCs](https://support.google.com/chrome/a/answer/187202?hl=en)
* *[Set app and extension policies for Windows](https://support.google.com/chrome/a/answer/7532015?hl=en)