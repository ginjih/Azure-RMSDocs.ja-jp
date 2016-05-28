---
# required metadata

title: 電子メール通知の有効化 |Azure RMS
description: 電子メール通知を使用すると、保護されたコンテンツがアクセスされたたときに、そのコンテンツの所有者に通知することができます。
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: fcaa5643-64a9-4181-b29b-90211fce7ab5

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

﻿
# 電子メール通知の有効化

電子メール通知を使用すると、保護されたコンテンツがアクセスされたたときに、そのコンテンツの所有者に通知することができます。

任意のライセンスの電子メール通知をセットアップするには、プロパティの型パラメーター *dwPropID* を [**IPC\_LI\_APP\_SPECIFIC\_DATA**](/rights-management/sdk/2.1/api/win/License%20property%20types#msipc_license_property_types_IPC_LI_APP_SPECIFIC_DATA)、アプリケーション データ フィールドの形式を [**IPC\_NAME\_VALUE\_LIST**](/rights-management/sdk/2.1/api/win/structures#msipc_ipc_name_value_list) として [**IpcSetLicenseProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicenseproperty) を使用します。

## C++

    ...
    int numDataPairs = 3;

    IPC_NAME_VALUE propertyValuePairs [numDataPairs];

    // lcid field set to 0 causes the default lcid to be used

    propertyValuePairs[0] = {&quot;MS.Conetent.Name&quot;, 0, &quot;FinancialReport.docx&quot;};
    propertyValuePairs[1] = {&quot;MS.Notify.Enabled&quot;,0 , &quot;true&quot;};
    propertyValuePairs[2] = {&quot;MS.Notify.Culture&quot;,0 , “en-US”};

    IPC_NAME_VALUE_LIST emailNotificationAppData = {numDataPairs, propertyValuePairs};

    result = IpcSetLicenseProperty( licenseHandle, FALSE, IPC_LI_APP_SPECIFIC_DATA, emailNotificationAppData);
    ...    

次の表に RMS 電子メール通知の、アプリケーション データ フィールド、プロパティの名前と値のペアを示します。


|プロパティ名 | データ型 | 値の例 | 注 |
|--------------|-----------|---------------|-------|
|MS.Content.Name|string|“FinancialReport.docx”|保護されたコンテンツに関連付けられている識別子です。<br><br> 保護されたファイルでは、この値はパス情報がないファイルの名前にする必要があります。<br><br> 電子メール メッセージなどの他の種類のコンテンツでは、電子メールの件名であったり、空であったりする場合もあります。|
|MS.Notify.Enabled|string|“true”、“false”|この値を "true" にすると、だれかが発行ライセンスを使用してエンド ユーザー ライセンスを取得しようとしたときに、発行ライセンスの所有者に通知電子メールが送信されます。|
|MS.Notify.Culture|string|“en-US”| **ソース:** System.Globalization.CultureInfo.CurrentUICulture.Name <br><br>この値は、通知電子メールのローカライズ言語と、電子メール メッセージで使用する日付/時刻と数値の書式設定の指定に使用します。<br><br>発行ライセンスが作成されたコンピューターのユーザー設定、または発行ライセンスの所有者の優先カルチャに基づいて設定してください。|
|MS.Notify.TZID|string|“Pacific Standard Time”|**ソース:** TimeZoneInfo.Local.Id - Windows タイム ゾーンの ID。<br><br>この値は、特定のタイム ゾーンとその特性を表す Microsoft Windows OS のタイム ゾーンの識別子です。|
|MS.Notify.TZO|string|“-480”|UTC 時刻の分の観点から求められる、発行ライセンス所有者のタイム ゾーン オフセットです。<br><br>有効な TZID 値が指定されている場合は、それによって指定されるタイム ゾーンのオフセットが使用され、この値は無視されます。<br><br>ほとんどの場合、この値は Windows OS のタイム ゾーン ID 値のリストへのアクセス権がない非 Windows ベースの公開プラットフォームで使用されます。<br><br>TZID 値が指定されていない場合は、通知メッセージのタイム オフセットの計算にこの値が使用され、タイム ゾーン名の表示に (タイム ゾーン値に関係なく) TZSN が使用されます。 これにより、タイム ゾーンが固定され、夏時間で更新されなくなります (該当する場合)。<br><br>例:<br><br>TXID を空白、TZ0 を「-420」、TZSN を「Pacific Daylight Time」に設定すると、通知電子メールに表示されるすべての値が「太平洋夏時間」に調整され、夏時間ではなくなった場合でもそのように表示されます。<br><br>その一方で、TZID と共に TZSN と TZDN を指定すると、通知電子メール内に指定された時刻の調整と表示は、日付と時刻を夏時間モードと標準モードのどちらで表示するかに基づいて決まります。|
|MS.Notify.TZSN|string|“Pacific Standard Time”|**ソース:** TimeZoneInfo.Local.StandardName - 標準タイム ゾーンの名前。<br><br>タイム ゾーンの標準タイム ゾーン名のローカライズされた名前にする必要があります。|
|MS.Notify.TZDN|string|“Pacific Daylight Time”|**ソース:** TimeZoneInfo.Local.DaylightName - 夏時間タイム ゾーンの名前。<br><br>タイム ゾーンの夏時間名のローカライズされた名前にする必要があります。 タイム ゾーンが夏時間をサポートしていない場合は、標準名と同じにすることができます。|

## 関連項目

* [**IpcSetLicenseProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicenseproperty)
* [**IPC\_LI\_APP\_SPECIFIC\_DATA**](/rights-management/sdk/2.1/api/win/License%20property%20types#msipc_license_property_types_IPC_LI_APP_SPECIFIC_DATA)
* [**IPC\_NAME\_VALUE\_LIST**](/rights-management/sdk/2.1/api/win/structures#msipc_ipc_name_value_list)
 

 


<!--HONumber=Apr16_HO3-->

