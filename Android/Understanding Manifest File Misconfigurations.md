# Understanding Manifest File Misconfigurations
From the perspective of security the manifest file is usually the first thing that a penetration tester will check on an engagement.
We need to ensure that the Manifest file doesn’t contain any misconfigurations which can be leveraged by an attacker in a malicious way.

## Debug Mode

The **debuggable** attribute defines whether the application can be debugged or not.

If the application can be debugged then it can be leverged by an attacker to gather plenty of information.

_**Android applications that are not in the production state are expected to have this attribute set to true to assist the developers however before the actual release of the application this tag should be set to false.**_

```
1	<application
2	android:debuggable="false"
3	</application>

```

## BackUp Flag

The **allowBackup** attribute defines whether application data can be backed up and restored by a user who has enabled usb debugging.

_**Applications that handle and store sensitive information such as card details, passwords etc. should have this setting set to false to prevent such risks**_.

```
1	<application
2	android:allowBackup="false"
3	</application>

```

## External Storage

_**Applications that have the permission to copy data to external storage should be reviewed to ensure that no sensitive information is stored.**_

```
1	<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
```

## Permissions

The **android:protectionLevel** attribute defines the procedure that the system should follow before it grants the permission to the application that has requested it.

There are four values that can be used with this attribute:

	• normal
	• dangerous
	• signature
 	• signatureOrSystem
 
_**All the permissions that the application requests should be reviewed to ensure that they don’t introduce a security risk.**_

```
1	<permission>
2	android:protectionLevel="signature"
3	</permission>
```

## Application Components

Depending of the functionality, an application can launch a service, perform an activity, receive content from another source or receive intents by the phone or by other applications. There are four application components:

	• Activities
	• Services
	• Content Providers
	• Broadcast Receivers
 
_**Activities, Services, Content Providers and Broadcast Receivers can all be exported. Therefore all of them they should be reviewed that they don’t perform any sensitive action and that they are protected by appropriate permissions as otherwise information could be exposed to malicious third parties.**_

The following image demonstrates how a broadcast receiver is defined in the manifest file:
```
1	<receiver
2	android:exported="true"
3	android:name="string"
4	android:permission="string"
5	</receiver>
```
## Intents

Intents can be used to launch an activity, to send it to any interested broadcast receiver components, and to communicate with a background service.

_**Intents messages should be reviewed to ensure that they doesn’t contain any sensitive information that could be intercepted.**_
```
1	<intent-filter>
2	<action android:name="string" />
3	<category android:name="string" />
4	</intent-filter>
```


























