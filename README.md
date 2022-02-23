# <Your-Project-Title>
## <img src="images/description.jpg" alt="Logo" width="1698">
  
<div align="justify">
  
The tests chosen for the analysis of the devices are set out below, with a brief description of each one:
- **Authentication**: the application associated with the wearable implements a method to authenticate the user's identity.
- **Insecure pairing method**: the link between the wearable and the mobile device uses a pairing method considered insecure or ineffective against MITM or passive eavesdropping attacks and lacks privacy safeguards:
  -	_Just Works_ does not provide any protection against MITM and eavesdropping attacks .
  -	_Numeric Comparison_ does not protect against eavesdropping.
  -	_Passkey_ does not protect a device against eavesdropping in BLE v 4.2 [1], [2].
- **Unencrypted Communications**: the BLE communication between the wearable device and smartphone is not encrypted. 
- **Encryption keys sent in plain text**: during the pairing process, the wearable and mobile devices exchange encryption keys in a format that can be easily captured and processed by the BLE sniffer.
- **Static MAC address**: the wearable uses a static MAC address (i.e., it does not change when the device is turned off or restarted), exposing it to tracking and user identification attacks.
- **Transmission of sensitive information to third-party servers**: the fitness application sends sensitive user information to third-party servers.
- Sending of information and firmware updates via HTTP: The application receives firmware updates and sends requests with sensitive information using HTTP without TLS.

</div>
  
## <img src="images/testwithus.jpg" alt="Logo" width="1698">

<div align="justify">

The generalised **operation process** for different models of wearables is outlined below. The procedure to be followed:
  - Switching on the wearable and mobile device.
  - Connection of the wearable with nRF52 DK and Wireshark.
  - Registering/Logging in to the application.
  - Pairing process of wearable device and smartphone.
  - BLE data collection activities:
    - Carrying out physical activities such as walking, running, etc.
    - Data Synchronization with wearable.
    - Disconnection from wearable.
    - Reconnection with wearable.
  - HTTP data collection activities:
    - Editing the user profile.
    - Synchronization of data with cloud server.
    - Logging off.
    - Logging in.
  - Disconnection.

</div>
  
## <img src="images/results.jpg" alt="Logo" width="1698">
  
<div align="justify">

Our results show a clear difference between devices from well-known brands versus those less known to consumers. The first ones implement more security and privacy measures than devices from smaller companies. Even so, many of them do not encrypt BLE communications or implement pairing methods that do not ensure the privacy of user data. Although they try to obfuscate their communications by using proprietary BLE services and attributes, it has been found on several occasions that these methods had been breached by reverse engineering and there is publicly accessible information describing their operation.
  
On the other hand, the only wearables which can prevent MITM, and eavesdropping attacks are the ones that implement BLE Secure Connections with ECDH key exchange or secure proprietary exchange methods. All other systems use outdated legacy versions of BLE, with Legacy Pairing methods such as Just Works that allow an attacker to intercept keys and access decrypted traffic. Nonetheless, all devices are susceptible to being attacked by KNOB or BIAS, due to a vulnerability in the Bluetooth architecture in versions 5 or less.
  
As for fitness apps and their privacy, all of them seem to state that they collect sensitive user information in their privacy policies. Moreover, some apps used by smaller brands send private date over an insecure channel (HTTP), while the rest (well-known brand apps) implement Certificate Pinning on HTTPS/TLS avoiding MITM and eavesdropping attacks with tools like mitmproxy. Only the applications used by high-end wearables require user authentication, and in the case of devices specifically designed for minors, only a minority applies specific measures to protect the minor's information.
  
Those applications that do not encrypt either the BLE connection or requests sent over HTTP, are the most insecure and least private among those analysed. Its operation is vulnerable to reverse engineering attacks, regardless of the connected device. 
  
One last particularly relevant finding from the analysis is that most of the devices analysed make use of static MAC addresses. The MAC address of a BLE peripheral device is constantly advertised unencrypted when it is disconnected from its central controller, making it vulnerable to being tracked and identified by an attacker. 
  
</div>
