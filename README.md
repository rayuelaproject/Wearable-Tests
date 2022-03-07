# <Your-Project-Title>
## <img src="images/description.jpg" alt="Logo" width="1698">
  
<div align="justify">
  
The tests chosen for the analysis of the devices are set out below, with a brief description of each one:
<br />
<ul>
  <br />
  <li><strong>Authentication</strong>: the application associated with the wearable implements a method to authenticate the user's identity.</li>  
  <br />
  <li><strong>Insecure pairing method</strong>: the link between the wearable and the mobile device uses a pairing method considered insecure or ineffective against MITM or passive eavesdropping attacks and lacks privacy safeguards:</li> 
  <ul>
    <li><i>Just Works</i> does not provide any protection against MITM and eavesdropping attacks.</li>
    <li><i>Numeric Comparison</i> does not protect against eavesdropping.</li>
    <li><i>Passkey</i> does not protect a device against eavesdropping in BLE v 4.2.</li>
  </ul>
  <br />
  <li><strong>Unencrypted Communications</strong>: the BLE communication between the wearable device and smartphone is not encrypted. </li> 
  <br />
  <li><strong>Encryption keys sent in plain text</strong>: during the pairing process, the wearable and mobile devices exchange encryption keys in a format that can be easily captured and processed by the BLE sniffer.</li> 
  <br />
  <li><strong>Static MAC address</strong>: the wearable uses a static MAC address (i.e., it does not change when the device is turned off or restarted), exposing it to tracking and user identification attacks.</li> 
  <br />
  <li><strong>Transmission of sensitive information to third-party servers</strong>: the fitness application sends sensitive user information to third-party servers.</li> 
  <ul>
    <li>Sending of information and firmware updates via HTTP: The application receives firmware updates and sends requests with sensitive information using HTTP without TLS.</li>
  </ul>
</ul>

<p align="right">(<a href="https://soniasoleracotanilla.github.io/Tests/">Back Testing</a>)</p>
</div>
        

## <img src="images/testwithus.jpg" alt="Logo" width="1698">

<div align="justify">

The generalised <b>operation process</b> for different models of wearables is outlined below. The procedure to be followed:
<br />
<br />
<ul>
  <li>Switching on the wearable and mobile device.</li>
  <li>Connection of the wearable with nRF52 DK and Wireshark.</li>
  <li>Registering/Logging in to the application.</li>
  <li>Pairing process of wearable device and smartphone.</li>
  <li>BLE data collection activities:</li>
  <ul>
    <li>Carrying out physical activities such as walking, running, etc.</li>
    <li>Data Synchronization with wearable.</li>
    <li>Disconnection from wearable.</li>
    <li>Reconnection with wearable.</li>
  </ul>
  <li>HTTP data collection activities:</li>
  <ul>
    <li>Editing the user profile.</li>
    <li>Synchronization of data with cloud server.</li>
    <li>Logging off.</li>
    <li>Logging in.</li>
  </ul>
  <li>Disconnection.</li>
</ul>

<p align="right">(<a href="https://soniasoleracotanilla.github.io/Tests/">Back Testing</a>)</p>

</div>        

## <img src="images/results.jpg" alt="Logo" width="1698">
  
<div align="justify">

Our results show a clear difference between devices from well-known brands versus those less known to consumers. The first ones implement more security and privacy measures than devices from smaller companies. Even so, many of them do not encrypt BLE communications or implement pairing methods that do not ensure the privacy of user data. Although they try to obfuscate their communications by using proprietary BLE services and attributes, it has been found on several occasions that these methods had been breached by reverse engineering and there is publicly accessible information describing their operation.
<br />
<br />
On the other hand, the only wearables which can prevent MITM, and eavesdropping attacks are the ones that implement BLE Secure Connections with ECDH key exchange or secure proprietary exchange methods. All other systems use outdated legacy versions of BLE, with Legacy Pairing methods such as Just Works that allow an attacker to intercept keys and access decrypted traffic. Nonetheless, all devices are susceptible to being attacked by KNOB or BIAS, due to a vulnerability in the Bluetooth architecture in versions 5 or less.
<br />
<br />
As for fitness apps and their privacy, all of them seem to state that they collect sensitive user information in their privacy policies. Moreover, some apps used by smaller brands send private date over an insecure channel (HTTP), while the rest (well-known brand apps) implement Certificate Pinning on HTTPS/TLS avoiding MITM and eavesdropping attacks with tools like mitmproxy. Only the applications used by high-end wearables require user authentication, and in the case of devices specifically designed for minors, only a minority applies specific measures to protect the minor's information.
<br />
<br />
Those applications that do not encrypt either the BLE connection or requests sent over HTTP, are the most insecure and least private among those analysed. Its operation is vulnerable to reverse engineering attacks, regardless of the connected device. 
<br />
<br />
One last particularly relevant finding from the analysis is that most of the devices analysed make use of static MAC addresses. The MAC address of a BLE peripheral device is constantly advertised unencrypted when it is disconnected from its central controller, making it vulnerable to being tracked and identified by an attacker. 
<p align="right">(<a href="https://soniasoleracotanilla.github.io/Tests/">Back Testing</a>)</p>
</div>
        

