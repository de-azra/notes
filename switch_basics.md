# Cisco Lab Switch basics

I got myself an old Cisco 2960 switch and while trying to set it up with a base configuration to use in my homelab, I realized that although I spent several months of my life with Cisco switches, I have pretty much forgotten everything... yeah. So I decided to note down all the relevant stuff - should I ever need to do this again.

## +++ Factory Reset Switch +++

**Step1:** Connect up your console cable and power on the switch, whilst holding down the “mode” button.

**Step2:** switch:flash_init

**Step3:** switch:del flash:config.text

**Step4:** switch:del flash:vlan.dat

**Step5:** switch:boot

[Source](http://notthenetwork.me/blog/2013/05/28/reset-a-cisco-2960-switch-to-factory-default-settings/)

## +++ Activate Management over IP +++

**Step1:** switch>en

**Step2:** switch#conf t

**Step3:** switch#int vlan 1

**Step4:** switch#ip address 10.0.0.123 255.255.255.0

**Step5:** switch#no shutdown

**Step6:** switch#end

**Step7:** Give it a bit and connect via browser

[Source](https://www.dummies.com/programming/networking/cisco/cisco-networking-switch-management-interface-configuration/)

## +++ Activate Web UI +++

For some reason the web ui doesn't just come up. But this helped

**Step1:** switch#no aaa new-model

**Step2:** switch# ip http authentication local

[Source](https://community.cisco.com/t5/switching/3850-webui-will-not-log-in/td-p/3015188)

## +++ Enable SSH on a Cisco switch +++

**Step1:** switch#crypto key generate rsa

**Step2:** switch#line vty 0 4

**Step3:** switch()#transport input ssh

**Step4:** switch()#login local

**Step5:** switch()#password 7

**Step6:** switch()#exit

[Source](https://www.thegeekstuff.com/2013/08/enable-ssh-cisco/)

## +++ Update IOS Version +++

[Source](https://www.thegeekstuff.com/2011/06/upgrade-cisco-ios-image/

## --- Extracting a tar file ---

[Source](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst2960/software/release/12-2_58_se/configuration/guide/2960scg/swiosfs.html

## --- Notes ---

[Download Page for IOSs](https://software.cisco.com/download/home/279963472/type/280805680/release/15.0.2-SE11)
**.bin file** CLI file without web frontend
**.tar file** is an ISO with web frontend
