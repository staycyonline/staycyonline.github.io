---
tags:
  - iOS
  - Lab
  - Pentest
  - Aresenal
  - Application
categories: Lab Setup, Arsenal
title: Setting up an iOS Application Pentest Lab Level 1
---


Setting up a home lab for iOS application dynamic testing has been a fascinating journey for me. This tutorial aims to document my Level 1 setup, focusing on dynamic testing with a physical iOS device. 

Let's dive in!

## Level 1 Setup
---
- **Burp Suite Pro**: Installed on either Windows or Linux to proxy app traffic.
- **iOS Device**: A Jailbroken iPhone with specific tweaks, which I'll discuss below.

## Motivation
---
I've always been eager to explore iOS Application Pentesting ever since I began my cybersecurity career. Interestingly, iOS Application Pentesting remains a less explored area compared to Android. I was curious to understand the reasons behind this and the challenges of setting up a testing lab for iOS applications.

## Ditching Emulators for a Physical iPhone
---
Initially, I explored using emulators for iOS testing but found them to be expensive or limited compared to Android emulators. While Xcode offers some form of iOS emulation, I didn't have access to a Mac.

Popular options like [Correlium](https://www.corellium.com/) and [Appetize.io](https://appetize.io/) were quite pricey. Realizing that a physical device was the only viable option, I purchased a refurbished iPhone 8 Plus (64GB variant) for around ₹16k-₹17k (less than $200) from [Cashify](https://www.cashify.in/). Cashify is a bit on the pricier side, I recommend checking local resellers first for better deals.

The device was in good condition with minor screen bleed. Surprisingly, it came with iOS 16.3.1 instead of the expected iOS 11. 

Now, let's move on to jailbreaking.

## Choosing the Right Jailbreaking Software
---
After some research, I found that Dopamine and Palera1n were suitable jailbreak options for my iOS version.

I opted for [Dopamine](https://github.com/opa334/Dopamine) since Palera1n didn't work on my Windows laptop. Dopamine offered a straightforward one-click jailbreaking process. However, it's an untethered jailbreak, meaning it will be lost if the device is rebooted or turned off. Sometimes, multiple attempts and switching exploit types are required to make it work.

Once successful, you will have access to Sileo Store to install required software.

Here are my recommended software installations from the Sileo store:

- **trollstore**: For installing .ipa files directly on the device.
- **Newterm**: A terminal emulator.
- **Filza**: A file manager.
- **Ellekit**: Useful for installing tweaks (requires further research for a complete understanding).

## Implementing SSL Killswitch 3
---
To disable SSL/TLS certificate validation, including certificate pinning, within iOS, I used [SSLKillswitch3](https://github.com/NyaMisty/ssl-kill-switch3).

Before installing SSLKillswitch3, ensure that the PreferenceLoader package is installed from the Sileo store. Download the rootless deb from the releases tab onto the iPhone and open the .ipa file using Filza. The file should install successfully.

Navigate to Settings to check if the SSLKillswitch3 menu item is available.

## Overcoming a Major Hurdle: Proxy Issues
---
Despite following the [Burp Suite tutorial](https://portswigger.net/burp/documentation/desktop/mobile/config-ios-device) meticulously, I faced an issue where applications didn't proxy traffic through Burp Suite. The iPhone seemed to ignore or fail to connect to the proxy settings.

After trying numerous solutions, including resetting internet settings and re-rooting the device, I finally found a workaround. Setting up a Wi-Fi hotspot on my laptop and configuring the laptop's IP as the proxy for that network resolved the issue.

And there you have it! 

That's my Level 1 iOS Pentest setup.

## Future Additions
---
For Level 2, I plan to:

- Acquire a Mac OS-based system or VM for Xcode and related tasks.
- Explore and incorporate new tools and techniques as I continue my journey.

I might also consider adding MobSF installation and static testing to my Level 1 arsenal in the future. 

Happy hacking!