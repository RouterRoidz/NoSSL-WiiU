# NoSSL-WiiU
A guide on how to safely use NoSSL on Wii U

## Part 1: Proxy Configuration

1: Download Fiddler Classic from https://www.telerik.com/download/fiddler/fiddler4

2: Open Fiddler and make sure the settings are set like this:

![Screenshot_1](https://user-images.githubusercontent.com/54253840/229333924-a1a20d3c-a7da-4955-884d-544473105b03.png)
![Screenshot_2](https://user-images.githubusercontent.com/54253840/229333928-f9bde7b2-c602-4a5d-9514-18b4521bde5b.png)

If Fiddler prompts you to install a certificate, install it, as not doing so may not make this work.

3: [Download this FiddlerScript](https://drive.google.com/file/d/1Owood0g3mphR4jAl6NyRja90lE9l14JH/view?usp=sharing), and replace the already existing one located in `C:\Users\[YourName]\Documents\Fiddler2\Scripts`, with `[YourName]` being the name of your user account.

4: [Go to this site](https://certs.larsenv.xyz/) to download the needed certificates. You will need `Wii U Common Prod 1` and `Wii U Account Prod 1`

5: Click on the downloaded certificates to import them, and check the `Mark this key as exportable` option for both. Password for both certificates is `alpine`

It's recommended that you store the certificates in the `Personal` store so it'll be easy to find them later
![Screenshot_3](https://user-images.githubusercontent.com/54253840/229334260-1abb1b3f-1e04-4fe4-8098-8a5fbbbb86b8.png)

6: Once both certificates are installed, create a folder on the root of your computer's C: drive, labeled `WIIU`

7: Press Windows Key + R and type in `certmgr.msc` to open the certificate manager. Navigate to `Personal > Certificates`, and look for the Wii U certificates you installed.

![Screenshot_4](https://user-images.githubusercontent.com/54253840/229334356-1e4650f5-4eef-4c4a-944c-228f6f55b7a9.png)

8: Right click on `Wii U Account Prod 1`, go to `All Tasks` and export it. Exporting the private key is not required.

Make sure to export it as a `Base-64 encoded X.509 (CER)` certificate. For the file name, name it `account.cer` and place it in `C:\WIIU`

Repeat this process for the `Wii U Common Prod 1` certificate. Name it `common.cer` and place it in `C:\WIIU`

Your `WIIU` folder should look like this now


![Screenshot_5](https://user-images.githubusercontent.com/54253840/229334496-59ee4a7e-03f3-407f-aa01-d93145d70ff1.png)


## Part 2: Wii U Configuration

1: Download the [NoSSL patcher from here](https://cdn.discordapp.com/attachments/895494927033729044/906498563096313856/Wii_U_NoSSL_Patcher.zip)

2: Open System Settings on your Wii U and go to the Internet Settings page for your Access Point. Scroll to the far right until you see `Proxy Settings`

3: Tap it, set the option to Use it and press OK on the popup that appears.

4: For the proxy server, use your computer's IP address. For the port, use the one in Fiddler (Should default to 8888). Make sure `Basic Authentication` is disabled.

5: Save the settings and perform a connection test. If `conntest.nintendowifi.net` appears on the proxy, it means you set up everything properly. The test should be successful.

6: Once you're on the Wii U Menu, you may notice you aren't able to access online services, this is why the NoSSL patcher is required.

Open the Homebrew Launcher, and launch the NoSSL patcher app that you installed. It should return to the Homebrew launcher after a few seconds.

7: If everything went well, HTTPS traffic should appear on Fiddler! Congratulations, you did it correctly.


## A few things to know.

For reasons currently unknown, NoSSL patcher does NOT work with Aroma CFW. Please use Tiramisu for this guide.
