---
title: 使用敏感信息类型查找什么
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: reference
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
description: Office 365 安全&amp;合规中心中的数据丢失防护（DLP）包括可供您在 DLP 策略中使用的80敏感信息类型。 本主题列出了所有这些敏感信息类型，并显示 DLP 策略在检测到每种类型时查找的内容。
ms.openlocfilehash: bd74551b7e8b2d659724a1222e115a479db76ec8
ms.sourcegitcommit: fce0d5cad32ea60a08ff001b228223284710e2ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "42894295"
---
# <a name="what-the-sensitive-information-types-look-for"></a>使用敏感信息类型查找什么

Office 365 安全&amp;合规中心中的数据丢失防护（DLP）包括许多可供您在 DLP 策略中使用的敏感信息类型。 本主题列出了所有这些敏感信息类型，并显示 DLP 策略在检测到每种类型时查找的内容。 敏感信息类型通过正则表达式或函数可以识别的模式定义。 此外，关键字和校验和等确凿的证据可用于识别敏感信息类型。 可信度和相似度也会在评估过程中使用。
  
## <a name="aba-routing-number"></a>ABA 银行代号

### <a name="format"></a>Format

9 个数字，可以是格式化模式，也可以是非格式化模式 

### <a name="pattern"></a>模式

格式
- 四个数字，以 0、 1、 2、 3、 6、 7 或 8 开头
- 一个连字符 
- 四个数字
- 一个连字符 
- 一个数字

无格式：9个连续的数字，以0、1、2、3、6、7或8开头 

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_aba_routing 找到与该模式匹配的内容。
- 找到 Keyword_ABA_Routing 中的一个关键字。

```xml
<!-- ABA Routing Number -->
<Entity id="cb353f78-2b72-4c3c-8827-92ebe4f69fdf" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_aba_routing" />
        <Match idRef="Keyword_ABA_Routing" />
      </Pattern>
 </Entity>
```


### <a name="keywords"></a>关键字

#### <a name="keyword_aba_routing"></a>Keyword_ABA_Routing

- aba
- aba #
- aba routing #
- aba routing number
- aba#
- abarouting#
- aba number
- abaroutingnumber
- american bank association routing #
- american bank association routing number
- americanbankassociationrouting#
- americanbankassociationroutingnumber
- bank routing number
- bankrouting#
- bankroutingnumber
- routing transit number
- RTN 
   
## <a name="argentina-national-identity-dni-number"></a>阿根廷国家身份证 (DNI) 号

### <a name="format"></a>Format

八个数字，用点分隔

### <a name="pattern"></a>模式

八个数字：
- 两个数字
- 一个点 
- 三个数字 
- 一个点 
- 三位数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_argentina_national_id 找到与该模式匹配的内容。
- 找到 Keyword_argentina_national_id 中的一个关键字。

```xml
<!-- Argentina National Identity (DNI) Number -->
<Entity id="eefbb00e-8282-433c-8620-8f1da3bffdb2" recommendedConfidence="75" patternsProximity="300">
   <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_argentina_national_id"/>
      <Match idRef="Keyword_argentina_national_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- Argentina National Identity number 
- 标识 
- 标识国家/地区身份卡片 
- DNI 
- 个人的网络国家注册表 
- Documento Nacional de Identidad 
- Registro Nacional de las Personas 
- Identidad 
- Identificación 
   
## <a name="australia-bank-account-number"></a>澳大利亚银行帐号

### <a name="format"></a>Format

6-10 个数字，带或不带 BSB 号码 

### <a name="pattern"></a>模式

帐号为 6-10 个数字。
澳大利亚银行州级分部编号：
- 三个数字  
- 连字符 
- 三位数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_australia_bank_account_number 找到与该模式匹配的内容。
- 找到 Keyword_australia_bank_account_number 中的一个关键字。
- 正则表达式 Regex_australia_bank_account_number_bsb 找到与该模式匹配的内容。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_australia_bank_account_number 找到与该模式匹配的内容。
- 找到 Keyword_australia_bank_account_number 中的一个关键字。

```xml
<!-- Australia Bank Account Number -->
<Entity id="74a54de9-2a30-4aa0-a8aa-3d9327fc07c7" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
        <Match idRef="Regex_australia_bank_account_number_bsb" />
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
  </Pattern>
 </Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_australia_bank_account_number"></a>Keyword_australia_bank_account_number

- swift bank code
- correspondent bank
- base currency
- usa account
- holder address
- bank address
- information account
- fund transfers
- bank charges
- bank details
- banking information
- full names
- iaea

   
## <a name="australia-drivers-license-number"></a>澳大利亚驾驶证号码

### <a name="format"></a>Format

九个字母和数字

### <a name="pattern"></a>模式

九个字母和数字： 

- 两位数字或字母（不区分大小写） 
- 两位数字 
- 五位数字或字母（不区分大小写）

或

- 1-2 个可选字母（不区分大小写）  
- 4-9 位数字

或

- 九个数字或字母（不区分大小写）

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_australia_drivers_license_number 找到与该模式匹配的内容。
- 找到 Keyword_australia_drivers_license_number 中的一个关键字。
- 未找到 Keyword_australia_drivers_license_number_exclusions 中的关键字。

```xml
<!-- Australia Drivers License Number -->
<Entity id="1cbbc8f5-9216-4392-9eb5-5ac2298d1356" patternsProximity="300" recommendedConfidence="75">
   <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_drivers_license_number" />
        <Match idRef="Keyword_australia_drivers_license_number" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_australia_drivers_license_number_exclusions" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_australia_drivers_license_number"></a>Keyword_australia_drivers_license_number

- international driving permits
- australian automobile association
- international driving permit
- DriverLicence
- DriverLicences
- Driver Lic
- Driver Licence
- Driver Licences
- DriversLic
- DriversLicence
- DriversLicences
- Drivers Lic
- Drivers Lics
- Drivers Licence
- Drivers Licences
- Driver'Lic
- Driver'Lics
- Driver'Licence
- Driver'Licences
- Driver' Lic
- Driver' Lics
- Driver' Licence
- Driver' Licences
- Driver'sLic
- Driver'sLics
- Driver'sLicence
- Driver'sLicences
- Driver's Lic
- Driver's Lics
- Driver's Licence
- Driver's Licences
- DriverLic#
- DriverLics#
- DriverLicence#
- DriverLicences#
- Driver Lic#
- Driver Lics#
- Driver Licence#
- Driver Licences#
- DriversLic#
- DriversLics#
- DriversLicence#
- DriversLicences#
- Drivers Lic#
- Drivers Lics#
- Drivers Licence#
- Drivers Licences#
- Driver'Lic#
- Driver'Lics#
- Driver'Licence#
- Driver'Licences#
- Driver' Lic#
- Driver' Lics#
- Driver' Licence#
- Driver' Licences#
- Driver'sLic#
- Driver'sLics#
- Driver'sLicence#
- Driver'sLicences#
- Driver's Lic#
- Driver's Lics#
- Driver's Licence#
- Driver's Licences# 

#### <a name="keyword_australia_drivers_license_number_exclusions"></a>Keyword_australia_drivers_license_number_exclusions

- aaa
- DriverLicense
- DriverLicenses
- Driver License
- Driver Licenses
- DriversLicense
- DriversLicenses
- Drivers License
- Drivers Licenses
- Driver'License
- Driver'Licenses
- Driver' License
- Driver' Licenses
- Driver'sLicense
- Driver'sLicenses
- Driver's License
- Driver's Licenses
- DriverLicense#
- DriverLicenses#
- Driver License#
- Driver Licenses#
- DriversLicense#
- DriversLicenses#
- Drivers License#
- Drivers Licenses#
- Driver'License#
- Driver'Licenses#
- Driver' License#
- Driver' Licenses#
- Driver'sLicense#
- Driver'sLicenses#
- Driver's License#
- Driver's Licenses#
   
## <a name="australia-medical-account-number"></a>澳大利亚医疗帐号

### <a name="format"></a>Format

10-11 个数字

### <a name="pattern"></a>模式

10-11 个数字：
- 第一个数字范围为 2-6
- 第九个数字是校验位
- 第十个数字是问题数字
- 第十一个数字（可选）是个人号码

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 95% 确信它检测到这种类型的敏感信息：
- 函数 Func_australian_medical_account_number 找到与该模式匹配的内容。
- 找到 Keyword_Australia_Medical_Account_Number 中的一个关键字。
- 校验和通过。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_australian_medical_account_number 找到与该模式匹配的内容。
- 校验和通过。

```xml
  <!-- Australia Medical Account Number -->
<Entity id="104a99a0-3d3b-4542-a40d-ab0b9e1efe63" recommendedConfidence="85" patternsProximity="300">
    <Pattern confidenceLevel="95">
     <IdMatch idRef="Func_australian_medical_account_number"/>
     <Any minMatches="1">
     <Match idRef="Keyword_Australia_Medical_Account_Number"/>
     </Any>
  </Pattern>
<Pattern confidenceLevel="85">
     <IdMatch idRef="Func_australian_medical_account_number"/>
     <Any minMatches="0" maxMatches="0">
  <Match idRef="Keyword_Australia_Medical_Account_Number"/>
     </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_australia_medical_account_number"></a>Keyword_Australia_Medical_Account_Number

- bank account details
- medicare payments
- mortgage account
- bank payments
- information branch
- credit card loan
- department of human services
- local service
- medicare

   
## <a name="australia-passport-number"></a>澳大利亚护照号

### <a name="format"></a>Format

一个字母后跟七个数字

### <a name="pattern"></a>模式

一个字母（不区分大小写）后跟七个数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_australia_passport_number 找到与该模式匹配的内容。
- 找到 Keyword_passport 或 Keyword_australia_passport_number 中的关键字。

```xml
<!-- Australia Passport Number -->
<Entity id="29869db6-602d-4853-ab93-3484f905df50" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_passport_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_passport" />
          <Match idRef="Keyword_australia_passport_number" />
        </Any>
   </Pattern>
</Entity>   
```

### <a name="keywords"></a>关键字

#### <a name="keyword_passport"></a>Keyword_passport

- Passport Number
- Passport No
- Passport #
- 登记卡#
- PassportID
- Passportno
- passportnumber
- パスポート
- パスポート番号
- パスポートのNum
- パスポート ＃ 
- Numéro de passeport
- Passeport n °
- Passeport Non
- Passeport #
- Passeport#
- PasseportNon
- Passeportn °

#### <a name="keyword_australia_passport_number"></a>Keyword_australia_passport_number

- 登记卡
- passport details
- immigration and citizenship
- commonwealth of australia
- department of immigration
- residential address
- department of immigration and citizenship
- 反之
- national identity card
- passport number
- travel document
- issuing authority
   
## <a name="australia-tax-file-number"></a>澳大利亚税号

### <a name="format"></a>Format

8-9 个数字

### <a name="pattern"></a>模式

通常 8-9 位数字，显示中包含空格，如下所示：
- 三位数字 
- 可选空格 
- 三位数字 
- 可选空格 
- 2-3 位数字，最后一位数字是校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_australian_tax_file_number 找到与该模式匹配的内容。
- 未找到 Keyword_Australia_Tax_File_Number 或 Keyword_number_exclusions 中的关键字。
- 校验和通过。

```xml
   <!-- Australia Tax File Number -->
    <Entity id="e29bc95f-ff70-4a37-aa01-04d17360a4c5" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_australian_tax_file_number" />
        <Match idRef="Keyword_Australia_Tax_File_Number" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_number_exclusions" />
        </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_australia_tax_file_number"></a>Keyword_Australia_Tax_File_Number

- australian business number
- marginal tax rate
- medicare levy
- portfolio number
- service veterans
- withholding tax
- individual tax return
- tax file number

#### <a name="keyword_number_exclusions"></a>Keyword_number_exclusions

- 00000000
- 11111111
- 22222222
- 33333333
- 44444444
- 55555555
- 66666666
- 77777777
- 88888888
- 99999999
- 000000000
- 111111111
- 222222222
- 333333333
- 444444444
- 555555555
- 666666666
- 777777777
- 888888888
- 999999999
- 0000000000
- 1111111111
- 2222222222
- 3333333333
- 4444444444
- 5555555555
- 6666666666
- 7777777777
- 8888888888
- 9999999999

## <a name="azure-documentdb-auth-key"></a>Azure DocumentDB 身份验证密钥

### <a name="format"></a>Format

字符串 "DocumentDb"，后跟下面模式中所示的字符和字符串。

### <a name="pattern"></a>模式

- 字符串 "DocumentDb"
- 介于3-200 个字母、数字、符号、特殊字符或空格之间的任意组合
- 大于号（>）、等号（=）、引号（"）或撇号（'）
- 86字母、数字、数字、正斜杠（/）或加号（+）的任意组合
- 两个等号（=）

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 CEP_Regex_AzureDocumentDBAuthKey 找到与该模式匹配的内容。
- 正则表达式**CEP_CommonExampleKeywords 不会找到与**该模式匹配的内容。

```xml
<!-- Azure Document DB Auth Key -->
<Entity id="0f587d92-eb28-44a9-bd1c-90f2892b47aa" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureDocumentDBAuthKey" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
          </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

（请注意，从技术上讲，此敏感信息类型通过使用正则表达式（而不是关键字列表）来标识这些关键字。

- 尚未
- 送交
- 罗斯
- 沙盒
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int。<!--no-hyperlink-->netmeeting

## <a name="azure-iaas-database-connection-string-and-azure-sql-connection-string"></a>Azure IAAS 数据库连接字符串和 Azure SQL 连接字符串

### <a name="format"></a>Format

字符串 "Server"、"server" 或 "data source"，后跟下面模式中所述的字符和字符串，包括字符串 "cloudapp"。<!--no-hyperlink-->com "或" cloudapp "。<!--no-hyperlink-->net "或" database。<!--no-hyperlink-->net "和字符串" Password "或" password "或" pwd "。

### <a name="pattern"></a>模式

- 字符串 "Server"、"server" 或 "data source"
- 0-2 空白字符
- 等号（=）
- 0-2 空白字符
- 介于1-200 个字母、数字、符号、特殊字符或空格之间的任意组合
- 字符串 "cloudapp"。<!--no-hyperlink-->com "，" cloudapp。<!--no-hyperlink-->net "或" database。<!--no-hyperlink-->netmeeting
- 介于1-300 个字母、数字、符号、特殊字符或空格之间的任意组合
- 字符串 "Password"、"password" 或 "pwd"
- 0-2 空白字符
- 等号（=）
- 0-2 空白字符
- 一个或多个不是分号（;)、引号（"）或撇号（'）的字符
- 分号（;)、引号（"）或撇号（'）

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 CEP_Regex_AzureConnectionString 找到与该模式匹配的内容。
- 正则表达式**CEP_CommonExampleKeywords 不会找到与**该模式匹配的内容。

```xml
<!--Azure IAAS Database Connection String and Azure SQL Connection String-->
<Entity id="ce1a126d-186f-4700-8c0c-486157b953fd" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

（请注意，从技术上讲，此敏感信息类型通过使用正则表达式（而不是关键字列表）来标识这些关键字。

- 尚未
- 送交
- 罗斯
- 沙盒
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int。<!--no-hyperlink-->netmeeting

## <a name="azure-iot-connection-string"></a>Azure IoT 连接字符串

### <a name="format"></a>Format

字符串 "HostName"，后跟下面模式中所示的字符和字符串，包括字符串 "azure 设备"。<!--no-hyperlink-->net "和" SharedAccessKey "。

### <a name="pattern"></a>模式

- 字符串 "HostName"
- 0-2 空白字符
- 等号（=）
- 0-2 空白字符
- 介于1-200 个字母、数字、符号、特殊字符或空格之间的任意组合
- 字符串 "azure 设备。<!--no-hyperlink-->netmeeting
- 介于1-200 个字母、数字、符号、特殊字符或空格之间的任意组合
- 字符串 "SharedAccessKey"
- 0-2 空白字符
- 等号（=）
- 0-2 空白字符
- 43字母、数字、数字、正斜杠（/）或加号（+）的任意组合
- 等号（=）

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 CEP_Regex_AzureIoTConnectionString 找到与该模式匹配的内容。
- 正则表达式**CEP_CommonExampleKeywords 不会找到与**该模式匹配的内容。

```xml
<!--Azure IoT Connection String-->
<Entity id="0b34bec3-d5d6-4974-b7b0-dcdb5c90c29d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureIoTConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

（请注意，从技术上讲，此敏感信息类型通过使用正则表达式（而不是关键字列表）来标识这些关键字。

- 尚未
- 送交
- 罗斯
- 沙盒
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int。<!--no-hyperlink-->netmeeting

## <a name="azure-publish-setting-password"></a>Azure 发布设置密码

### <a name="format"></a>Format

字符串 "userpwd ="，后跟一个字母数字字符串。

### <a name="pattern"></a>模式

- 字符串 "userpwd ="
- 任何60小写字母或数字的组合
- 一个引号（"）

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 CEP_Regex_AzurePublishSettingPasswords 找到与该模式匹配的内容。
- 正则表达式**CEP_CommonExampleKeywords 不会找到与**该模式匹配的内容。


```xml
<!--Azure Publish Setting Password-->
<Entity id="75f4cc8a-a68e-49e5-89ce-fa8f03d286a5" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
       <IdMatch idRef="CEP_Regex_AzurePublishSettingPasswords" />
       <Any minMatches="0" maxMatches="0">
           <Match idRef="CEP_CommonExampleKeywords" />
       </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

（请注意，从技术上讲，此敏感信息类型通过使用正则表达式（而不是关键字列表）来标识这些关键字。

- 尚未
- 送交
- 罗斯
- 沙盒
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int。<!--no-hyperlink-->netmeeting

## <a name="azure-redis-cache-connection-string"></a>Azure Redis 缓存连接字符串

### <a name="format"></a>Format

字符串 "redis"。<!--no-hyperlink-->net "，后跟下面的模式中所述的字符和字符串，包括字符串" password "或" pwd "。

### <a name="pattern"></a>模式

- 字符串 "redis"。<!--no-hyperlink-->netmeeting
- 介于1-200 个字母、数字、符号、特殊字符或空格之间的任意组合
- 字符串 "password" 或 "pwd"
- 0-2 空白字符
- 等号（=）
- 0-2 空白字符
- 43个字符的任意组合，这些字符为小写字母、数字、斜杠（/）或加号（+）
- 等号（=）

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 CEP_Regex_AzureRedisCacheConnectionString 找到与该模式匹配的内容。。
- 正则表达式**CEP_CommonExampleKeywords 不会找到与**该模式匹配的内容。

```xml
<!--Azure Redis Cache Connection String-->
<Entity id="095a7e6c-efd8-46d5-af7b-5298d53a49fc" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureRedisCacheConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

（请注意，从技术上讲，此敏感信息类型通过使用正则表达式（而不是关键字列表）来标识这些关键字。

- 尚未
- 送交
- 罗斯
- 沙盒
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int。<!--no-hyperlink-->netmeeting

## <a name="azure-sas"></a>Azure SA

### <a name="format"></a>Format

字符串 "sig"，后跟下面模式中所示的字符和字符串。

### <a name="pattern"></a>模式

- 字符串 "sig"
- 0-2 空白字符
- 等号（=）
- 0-2 空白字符
- 介于43-53 个字符和小写字母、数字或百分比符号（%）之间的任意组合
- 字符串 "% 3d"
- 不是字母或大写字符、数字或百分号（%）的任何字符

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 CEP_Regex_AzureSAS 找到与该模式匹配的内容。

```xml
<!--Azure SAS-->
<Entity id="4d235014-e564-47f4-a6fb-6ebb4a826834" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureSAS" />
  </Pattern>
</Entity>
```

## <a name="azure-service-bus-connection-string"></a>Azure 服务总线连接字符串

### <a name="format"></a>Format

字符串 "终结点"，后跟下面模式中所示的字符和字符串，包括字符串 "<!--no-hyperlink-->net "和" SharedAccesKey "。

### <a name="pattern"></a>模式

- 字符串 "EndPoint"
- 0-2 空白字符
- 等号（=）
- 0-2 空白字符
- 介于1-200 个字母、数字、符号、特殊字符或空格之间的任意组合
- 字符串 "<!--no-hyperlink-->netmeeting
- 介于1-200 个字母、数字、符号、特殊字符或空格之间的任意组合
- 字符串 "SharedAccessKey"
- 0-2 空白字符
- 等号（=）
- 0-2 空白字符
- 43个字符的任意组合，这些字符为小写字母、数字、斜杠（/）或加号（+）
- 等号（=）

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 CEP_Regex_AzureServiceBusConnectionString 找到与该模式匹配的内容。。
- 正则表达式**CEP_CommonExampleKeywords 不会找到与**该模式匹配的内容。

```xml
<!--Azure Service Bus Connection String-->
<Entity id="b9a6578f-a83f-4fcd-bf44-2130bae49a6f" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureServiceBusConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

（请注意，从技术上讲，此敏感信息类型通过使用正则表达式（而不是关键字列表）来标识这些关键字。

- 尚未
- 送交
- 罗斯
- 沙盒
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int。<!--no-hyperlink-->netmeeting

## <a name="azure-storage-account-key"></a>Azure 存储帐户密钥

### <a name="format"></a>Format

字符串 "DefaultEndpointsProtocol"，后跟下面模式中所述的字符和字符串，包括字符串 "AccountKey"。

### <a name="pattern"></a>模式

- 字符串 "DefaultEndpointsProtocol"
- 0-2 空白字符
- 等号（=）
- 0-2 空白字符
- 介于1-200 个字母、数字、符号、特殊字符或空格之间的任意组合
- 字符串 "AccountKey"
- 0-2 空白字符
- 等号（=）
- 0-2 空白字符
- 86个字符的任意组合，这些字符为小写字母、数字、斜杠（/）或加号（+）
- 两个等号（=）

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 CEP_Regex_AzureStorageAccountKey 找到与该模式匹配的内容。
- 正则表达式**CEP_AzureEmulatorStorageAccountFilter 不会找到与**该模式匹配的内容。
- 正则表达式**CEP_CommonExampleKeywords 不会找到与**该模式匹配的内容。

```xml
<!--Azure Storage Account Key-->
<Entity id="c7bc98e8-551a-4c35-a92d-d2c8cda714a7" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKey" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_AzureEmulatorStorageAccountFilter" />
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="cep_azureemulatorstorageaccountfilter"></a>CEP_AzureEmulatorStorageAccountFilter

（请注意，从技术上讲，此敏感信息类型通过使用正则表达式（而不是关键字列表）来标识这些关键字。

- Eby8vdM02xNOcqFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw = =

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

（请注意，从技术上讲，此敏感信息类型通过使用正则表达式（而不是关键字列表）来标识这些关键字。

- 尚未
- 送交
- 罗斯
- 沙盒
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int。<!--no-hyperlink-->netmeeting

## <a name="azure-storage-account-key-generic"></a>Azure 存储帐户密钥（常规）

### <a name="format"></a>Format

任何86位或大写字母、数字、正斜杠（/）或加号（+）的任意组合，前面或后面是下面模式中所述的字符。

### <a name="pattern"></a>模式

- 大于号（>）、撇号（'）、等号（=）、引号（"）或数字符号（#）的0-1
- 86个字符的任意组合，这些字符为小写字母、数字、斜杠（/）或加号（+）
- 两个等号（=）


### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 CEP_Regex_AzureStorageAccountKeyGeneric 找到与该模式匹配的内容。

```xml
<!--Azure Storage Account Key (Generic)-->
<Entity id="7ff41bd0-5419-4523-91d6-383b3a37f084" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKeyGeneric" />
  </Pattern>
</Entity>
```

## <a name="belgium-national-number"></a>比利时国家号码

### <a name="format"></a>Format

11 个数字加分隔符

### <a name="pattern"></a>模式

11 个数字加分隔符：
- 六个数字加两个点，采用格式  YY.MM.DD，代表出生日期   
- 一个连字符  
- 三个连续的数字（男性用奇数，女性用偶数）  
- 一个点 
- 两个数字，是校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_belgium_national_number 找到与该模式匹配的内容。
- 找到 Keyword_belgium_national_number 中的一个关键字。
- 校验和通过。

```xml
<!-- Belgium National Number -->
  <Entity id="fb969c9e-0fd1-4b18-8091-a2123c5e6a54" recommendedConfidence="75" patternsProximity="300">
   <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_belgium_national_number"/>
     <Match idRef="Keyword_belgium_national_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_belgium_national_number"></a>Keyword_belgium_national_number

- 标识
- 注册
- Id 
- ID 
- Identiteitskaart
- Registratie nummer 
- Identificatie nummer 
- Identiteit
- Registratie
- Identificatie 
- Carte d’identité 
- numéro d'immatriculation
- numéro d'identification
- identité 
- inscription 
- Identifikation
- Identifizierung
- Identifikationsnummer
- Personalausweis
- Registrierung
- Registrationsnummer

   
## <a name="brazil-cpf-number"></a>巴西 CPF 号码

### <a name="format"></a>Format

11 个数字（包括校验位），可以格式化，也可以非格式化

### <a name="pattern"></a>模式

格式
- 三位数字 
- 一个点  
- 三位数字 
- 一个点  
- 三位数字 
- 一个连字符  
- 两个数字，是校验位

纯
- 11 个数字，其中最后两个数字是校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_brazil_cpf 找到与该模式匹配的内容。
- 找到 Keyword_brazil_cpf 中的一个关键字。
- 校验和通过。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_brazil_cpf 找到与该模式匹配的内容。
- 校验和通过。

```xml
<!-- Brazil CPF Number -->
<Entity id="78e09124-f2c3-4656-b32a-c1a132cd2711" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_cpf"/>
     <Match idRef="Keyword_brazil_cpf"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_cpf"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_brazil_cpf"></a>Keyword_brazil_cpf

- CPF
- Id
- 注册
- 营业
- Cadastro de Pessoas Físicas 
- Imposto 
- Identificação 
- Inscrição 
- Receita 
   
## <a name="brazil-legal-entity-number-cnpj"></a>巴西法律实体编号 (CNPJ)

### <a name="format"></a>Format

14 个数字（包括注册号、分行号码和校验位），再加上分隔符

### <a name="pattern"></a>模式
14 个数字，再加上分隔符：
- 两个数字  
- 一个点  
- 三个数字  
- 一个点  
- 三个数字（前 8 位数是注册号）  
- 正斜杠  
- 四位分行号码  
- 一个连字符  
- 两个数字，是校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_brazil_cnpj 找到与该模式匹配的内容。
- 找到 Keyword_brazil_cnpj 中的一个关键字。
- 校验和通过。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_brazil_cnpj 找到与该模式匹配的内容。
- 校验和通过。

```xml
<!-- Brazil Legal Entity Number (CNPJ) -->
<Entity id="9b58b5cd-5e90-4df6-b34f-1ebcc88ceae4" recommendedConfidence="85" patternsProximity="300">
   <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_cnpj"/>
     <Match idRef="Keyword_brazil_cnpj"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_cnpj"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_brazil_cnpj"></a>Keyword_brazil_cnpj

- CNPJ 
- CNPJ/MF 
- CNPJ-MF 
- National Registry of Legal Entities 
- Taxpayers Registry 
- Legal entity 
- Legal entities 
- Registration Status 
- 商业版 
- Company
- CNPJ 
- Cadastro Nacional da Pessoa Jurídica 
- Cadastro Geral de Contribuintes 
- CGC 
- Pessoa jurídica 
- Pessoas jurídicas 
- Situação cadastral 
- Inscrição 
- Empresa 
   
## <a name="brazil-national-id-card-rg"></a>	巴西国家身份证 (RG)

### <a name="format"></a>Format

Registro Geral （旧格式）：9个数字

Registro de Identidade （RIC）（新格式）：11个数字

### <a name="pattern"></a>模式

Registro Geral（旧格式）：
- 两个数字  
- 一个点  
- 三个数字  
- 一个点  
- 三个数字  
- 一个连字符  
- 一个数字，是校验位

Registro de Identidade （RIC）（新格式）：
- 10 个数字 
- 一个连字符  
- 一个数字，是校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_brazil_rg 找到与该模式匹配的内容。
- 找到 Keyword_brazil_rg 中的一个关键字。
- 校验和通过。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_brazil_rg 找到与该模式匹配的内容。
- 校验和通过。

```xml
<!-- Brazil National ID Card (RG) -->
<Entity id="486de900-db70-41b3-a886-abdf25af119c" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_rg"/>
     <Match idRef="Keyword_brazil_rg"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_rg"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_brazil_rg"></a>Keyword_brazil_rg

Cédula de identidade identity 卡片国家 id número de rregistro registro de Iidentidade registro geral RG （此关键字区分大小写） RIC （此关键字区分大小写） 
   
## <a name="canada-bank-account-number"></a>加拿大银行帐号

### <a name="format"></a>Format

七个或十二个数字

### <a name="pattern"></a>模式

加拿大银行帐号是七个或十二个数字。

加拿大银行帐户的银行代号是：
- 五位数字 
- 连字符 
- 三位数字或
- 一个零“0”  
- 八位数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_canada_bank_account_number 找到与该模式匹配的内容。
- 找到 Keyword_canada_bank_account_number 中的一个关键字。
- 正则表达式 Regex_canada_bank_account_transit_number 找到与该模式匹配的内容。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_canada_bank_account_number 找到与该模式匹配的内容。
- 找到 Keyword_canada_bank_account_number 中的一个关键字。

```xml
<!-- Canada Bank Account Number -->
<Entity id="552e814c-cb50-4d94-bbaa-bb1d1ffb34de" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
        <Match idRef="Regex_canada_bank_account_transit_number" />
   </Pattern>
   <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
   </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_canada_bank_account_number"></a>Keyword_canada_bank_account_number

- canada savings bonds
- canada revenue agency
- canadian financial institution
- direct deposit form
- canadian citizen
- legal representative
- notary public
- commissioner for oaths
- child care benefit
- universal child care
- canada child tax benefit
- income tax benefit
- harmonized sales tax
- social insurance number
- income tax refund
- child tax benefit
- territorial payments
- institution number
- deposit request
- banking information
- direct deposit
   
## <a name="canada-drivers-license-number"></a>加拿大驾驶证号码

### <a name="format"></a>Format

因省而异

### <a name="pattern"></a>模式

各种模式，涵盖艾伯塔、 不列颠哥伦比亚、 马尼托巴、 新不伦瑞克、 纽芬兰/拉布拉多、 新斯科舍、 安大略、 爱德华王子岛，魁北克和萨斯喀彻温

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_[province_name]_drivers_license_number 找到与该模式匹配的内容。
- 找到 Keyword_[province_name]_drivers_license_name 中的一个关键字。
- 找到 Keyword_canada_drivers_license 中的一个关键字。

```xml
<!-- Canada Driver's License Number -->
    <Entity id="37186abb-8e48-4800-ad3c-e3d1610b3db0" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_alberta_drivers_license_number" />
        <Match idRef="Keyword_alberta_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_british_columbia_drivers_license_number" />
        <Match idRef="Keyword_british_columbia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_manitoba_drivers_license_number" />
        <Match idRef="Keyword_manitoba_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_brunswick_drivers_license_number" />
        <Match idRef="Keyword_new_brunswick_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_newfoundland_labrador_drivers_license_number" />
        <Match idRef="Keyword_newfoundland_labrador_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_nova_scotia_drivers_license_number" />
        <Match idRef="Keyword_nova_scotia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_ontario_drivers_license_number" />
        <Match idRef="Keyword_ontario_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_prince_edward_island_drivers_license_number" />
        <Match idRef="Keyword_prince_edward_island_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_quebec_drivers_license_number" />
        <Match idRef="Keyword_quebec_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_saskatchewan_drivers_license_number" />
        <Match idRef="Keyword_saskatchewan_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_province_name_drivers_license_name"></a>Keyword_ [province_name] _drivers_license_name

- 省/市/自治区的缩写，例如 AB
- 省名称，例如 Alberta

#### <a name="keyword_canada_drivers_license"></a>Keyword_canada_drivers_license

- 通讯
- DLS
- 采用
- CDLS
- DriverLic
- DriverLics
- DriverLicense
- DriverLicenses
- DriverLicence
- DriverLicences
- Driver Lic
- Driver Lics
- Driver License
- Driver Licenses
- Driver Licence
- Driver Licences
- DriversLic
- DriversLics
- DriversLicence
- DriversLicences
- DriversLicense
- DriversLicenses
- Drivers Lic
- Drivers Lics
- Drivers License
- Drivers Licenses
- Drivers Licence
- Drivers Licences
- Driver'Lic
- Driver'Lics
- Driver'License
- Driver'Licenses
- Driver'Licence
- Driver'Licences
- Driver' Lic
- Driver' Lics
- Driver' License
- Driver' Licenses
- Driver' Licence
- Driver' Licences
- Driver'sLic
- Driver'sLics
- Driver'sLicense
- Driver'sLicenses
- Driver'sLicence
- Driver'sLicences
- Driver's Lic
- Driver's Lics
- Driver's License
- Driver's Licenses
- Driver's Licence
- Driver's Licences
- Permis de Conduire
- id
- ids
- idcard number
- idcard numbers
- idcard #
- idcard #s
- idcard card
- idcard cards
- idcard
- identification number
- identification numbers
- identification #
- identification #s
- identification card
- identification cards
- id 
- 通讯#
- DLS# 
- 采用# 
- CDLS# 
- DriverLic# 
- DriverLics# 
- DriverLicense# 
- DriverLicenses# 
- DriverLicence# 
- DriverLicences# 
- Driver Lic#
- Driver Lics# 
- Driver License# 
- Driver Licenses# 
- Driver License# 
- Driver Licences# 
- DriversLic# 
- DriversLics# 
- DriversLicense# 
- DriversLicenses# 
- DriversLicence# 
- DriversLicences# 
- Drivers Lic# 
- Drivers Lics# 
- Drivers License# 
- Drivers Licenses# 
- Drivers Licence# 
- Drivers Licences# 
- Driver'Lic# 
- Driver'Lics# 
- Driver'License# 
- Driver'Licenses# 
- Driver'Licence# 
- Driver'Licences# 
- Driver' Lic# 
- Driver' Lics# 
- Driver' License# 
- Driver' Licenses# 
- Driver' Licence# 
- Driver' Licences# 
- Driver'sLic# 
- Driver'sLics# 
- Driver'sLicense# 
- Driver'sLicenses# 
- Driver'sLicence# 
- Driver'sLicences# 
- Driver's Lic# 
- Driver's Lics# 
- Driver's License# 
- Driver's Licenses# 
- Driver's Licence# 
- Driver's Licences# 
- Permis de Conduire# 
- 号# 
- id# 
- idcard card# 
- idcard cards# 
- idcard# 
- identification card# 
- identification cards# 
- id# 
   
## <a name="canada-health-service-number"></a>加拿大卫生服务号

### <a name="format"></a>Format

10 个数字

### <a name="pattern"></a>模式

10 个数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_canada_health_service_number 找到与该模式匹配的内容。
- 找到 Keyword_canada_health_service_number 中的一个关键字。

```xml
<!-- Canada Health Service Number -->
<Entity id="59c0bf39-7fab-482c-af25-00faa4384c94" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_health_service_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_canada_health_service_number" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_canada_health_service_number"></a>Keyword_canada_health_service_number

- personal health number
- patient information
- health services
- speciality services
- automobile accident
- patient hospital
- psychiatrist
- workers compensation
- 障碍
      
## <a name="canada-passport-number"></a>加拿大护照号码

### <a name="format"></a>Format

两个大写字母后跟六个数字

### <a name="pattern"></a>模式

两个大写字母后跟六个数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_canada_passport_number 找到与该模式匹配的内容。
- 找到 Keyword_canada_passport_number 或 Keyword_passport 中的关键字。

```xml 
<!-- Canada Passport Number -->
<Entity id="14d0db8b-498a-43ed-9fca-f6097ae687eb" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_passport_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_canada_passport_number" />
          <Match idRef="Keyword_passport" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_canada_passport_number"></a>Keyword_canada_passport_number

- canadian citizenship
- canadian passport
- passport application
- passport photos
- certified translator
- canadian citizens
- processing times
- renewal application

#### <a name="keyword_passport"></a>Keyword_passport

- Passport Number
- Passport No
- Passport #
- 登记卡#
- PassportID
- Passportno
- passportnumber
- パスポート
- パスポート番号
- パスポートのNum
- パスポート＃
- Numéro de passeport
- Passeport n °
- Passeport Non
- Passeport #
- Passeport#
- PasseportNon
- Passeportn °
   
## <a name="canada-personal-health-identification-number-phin"></a>加拿大个人健康标识号 (PHIN)

### <a name="format"></a>Format

九个数字

### <a name="pattern"></a>模式

九个数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

DLP 策略75% 确信在300个字符的邻近度内检测到此类型的敏感信息：正则表达式 Regex_canada_phin 找到与该模式匹配的内容。
找到 Keyword_canada_phin 或 Keyword_canada_provinces 中至少有两个关键字。。

```xml
<!-- Canada PHIN -->
<Entity id="722e12ac-c89a-4ec8-a1b7-fea3469f89db" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_phin" />
        <Any minMatches="2">
          <Match idRef="Keyword_canada_phin" />
          <Match idRef="Keyword_canada_provinces" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_canada_phin"></a>Keyword_canada_phin

- social insurance number
- health information act
- income tax information
- manitoba health
- health registration
- prescription purchases
- benefit eligibility
- personal health
- power of attorney
- registration number
- personal health number
- practitioner referral
- wellness professional
- patient referral
- health and wellness

#### <a name="keyword_canada_provinces"></a>Keyword_canada_provinces

- Nunavut
- 省
- Northwest Territories
- 省
- British Columbia
- Alberta
- 彻
- Manitoba
- Yukon
- Newfoundland and Labrador
- New Brunswick
- Nova Scotia
- Prince Edward Island
- 加拿大
   
## <a name="canada-social-insurance-number"></a>加拿大社会保险号码

### <a name="format"></a>Format

九个数字，包含可选连字符或空格

### <a name="pattern"></a>模式

格式
- 三位数字 
- 连字符或空格 
- 三位数字 
- 连字符或空格 
- 三位数字

未格式化：9个数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_canadian_sin 找到与该模式匹配的内容。
- 至少两个以下任意组合：
    - 找到 Keyword_sin 中的一个关键字。
    - 找到 Keyword_sin_collaborative 中的一个关键字。
    - 函数 Func_eu_date 找到正确日期格式的日期。
- 校验和通过。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_unformatted_canadian_sin 找到与该模式匹配的内容。
- 找到 Keyword_sin 中的一个关键字。
- 校验和通过。

```xml
<!-- Canada Social Insurance Number -->
<Entity id="a2f29c85-ecb8-4514-a610-364790c0773e" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_canadian_sin" />
        <Any minMatches="2">
          <Match idRef="Keyword_sin" />
          <Match idRef="Keyword_sin_collaborative" />
          <Match idRef="Func_eu_date" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_canadian_sin" />
        <Match idRef="Keyword_sin" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_sin"></a>Keyword_sin

- sin 
- social insurance 
- numero d'assurance sociale 
- 罪 
- ssn 
- ssn 
- social security 
- numero d'assurance social 
- national identification number 
- national id 
- sin# 
- soc ins 
- social ins 

#### <a name="keyword_sin_collaborative"></a>Keyword_sin_collaborative

- driver's license 
- drivers license 
- driver's licence 
- drivers licence 
- DOB 
- 出生日期 
- 一定 
- Date of Birth 
   
## <a name="chile-identity-card-number"></a>	智利身份证号

### <a name="format"></a>Format

7-8 位数加上分隔符一个校验位或字母

### <a name="pattern"></a>模式

7-8 个数字加分隔符：
- 1-2 个数字  
- 一个点  
- 三个数字  
- 一个点  
- 三个数字  
- 一个短划线  
- 一个数字或字母（不区分大小写），是校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_chile_id_card 找到与该模式匹配的内容。
- 找到 Keyword_chile_id_card 中的一个关键字。
- 校验和通过。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_chile_id_card 找到与该模式匹配的内容。
- 校验和通过。

```xml
<!-- Chile Identity Card Number -->
<Entity id="4e979794-49a0-407e-a0b9-2c536937b925" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_chile_id_card"/>
     <Match idRef="Keyword_chile_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_chile_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_chile_id_card"></a>Keyword_chile_id_card

- National Identification Number 
- Identity card 
- ID 
- Id 
- Rol Único Nacional 
- 以 
- Rol Único Tributario 
- 墨守成规 
- Cédula de Identidad 
- Número De Identificación Nacional 
- Tarjeta de identificación 
- Identificación 
   
## <a name="china-resident-identity-card-prc-number"></a>	中国居民身份证号

### <a name="format"></a>Format

18 个数字

### <a name="pattern"></a>模式

18 个数字：
- 其中六个数字是地址代码  
- 八个数字，采用  YYYYMMDD 格式，代表出生日期  
- 三个数字，是顺序代码  
- 一个数字，是校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_china_resident_id 找到与该模式匹配的内容。
- 找到 Keyword_china_resident_id 中的一个关键字。
- 校验和通过。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_china_resident_id 找到与该模式匹配的内容。
- 校验和通过。

```xml
<!-- China Resident Identity Card (PRC) Number -->
<Entity id="c92daa86-2d16-4871-901f-816b3f554fc1" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_china_resident_id"/>
     <Match idRef="Keyword_china_resident_id"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_china_resident_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

### <a name="keyword_china_resident_id"></a>Keyword_china_resident_id

- Resident Identity Card 
- 台湾 
- National Identification Card 
- 身份证 
- 居民 身份证 
- 居民身份证 
- 鉴定 
- 身分證 
- 居民身份證
- 鑑定 
   
## <a name="credit-card-number"></a>信用卡号

### <a name="format"></a>Format

14到16个数字，可以是格式化或无格式（dddddddddddddddd），并且必须通过 Luhn 测试。

### <a name="pattern"></a>模式

非常复杂且强大的模式，检测到来自世界各地所有重要品牌的卡，包括 Visa、万事达卡、发现卡、JCB卡、美国运通卡、礼品卡以及大莱卡。

### <a name="checksum"></a>校验和

是，Luhn 校验和

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_credit_card 找到与该模式匹配的内容。
- 下列其中一项为真：
    - 找到 Keyword_cc_verification 中的一个关键字。
    - 找到 Keyword_cc_name 中的一个关键字。
    - 函数 Func_expiration_date 找到正确日期格式的日期。
- 校验和通过。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 65% 确信它检测到这种类型的敏感信息：
- 函数 Func_credit_card 找到与该模式匹配的内容。
- 校验和通过。

```xml
<!-- Credit Card Number -->
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
          <Match idRef="Func_expiration_date" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_credit_card" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_cc_verification"></a>Keyword_cc_verification

- card verification
- card identification number
- cvn
- cid
- cvc2
- cvv2
- pin block
- security code
- security number
- security no
- issue number
- issue no
- cryptogramme
- numéro de sécurité
- numero de securite
- kreditkartenprüfnummer
- kreditkartenprufnummer
- prüfziffer
- prufziffer
- sicherheits Kode
- sicherheitscode
- sicherheitsnummer
- verfalldatum
- codice di verifica
- 货. sicurezza
- cod sicurezza
- n autorizzazione
- código
- codigo
- 货. seg
- cod seg
- código de segurança
- codigo de seguranca
- codigo de segurança
- código de seguranca
- cód. segurança
- 货. seguranca 货到付款。 segurança
- cód. seguranca
- cód segurança
- 货到付款 seguranca 货到付款 segurança
- cód seguranca
- número de verificação
- numero de verificacao
- ablauf
- gültig bis
- gültigkeitsdatum
- gultig bis
- gultigkeitsdatum
- scadenza
- data scad
- fecha de expiracion
- fecha de venc
- vencimiento
- válido hasta
- valido hasta
- vto
- data de expiração
- data de expiracao
- data em que expira
- validade
- valor
- vencimento
- Venc 

#### <a name="keyword_cc_name"></a>Keyword_cc_name

- amex
- american express
- americanexpress
- 反之
- mastercard
- Master Card
- emc 
- mastercards
- master cards
- diner's Club
- diners club
- dinersclub
- discover card
- discovercard
- discover cards
- JCB
- japanese card bureau
- carte blanche
- carteblanche
- credit card
- 收件人#
- cc #：
- expiration date
- exp date
- expiry date
- date d’expiration
- date d'exp
- date expiration
- bank card
- bankcard
- card number
- card num
- cardnumber
- cardnumbers
- card numbers
- creditcard
- credit cards
- creditcards
- ccn
- card holder
- 持卡人
- card holders
- cardholders
- check card
- checkcard
- check cards
- checkcards
- debit card
- debitcard
- debit cards
- debitcards
- atm card
- atmcard
- atm cards
- atmcards
- enroute
- en route
- card type
- carte bancaire
- carte de crédit
- carte de credit
- numéro de carte
- numero de carte
- nº de la carte
- nº de carte
- kreditkarte
- karte
- karteninhaber
- karteninhabers
- kreditkarteninhaber
- kreditkarteninstitut
- kreditkartentyp
- eigentümername
- kartennr 
- kartennummer
- kreditkartennummer
- kreditkarten-nummer
- carta di credito
- carta credito
- carta
- n carta
- führerschein-nr. carta
- nr carta
- numero carta
- numero della carta
- numero di carta
- tarjeta credito
- tarjeta de credito
- tarjeta crédito
- tarjeta de crédito
- tarjeta de atm
- tarjeta atm
- tarjeta debito
- tarjeta de debito
- tarjeta débito
- tarjeta de débito
- nº de tarjeta
- 不。 de tarjeta
- no de tarjeta
- numero de tarjeta
- número de tarjeta
- tarjeta no
- tarjetahabiente
- cartão de crédito
- cartão de credito
- cartao de crédito
- cartao de credito
- cartão de débito
- cartao de débito
- cartão de debito
- cartao de debito
- débito automático
- debito automatico
- número do cartão
- numero do cartão 
- número do cartao
- numero do cartao
- número de cartão
- numero de cartão
- número de cartao
- numero de cartao
- nº do cartão
- nº do cartao
- n º。 do cartão
- no do cartão
- no do cartao
- 不。 do cartão
- 不。 do cartao 
   
## <a name="croatia-identity-card-number"></a>	克罗地亚身份证号

### <a name="format"></a>Format

九个数字

### <a name="pattern"></a>模式

九个连续的数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_croatia_id_card 找到与该模式匹配的内容。
- 找到 Keyword_croatia_id_card 中的一个关键字。

```xml
<!--Croatia Identity Card Number-->
<Entity id="ff12f884-c20a-4189-b185-34c8e7258d47" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_croatia_id_card"/>
     <Match idRef="Keyword_croatia_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_croatia_id_card"></a>Keyword_croatia_id_card

- Croatian identity card
- Osobna iskaznica

   
## <a name="croatia-personal-identification-oib-number"></a>	Croatia Personal Identification (OIB) Number

### <a name="format"></a>Format

11 个数字

### <a name="pattern"></a>模式

11 个数字：
- 10 个数字 
- 最后一个数字是用于国际数据交换目的的校验位，字母 HR 将加上11位数字。

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_croatia_oib_number 找到与该模式匹配的内容。
- 找到 Keyword_croatia_oib_number 中的一个关键字。
- 校验和通过。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_croatia_oib_number 找到与该模式匹配的内容。
- 校验和通过。

```xml
<!-- Croatia Personal Identification (OIB) Number -->
<Entity id="31983b6d-db95-4eb2-a630-b44bd091968d" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_croatia_oib_number"/>
     <Match idRef="Keyword_croatia_oib_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_croatia_oib_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_croatia_oib_number"></a>Keyword_croatia_oib_number

- Personal Identification Number
- Osobni identifikacijski broj 
- OIB 

   
## <a name="czech-personal-identity-number"></a>捷克个人识别码

### <a name="format"></a>Format

9个带可选正斜杠（旧格式）的数字，带可选正斜杠的10个数字（新的格式）

### <a name="pattern"></a>模式

9个数字（旧格式）：
- 九个数字

或

- 代表出生日期的六个数字
- 一个正斜杠 
- 三位数字

10个数字（新格式）：
- 10 个数字

或

- 代表出生日期的六个数字
- 一个正斜杠  
- 四个数字，其中最后一个数字是校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

DLP 策略85% 确信在300个字符的邻近度内检测到此类型的敏感信息：函数 Func_czech_id_card 找到与该模式匹配的内容。
找到 Keyword_czech_id_card 中的一个关键字。
校验和通过。

```xml
<!-- Czech Personal Identity Number -->
<Entity id="60c0725a-4eb6-455b-9dda-05d8a7396497"      patternsProximity="300" recommendedConfidence="85">
   <Pattern confidenceLevel="85">
      <IdMatch idRef="Func_czech_id_card" />
      <Match idRef="Keyword_czech_id_card" />
   </Pattern>
</Entity>
```
### <a name="keywords"></a>关键字

- 捷克个人识别码
- Rodné číslo
   
## <a name="denmark-personal-identification-number"></a>	丹麦个人身份号码

### <a name="format"></a>Format

10 个数字，包含连字符

### <a name="pattern"></a>模式

10 个数字：
- 六个数字，采用  DDMMYY 格式，代表出生日期  
- 一个连字符  
- 四个数字，最后一位数字是校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

DLP 策略75% 确信在300个字符的邻近度内检测到此类型的敏感信息：正则表达式 Regex_denmark_id 找到与该模式匹配的内容。
找到 Keyword_denmark_id 中的一个关键字。
校验和通过。

```xml
<!-- Denmark Personal Identification Number -->
<Entity id="6c4f2fef-56e1-4c00-8093-88d7a01cf460" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_denmark_id"/>
     <Match idRef="Keyword_denmark_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_denmark_id"></a>Keyword_denmark_id

- Personal Identification Number
- CPR
- Det Centrale Personregister
- Personnummer
   
## <a name="drug-enforcement-agency-dea-number"></a>药品管制局 (DEA) 号码

### <a name="format"></a>Format

两个字母后跟七个数字

### <a name="pattern"></a>模式

模式必须包括以下各项：
- 这一组可能的字母（不区分大小写）中的一个字母：abcdefghjklmnprstux，这是注册人代码 
- 一个字母（不区分大小写），这是注册人姓氏的第一个字母 
- 七位数字，最后一个数字是校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_dea_number 找到与该模式匹配的内容。
- 校验和通过。

```xml
<!-- DEA Number -->
<Entity id="9a5445ad-406e-43eb-8bd7-cac17ab6d0e4" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_dea_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

无

   
## <a name="eu-debit-card-number"></a>欧盟借记卡号

### <a name="format"></a>Format

16 个数字

### <a name="pattern"></a>模式

非常复杂且强大的模式

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_eu_debit_card 找到与该模式匹配的内容。
- 下列至少其中一项为真：
    - 找到 Keyword_eu_debit_card 中的一个关键字。
    - 找到 Keyword_card_terms_dict 中的一个关键字。
    - 找到 Keyword_card_security_terms_dict 中的一个关键字。
    - 找到 Keyword_card_expiration_terms_dict 中的一个关键字。
    - 函数 Func_expiration_date 找到正确日期格式的日期。
- 校验和通过。

```xml
    <!-- EU Debit Card Number -->
    <Entity id="0e9b3178-9678-47dd-a509-37222ca96b42" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_eu_debit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_eu_debit_card" />
          <Match idRef="Keyword_card_terms_dict" />
          <Match idRef="Keyword_card_security_terms_dict" />
          <Match idRef="Keyword_card_expiration_terms_dict" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_eu_debit_card"></a>Keyword_eu_debit_card

- account number 
- card number 
- card no. 
- security number 
- 收件人# 

#### <a name="keyword_card_terms_dict"></a>Keyword_card_terms_dict

- acct nbr 
- acct num 
- acct no 
- american express 
- americanexpress 
- americano espresso 
- amex 
- atm card 
- atm cards 
- atm kaart 
- atmcard 
- atmcards 
- atmkaart 
- atmkaarten 
- bancontact 
- bank card 
- bankkaart 
- card holder 
- card holders 
- card num 
- card number 
- card numbers 
- card type 
- cardano numerico 
- 持卡人 
- cardholders 
- cardnumber 
- cardnumbers 
- carta bianca 
- carta credito 
- carta di credito 
- cartao de credito 
- cartao de crédito 
- cartao de debito 
- cartao de débito 
- carte bancaire 
- carte blanche 
- carte bleue 
- carte de credit 
- carte de crédit 
- carte di credito 
- carteblanche 
- cartão de credito 
- cartão de crédito 
- cartão de debito 
- cartão de débito 
- cb 
- ccn 
- check card 
- check cards 
- checkcard
- checkcards 
- chequekaart 
- cirrus 
- cirrus-edc-maestro 
- controlekaart 
- controlekaarten 
- credit card 
- credit cards 
- creditcard 
- creditcards 
- debetkaart 
- debetkaarten 
- debit card 
- debit cards 
- debitcard 
- debitcards 
- debito automatico 
- diners club 
- dinersclub 
- 确定 
- discover card 
- discover cards 
- discovercard 
- discovercards 
- débito automático
- edc 
- eigentümername 
- european debit card 
- hoofdkaart 
- hoofdkaarten 
- in viaggio 
- japanese card bureau 
- japanse kaartdienst 
- jcb 
- kaart 
- kaart num 
- kaartaantal 
- kaartaantallen 
- kaarthouder 
- kaarthouders 
- karte  
- karteninhaber 
- karteninhabers
- kartennr 
- kartennummer 
- kreditkarte 
- kreditkarten-nummer 
- kreditkarteninhaber 
- kreditkarteninstitut 
- kreditkartennummer 
- kreditkartentyp 
- maestro 
- Master Card 
- master cards 
- mastercard 
- mastercards 
- emc 
- mister cash 
- n carta 
- carta 
- no de tarjeta 
- no do cartao 
- no do cartão 
- 不。 de tarjeta 
- 不。 do cartao 
- 不。 do cartão 
- nr carta 
- führerschein-nr. carta 
- numeri di scheda 
- numero carta 
- numero de cartao 
- numero de carte 
- numero de cartão 
- numero de tarjeta
- numero della carta 
- numero di carta 
- numero di scheda 
- numero do cartao 
- numero do cartão 
- numéro de carte 
- nº carta 
- nº de carte 
- nº de la carte 
- nº de tarjeta 
- nº do cartao 
- nº do cartão 
- n º。 do cartão 
- número de cartao 
- número de cartão 
- número de tarjeta 
- número do cartao 
- scheda dell'assegno 
- scheda dell'atmosfera 
- scheda dell'atmosfera 
- scheda della banca 
- scheda di controllo 
- scheda di debito 
- scheda matrice 
- schede dell'atmosfera 
- schede di controllo 
- schede di debito 
- schede matrici 
- scoprono la scheda 
- scoprono le schede 
- solo 
- supporti di scheda 
- supporto di scheda 
- 器 
- tarjeta atm 
- tarjeta credito 
- tarjeta de atm 
- tarjeta de credito 
- tarjeta de debito 
- tarjeta debito 
- tarjeta no
- tarjetahabiente 
- tipo della scheda 
- ufficio giapponese della 
- scheda 
- v pay 
- v-支付 
- 反之 
- visa plus 
- visa electron 
- visto 
- visum 
- vpay   

#### <a name="keyword_card_security_terms_dict"></a>Keyword_card_security_terms_dict

- card identification number
- card verification 
- cardi la verifica 
- cid 
- cod seg 
- cod seguranca 
- cod segurança 
- cod sicurezza 
- 货. seg 
- 货. seguranca 
- 货. segurança 
- 货. sicurezza 
- codice di sicurezza 
- codice di verifica 
- codigo 
- codigo de seguranca 
- codigo de segurança 
- crittogramma 
- cryptogram 
- cryptogramme 
- cv2 
- cvc 
- cvc2 
- cvn 
- cvv 
- cvv2 
- cód seguranca 
- cód segurança 
- cód. seguranca 
- cód. segurança 
- código 
- código de seguranca 
- código de segurança 
- de kaart controle 
- geeft nr uit 
- issue no 
- issue number 
- kaartidentificatienummer 
- kreditkartenprufnummer 
- kreditkartenprüfnummer 
- kwestieaantal 
- 不。 dell'edizione 
- 不。 di sicurezza 
- numero de securite 
- numero de verificacao 
- numero dell'edizione 
- numero di identificazione della 
- scheda 
- numero di sicurezza 
- numero van veiligheid 
- numéro de sécurité 
- nº autorizzazione 
- número de verificação 
- perno il blocco 
- pin block 
- prufziffer 
- prüfziffer 
- security code 
- security no 
- security number 
- sicherheits kode 
- sicherheitscode 
- sicherheitsnummer 
- speldblok 
- veiligheid nr 
- veiligheidsaantal 
- veiligheidscode 
- veiligheidsnummer 
- verfalldatum 

#### <a name="keyword_card_expiration_terms_dict"></a>Keyword_card_expiration_terms_dict

- ablauf 
- data de expiracao 
- data de expiração 
- data del exp 
- data di exp 
- data di scadenza 
- data em que expira 
- data scad 
- data scadenza 
- date de validité 
- datum afloop 
- datum van exp 
- de afloop 
- espira 
- espira 
- exp date 
- exp datum 
- 时间 
- 何时 
- 不久 
- 过期 
- fecha de expiracion 
- fecha de venc 
- gultig bis 
- gultigkeitsdatum 
- gültig bis 
- gültigkeitsdatum 
- la scadenza 
- scadenza 
- valable 
- validade 
- valido hasta 
- valor 
- venc 
- vencimento 
- vencimiento 
- verloopt 
- vervaldag 
- vervaldatum 
- vto 
- válido hasta 
   
## <a name="eu-drivers-license-number"></a>欧盟驾驶执照号码

若要了解详细信息，请参阅[EU 驱动程序的许可号敏感信息类型](eu-driver-s-license-number.md)。
  
## <a name="eu-national-identification-number"></a>欧盟国家身份证号

若要了解详细信息，请参阅[EU 国家身份证号敏感信息类型](eu-national-identification-number.md)。
  
## <a name="eu-passport-number"></a>EU 护照号码

若要了解详细信息，请参阅[EU 护照号敏感信息类型](eu-passport-number.md)。
  
## <a name="eu-social-security-number-or-equivalent-id"></a>欧盟社会安全号码或等效 ID

若要了解详细信息，请参阅[EU 社会保险号或等效 ID 敏感信息类型](eu-social-security-number-or-equivalent-id.md)。
  
## <a name="eu-tax-identification-number"></a>EU 税标识号

若要了解详细信息，请参阅[EU 纳税识别号敏感信息类型](eu-tax-identification-number.md)。
  
## <a name="finland-national-id"></a>芬兰国家/地区 ID

### <a name="format"></a>Format

六个数字加一个字符（表示一个世纪），加三个数字再加一个校验位

### <a name="pattern"></a>模式

模式必须包括以下各项：
- 采用 DDMMYY 格式的六位数字，表示出生日期 
- 世纪标记（“-”、“+”或“a”） 
- 三位个人标识号 
- 一个数字或字母（区分大小写），是校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_finnish_national_id 找到与该模式匹配的内容。
- 找到 Keyword_finnish_national_id 中的一个关键字。
- 校验和通过。

```xml
<!-- Finnish National ID-->
<Entity id="338FD995-4CB5-4F87-AD35-79BD1DD926C1" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_finnish_national_id" />
          <Match idRef="Keyword_finnish_national_id" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

- Keyword_finnish_national_id
- Sosiaaliturvatunnus
- SOTU Henkilötunnus HETU
- Personbeteckning
- Personnummer
   
## <a name="finland-passport-number"></a>芬兰护照号

设置九个字母和数字的组合的组合九个字母和数字的组合：两个字母（不区分大小写）七个数字校验和无定义 DLP 策略是75% 确信它检测到这种类型的敏感信息，如果在300个字符的邻近性：正则表达式 Regex_finland_passport_number 找到与该模式匹配的内容。
找到 Keyword_finland_passport_number 中的一个关键字。
<!-- Finland Passport Number -->
<Entity id="d1685ac3-1d3a-40f8-8198-32ef5669c7a5" recommendedConfidence="75" patternsProximity="300"> <Pattern confidenceLevel="75"> <IdMatch idRef="Regex_finland_passport_number"/> <Match idRef="Keyword_finland_passport_number"/> </Pattern>
</Entity>
Keyword_finland_passport_number Passport Passi 的关键字
   
## <a name="france-drivers-license-number"></a>法国驾驶证号码

### <a name="format"></a>Format

12 个数字

### <a name="pattern"></a>模式

12 个数字，会对类似模式（如法国电话号码）进行验证

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_french_drivers_license 找到与该模式匹配的内容。
- 下列至少其中一项为真：
- 找到 Keyword_french_drivers_license 中的一个关键字。
- 函数 Func_eu_date 找到正确日期格式的日期。

```xml
<!-- France Driver's License Number -->
<Entity id="18e55a36-a01b-4b0f-943d-dc10282a1824" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_drivers_license" />
        <Any minMatches="1">
          <Match idRef="Keyword_french_drivers_license" />
          <Match idRef="Func_eu_date" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_french_drivers_license"></a>Keyword_french_drivers_license

- drivers licence
- drivers license
- driving licence
- driving license
- permis de conduire
- licence number
- license number
- licence numbers
- license numbers

## <a name="france-national-id-card-cni"></a>法国国家/地区 ID 卡 (CNI)

### <a name="format"></a>Format

12 个数字

### <a name="pattern"></a>模式

12 个数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 65% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_france_cni 找到与该模式匹配的内容。

```xml
<!-- France CNI -->
<Entity id="f741ac74-1bc0-4665-b69b-f0c7f927c0c4" patternsProximity="300" recommendedConfidence="65">
  <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_france_cni" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

无
   
## <a name="france-passport-number"></a>法国护照号码

### <a name="format"></a>Format

9 个数字和字母

### <a name="pattern"></a>模式

九位数字和字母：
- 两位数字 
- 两个字母（不区分大小写） 
- 五位数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_fr_passport 找到与该模式匹配的内容。
- 找到 Keyword_passport 中的一个关键字。

```xml
<!-- France Passport Number -->
<Entity id="3008b884-8c8c-4cd8-a289-99f34fc7ff5d" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_fr_passport" />
        <Match idRef="Keyword_passport" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_passport"></a>Keyword_passport

- Passport Number
- Passport No
- Passport #
- 登记卡#
- PassportID
- Passportno
- passportnumber
- パスポート
- パスポート番号
- パスポートのNum
- パスポート ＃ 
- Numéro de passeport
- Passeport n °
- Passeport Non
- Passeport #
- Passeport#
- PasseportNon
- Passeportn °

      
## <a name="france-social-security-number-insee"></a>法国社会保险号 (INSEE)

### <a name="format"></a>Format

15 个数字

### <a name="pattern"></a>模式

必须匹配两种模式之一：
- 13位数，后跟一个空格，后跟两个数字<br/>
或
- 15 个连续的数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 95% 确信它检测到这种类型的敏感信息：
- 函数 Func_french_insee 或 Func_fr_insee 找到与该模式匹配的内容。
- 找到 Keyword_fr_insee 中的一个关键字。
- 校验和通过。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_french_insee 或 Func_fr_insee 找到与该模式匹配的内容。
- 未找到 Keyword_fr_insee 中的关键字。
- 校验和通过。

```xml
<!-- France INSEE -->
<Entity id="71f62b97-efe0-4aa1-aa49-e14de253619d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="95">
        <IdMatch idRef="Func_french_insee" />
        <Match idRef="Func_fr_insee" />
        <Any minMatches="1">
          <Match idRef="Keyword_fr_insee" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_french_insee" />
        <Match idRef="Func_fr_insee" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_fr_insee" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_fr_insee"></a>Keyword_fr_insee

- insee
- securité sociale
- securite sociale
- national id
- national identification
- numéro d identité
- no d'identité
- 不。 d'identité
- numero d'identite
- no d'identite
- 不。 d'identite
- social security number
- social security code
- social insurance number
- le numéro d'identification nationale
- d'identité nationale
- numéro de sécurité sociale
- le code de la sécurité sociale
- numéro d'assurance sociale
- numéro de sécu
- code sécu 
   
## <a name="german-drivers-license-number"></a>德国驾驶证号码

### <a name="format"></a>Format

11 个数字和字母组合

### <a name="pattern"></a>模式

11 位数字和字母（不区分大小写）：
- 一个数字或字母 
- 两位数字 
- 六位数字或字母 
- 一位数字 
- 一个数字或字母

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_german_drivers_license 找到与该模式匹配的内容。
- 下列至少其中一项为真：
    - 找到 Keyword_german_drivers_license_number 中的一个关键字。
    - 找到 Keyword_german_drivers_license_collaborative 中的一个关键字。
    - 找到 Keyword_german_drivers_license 中的一个关键字。
- 校验和通过。

```xml
<!-- German Driver's License Number -->
<Entity id="91da9335-1edb-45b7-a95f-5fe41a16c63c" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_drivers_license" />
        <Any minMatches="1">
          <Match idRef="Keyword_german_drivers_license_number" />
          <Match idRef="Keyword_german_drivers_license_collaborative" />
          <Match idRef="Keyword_german_drivers_license" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_german_drivers_license_number"></a>Keyword_german_drivers_license_number

- Führerschein-nr
- Fuhrerschein
- Fuehrerschein
- Führerscheinnummer
- Fuhrerscheinnummer
- Fuehrerscheinnummer
- Führerschein-nr 
- Fuhrerschein- 
- Fuehrerschein- 
- FührerscheinnummerNr
- FuhrerscheinnummerNr
- FuehrerscheinnummerNr
- FührerscheinnummerKlasse
- FuhrerscheinnummerKlasse
- FuehrerscheinnummerKlasse
- Führerschein-Nr
- Fuhrerschein- Nr
- Fuehrerschein- Nr 
- Führerschein- Klasse 
- Fuhrerschein- Klasse 
- Fuehrerschein- Klasse
- FührerscheinnummerNr 
- FuhrerscheinnummerNr 
- FuehrerscheinnummerNr 
- FührerscheinnummerKlasse 
- FuhrerscheinnummerKlasse 
- FuehrerscheinnummerKlasse 
- Führerschein-Nr 
- Fuhrerschein- Nr 
- Fuehrerschein- Nr 
- Führerschein- Klasse 
- Fuhrerschein- Klasse 
- Fuehrerschein- Klasse 
- 通讯 
- DLS
- Driv Lic 
- Driv Licen 
- Driv License
- Driv Licenses 
- Driv Licence 
- Driv Licences 
- Driv Lic 
- Driver Licen 
- Driver License 
- Driver Licenses 
- Driver Licence 
- Driver Licences 
- Drivers Lic 
- Drivers Licen 
- Drivers License 
- Drivers Licenses 
- Drivers Licence 
- Drivers Licences 
- Driver's Lic 
- Driver's Licen 
- Driver's License 
- Driver's Licenses 
- Driver's Licence 
- Driver's Licences 
- Driving Lic 
- Driving Licen 
- Driving License 
- Driving Licenses 
- Driving Licence 
- Driving Licences

#### <a name="keyword_german_drivers_license_collaborative"></a>Keyword_german_drivers_license_collaborative

- Nr-Führerschein-nr 
- Nr-Fuhrerschein 
- Nr-Fuehrerschein 
- Führerschein-nr 
- Fuhrerschein 
- Fuehrerschein 
- N-Führerschein-nr 
- N-Fuhrerschein 
- N-Fuehrerschein
- Nr-Führerschein-nr 
- Nr-Fuhrerschein 
- Nr-Fuehrerschein 
- Führerschein-nr 
- Fuhrerschein 
- Fuehrerschein 
- N-Führerschein-nr 
- N-Fuhrerschein 
- N-Fuehrerschein 

#### <a name="keyword_german_drivers_license"></a>Keyword_german_drivers_license

- ausstellungsdatum
- ausstellungsort
- ausstellende behöde
- ausstellende behorde
- ausstellende behoerde
   
## <a name="german-passport-number"></a>德国护照号码

### <a name="format"></a>Format

10 个数字或字母

### <a name="pattern"></a>模式

模式必须包括以下各项：
- 第一个字符是这一组（C、F、G、H、J、K）中的数字或字母 
- 三位数字 
- 五位数字或字母都来源于这一组（C、-H、J-N、P、R、T，V-Z） 
- 一位数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_german_passport 找到与该模式匹配的内容。
- 找到以下任意五个关键字列表中的关键字。
- 校验和通过。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_german_passport_data 找到与该模式匹配的内容。
- 找到以下任意五个关键字列表中的关键字。
- 校验和通过。

```xml
<!-- German Passport Number -->
<Entity id="2e3da144-d42b-47ed-b123-fbf78604e52c" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_german_passport" />
        <Any minMatches="1">
          <Match idRef="Keyword_german_passport" />
          <Match idRef="Keyword_german_passport_collaborative" />
          <Match idRef="Keyword_german_passport_number" />
          <Match idRef="Keyword_german_passport1" />
          <Match idRef="Keyword_german_passport2" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_passport_data" />
        <Any minMatches="1">
          <Match idRef="Keyword_german_passport" />
          <Match idRef="Keyword_german_passport_collaborative" />
          <Match idRef="Keyword_german_passport_number" />
          <Match idRef="Keyword_german_passport1" />
          <Match idRef="Keyword_german_passport2" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_german_passport"></a>Keyword_german_passport

- reisepass
- reisepasse
- reisepassnummer
- 登记卡
- passports

#### <a name="keyword_german_passport_collaborative"></a>Keyword_german_passport_collaborative

- geburtsdatum
- ausstellungsdatum
- ausstellungsort

#### <a name="keyword_german_passport_number"></a>Keyword_german_passport_number

Reisepass Nr-Reisepass

#### <a name="keyword_german_passport1"></a>Keyword_german_passport1

Reisepass-Nr

#### <a name="keyword_german_passport2"></a>Keyword_german_passport2

bnationalit
   
## <a name="germany-identity-card-number"></a>德国身份证号码

### <a name="format"></a>Format

自2010年11月1日起：九个字母和数字

从1年4月1987至31年10月2010：10位数字

### <a name="pattern"></a>模式

自 2010 年 11 月 1 日起：
- 一个字母（不区分大小写） 
- 八个数字

介于1年4月1987至 31 10 月2010：
- 10 个数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 65% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_germany_id_card 找到与该模式匹配的内容。
- 找到 Keyword_germany_id_card 中的一个关键字。

```xml
<!-- Germany Identity Card Number -->
<Entity id="e577372f-c42e-47a0-9d85-bebed1c237d4" recommendedConfidence="65" patternsProximity="300">
  <Pattern confidenceLevel="65">
     <IdMatch idRef="Regex_germany_id_card"/>
     <Match idRef="Keyword_germany_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_germany_id_card"></a>Keyword_germany_id_card

- Identity Card
- ID
- Id
- Personalausweis
- Identifizierungsnummer
- Ausweis
- Identifikation
   
## <a name="greece-national-id-card"></a>希腊国家 ID 卡

### <a name="format"></a>Format

7-8 个字母和数字组合加一个短划线

### <a name="pattern"></a>模式

七个字母和数字（旧格式）：
- 一个字母（希腊字母表中的任一字母）  
- 一个短划线  
- 六位数字

八个字母和数字（新格式）：
- 大写字符同时出现在希腊和拉丁字母表中的两个字母 (ABEZHIKMNOPTYX)  
- 一个短划线  
- 六位数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_greece_id_card 找到与该模式匹配的内容。
- 找到 Keyword_greece_id_card 中的一个关键字。

```xml
<!-- Greece National ID Card -->
<Entity id="82568215-1da1-46d3-874a-d2294d81b5ac" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_greece_id_card"/>
     <Match idRef="Keyword_greece_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_greece_id_card"></a>Keyword_greece_id_card

- Greek identity Card
- Tautotita
- Δελτίο αστυνομικής ταυτότητας
- Ταυτότητα
   
## <a name="hong-kong-identity-card-hkid-number"></a>香港身份证 (HKID) 号

### <a name="format"></a>Format

8-9 个字母和数字组合，最后一个字符两边可选择加括号

### <a name="pattern"></a>模式

8-9 个字母组合：
- 1-2 个字母（不区分大小写）  
- 六个数字  
- 最后一个字符（任意数字或字母 A）是校验位，两边可以选择加括号。

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_hong_kong_id_card 找到与该模式匹配的内容。
- 找到 Keyword_hong_kong_id_card 中的一个关键字。
- 校验和通过。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 65% 确信它检测到这种类型的敏感信息：
- 函数 Func_hong_kong_id_card 找到与该模式匹配的内容。
- 校验和通过。

```xml
<!-- Hong Kong Identity Card (HKID) number -->
<Entity id="e63c28a7-ad29-4c17-a41a-3d2a0b70fd9c" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_hong_kong_id_card"/>
     <Match idRef="Keyword_hong_kong_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="65">
     <IdMatch idRef="Func_hong_kong_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_hong_kong_id_card"></a>Keyword_hong_kong_id_card

- 中国香港恒等卡片
- HKIDC
- id card
- identity card
- hk identity 卡片
- 香港 id
- 香港身份證
- 香港永久性居民身份證
- 證
- 身份証
- 身分證
- 身分証
- 香港身份証
- 香港身分證
- 香港身分証
- 香港身份證
- 香港居民身份證
- 香港居民身份証
- 香港居民身分證
- 香港居民身分証
- 香港永久性居民身份証
- 香港永久性居民身分證
- 香港永久性居民身分証
- 香港永久性居民身份證
- 香港非永久性居民身份證
- 香港非永久性居民身份証
- 香港非永久性居民身分證
- 香港非永久性居民身分証
- 香港特別行政區永久性居民身份證
- 香港特別行政區永久性居民身份証
- 香港特別行政區永久性居民身分證
- 香港特別行政區永久性居民身分証
- 香港特別行政區非永久性居民身份證
- 香港特別行政區非永久性居民身份証
- 香港特別行政區非永久性居民身分證
- 香港特別行政區非永久性居民身分証
   
## <a name="india-permanent-account-number-pan"></a>印度永久帐号 (PAN)

### <a name="format"></a>Format

10 个字母或数字

### <a name="pattern"></a>模式

10 个字母或数字：
- 五个字母（不区分大小写）  
- 四位数字 
- 一个字母，是字母校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_india_permanent_account_number 找到与该模式匹配的内容。
- 找到 Keyword_india_permanent_account_number 中的一个关键字。
- 校验和通过。

```xml
<!-- India Permanent Account Number -->
<Entity id="2602bfee-9bb0-47a5-a7a6-2bf3053e2804" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_india_permanent_account_number"/>
     <Match idRef="Keyword_india_permanent_account_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_india_permanent_account_number"></a>Keyword_india_permanent_account_number

- Permanent Account Number 
- 蛋糕 
   
## <a name="india-unique-identification-aadhaar-number"></a>India Unique Identification (Aadhaar) Number

### <a name="format"></a>Format

12 个数字（包含可选空格或短划线）

### <a name="pattern"></a>模式

12 个数字：
- 四个数字 
- 一个可选空格或短划线  
- 四个数字 
- 一个可选空格或短划线  
- 最后一个数字是校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

DLP 策略85% 确信在300个字符的邻近度内检测到此类型的敏感信息：函数 Func_india_aadhaar 找到与该模式匹配的内容。
找到 Keyword_india_aadhar 中的一个关键字。
校验和通过。
DLP 策略75% 确信在300个字符的邻近度内检测到此类型的敏感信息：函数 Func_india_aadhaar 找到与该模式匹配的内容。
校验和通过。
```xml
<!-- India Unique Identification (Aadhaar) number -->
<Entity id="1ca46b29-76f5-4f46-9383-cfa15e91048f" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_india_aadhaar"/>
     <Match idRef="Keyword_india_aadhar"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_india_aadhaar"/>
  </Pattern>
</Entity>
```
### <a name="keywords"></a>关键字
   
#### <a name="keyword_india_aadhar"></a>Keyword_india_aadhar
- Aadhar
- Aadhaar
- UID
- आधार
   
## <a name="indonesia-identity-card-ktp-number"></a>印度尼西亚身份证 (KTP) 号

### <a name="format"></a>Format

16 个数字（包含可选点）

### <a name="pattern"></a>模式

16 个数字：
- 两位省代码  
- 一个点（可选）  
- 两位摄政统治区或城市代码  
- 两位住宅小区代码  
- 一个点（可选）  
- 六个数字，采用  DDMMYY 格式，代表出生日期  
- 一个点（可选）  
- 四个数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_indonesia_id_card 找到与该模式匹配的内容。
- 找到 Keyword_indonesia_id_card 中的一个关键字。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_indonesia_id_card 找到与该模式匹配的内容。

```xml
<!-- Indonesia Identity Card (KTP) Number -->
<Entity id="da68fdb0-f383-4981-8c86-82689d3b7d55" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_indonesia_id_card"/>
     <Match idRef="Keyword_indonesia_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_indonesia_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字
   
#### <a name="keyword_indonesia_id_card"></a>Keyword_indonesia_id_card

- KTP
- Kartu Tanda Penduduk 
- Nomor Induk Kependudukan 
   
## <a name="international-banking-account-number-iban"></a>国际银行帐号 (IBAN)

### <a name="format"></a>Format

国家/地区代码（两个字母）加校验位（两个数字）以及 bban 号码（最多 30 个字符）

### <a name="pattern"></a>模式

模式必须包括以下各项：

- 两个字母的国家/地区代码
- 两个校验位（后跟一个可选空间）  
- 1-7 个包含 4 个字母或数字的组（可以使用空格进行分隔）
- 1-3 个字母或数字

每个国家/地区的格式稍有不同。IBAN 敏感信息类型涵盖这 60 个国家/地区：

ad, ae, al, at, az, ba, be, bg, bh, ch, cr, cy, cz, de, dk, do, ee, es, fi, fo, fr, gb, ge, gi, gl, gr, hr, hu, ie, il, is, it, kw, kz, lb, li, lt, lu, lv, mc, md, me, mk, mr, mt, mu, nl, no, pl, pt, ro, rs, sa, se, si, sk, sm, tn, tr, vg

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_iban 找到与该模式匹配的内容。
- 校验和通过。

```xml
<Entity id="e7dc4711-11b7-4cb0-b88b-2c394a771f0e" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_iban" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

无

   
## <a name="ip-address"></a>IP 地址

### <a name="format"></a>Format

#### <a name="ipv4"></a>IPv4
解释 IPv4 地址格式化（点）版本或非格式化（没有点）版本的复杂模式

#### <a name="ipv6"></a>Ipv4
 解释格式化 IPv6 号码（包含冒号）的复杂模式

### <a name="pattern"></a>模式

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

对于 IPv6，在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_ipv6_address 找到与该模式匹配的内容。
- 未找到 Keyword_ipaddress 中的关键字。

对于 IPv4，在 300 个字符的相似度内，如果出现以下情况，DLP 策略 95% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_ipv4_address 找到与该模式匹配的内容。
- 找到 Keyword_ipaddress 中的一个关键字。

对于 IPv6，在 300 个字符的相似度内，如果出现以下情况，DLP 策略 95% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_ipv6_address 找到与该模式匹配的内容。
- 未找到 Keyword_ipaddress 中的关键字。

```xml
    <!-- IP Address -->
    <Entity id="1daa4ad5-e2dd-4ca4-a788-54722c09efb2" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv4_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP（此关键字区分大小写）
- ip address 
- ip addresses
- internet protocol
- IP-כתובת ה 
   
## <a name="international-classification-of-diseases-icd-10-cm"></a>国际分类的 Diseases （ICD-10 CM）

### <a name="format"></a>Format

Dictionary

### <a name="pattern"></a>模式

关键字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 找到 Dictionary_icd_10_updated 中的关键字。
- 找到 Dictionary_icd_10_codes 中的关键字。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 找到 Dictionary_icd_10_ 更新的关键字。

```xml
      <!-- ICD-10 CM -->
      <Entity id="3356946c-6bb7-449b-b253-6ffa419c0ce7" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_10_updated" />
          <Match idRef="Dictionary_icd_10_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_10_updated" />
        </Pattern>

```

关键字

Dictionary_icd_10_updated 关键字词典中的任何术语，基于[国际分类 Diseases，第10次修订，临床修改（icd-10-CM）](https://go.microsoft.com/fwlink/?linkid=852604)。 此类型仅查找术语，而不是保险代码。

Dictionary_icd_10_codes 关键字词典中的任何术语，基于[国际分类 Diseases，第10次修订，临床修改（icd-10-CM）](https://go.microsoft.com/fwlink/?linkid=852604)。 此类型仅查找保险业代码，而不是说明。

## <a name="international-classification-of-diseases-icd-9-cm"></a>国际分类的 Diseases （ICD-9-CM）

### <a name="format"></a>Format

Dictionary

### <a name="pattern"></a>模式

关键字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 找到 Dictionary_icd_9_updated 中的关键字。
- 找到 Dictionary_icd_9_codes 中的关键字。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 找到 Dictionary_icd_9_updated 中的关键字。

```xml
    <Entity id="fa3f9c74-ee07-4c52-b5f2-085d6b2c0ec4" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_9_updated" />
          <Match idRef="Dictionary_icd_9_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_9_updated" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>关键字

Dictionary_icd_9_updated 关键字词典中的任何术语，基于[国际分类的 Diseases，第九个修订，临床修改（icd-9 CM）](https://go.microsoft.com/fwlink/?linkid=852605)。 此类型仅查找术语，而不是保险代码。

Dictionary_icd_9_codes 关键字词典中的任何术语，基于[国际分类的 Diseases，第九个修订，临床修改（icd-9 CM）](https://go.microsoft.com/fwlink/?linkid=852605)。 此类型仅查找保险业代码，而不是说明。

## <a name="ireland-personal-public-service-pps-number"></a>爱尔兰个人公共服务 (PPS) 号码

### <a name="format"></a>Format

旧格式（到 31 Dec 2012）：
- 七位数字后跟 1-2  个字母  

新格式（2013年1月1日和之后）：
- 七位数字后跟两个字母

### <a name="pattern"></a>模式

旧格式（到 31 Dec 2012）：
- 七个数字  
- 1-2 个字母（不区分大小写）  

新格式（2013年1月1日和之后）：
- 七个数字  
- 一个字母（不区分大小写），是字母校验位  
- 字母“A”或“H”（不区分大小写）

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_ireland_pps 找到与该模式匹配的内容。
- 下列其中一项为真：
    - 找到 Keyword_ireland_pps 中的一个关键字。
    - 函数 Func_eu_date 找到正确日期格式的日期。
- 校验和通过。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 65% 确信它检测到这种类型的敏感信息：
- 函数 Func_ireland_pps 找到与该模式匹配的内容。
- 校验和通过。

```xml
<!-- Ireland Personal Public Service (PPS) Number -->
<Entity id="1cdb674d-c19a-4fcf-9f4b-7f56cc87345a" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_ireland_pps"/>
     <Any minMatches="1">
  <Match idRef="Keyword_ireland_pps"/>
  <Match idRef="Func_eu_date"/>
     </Any>
  </Pattern>
  <Pattern confidenceLevel="65">
     <IdMatch idRef="Func_ireland_pps"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_ireland_pps"></a>Keyword_ireland_pps

- Personal Public Service Number 
- PPS Number 
- PPS Num 
- PPS No. 
- PPS # 
- .PPS# 
- PPSN 
- Public Services Card 
- Uimhir Phearsanta Seirbhíse Poiblí 
- Uimh. PSP 
- PSP 
   
## <a name="israel-bank-account-number"></a>以色列银行帐号

### <a name="format"></a>Format

13 位数字

### <a name="pattern"></a>模式

格式
- 两位数字 
- 破折号 
- 三位数字 
- 破折号 
- 八位数字

纯
- 	13 个连续的数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_israel_bank_account_number 找到与该模式匹配的内容。
- 找到 Keyword_israel_bank_account_number 中的一个关键字。

```xml
<!-- Israel Bank Account Number -->
<Entity id="7d08b2ff-a0b9-437f-957c-aeddbf9b2b25" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_israel_bank_account_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_israel_bank_account_number" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_israel_bank_account_number"></a>Keyword_israel_bank_account_number

- Bank Account Number 
- Bank Account 
- Account Number 
- מספר חשבון בנק 
   
## <a name="israel-national-id"></a>以色列国家/地区 ID

### <a name="format"></a>Format

九个数字

### <a name="pattern"></a>模式

九个连续的数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_israeli_national_id_number 找到与该模式匹配的内容。
- 找到 Keyword_Israel_National_ID 中的一个关键字。
- 校验和通过。

```xml
<!-- Israel National ID Number -->
<Entity id="e05881f5-1db1-418c-89aa-a3ac5c5277ee" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_israeli_national_id_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_Israel_National_ID" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_israel_national_id"></a>Keyword_Israel_National_ID

- מספר זהות 
- National ID Number
   
## <a name="italy-drivers-license-number"></a>意大利驾驶证号码

### <a name="format"></a>Format

10 个字母和数字的组合

### <a name="pattern"></a>模式

- 10 个字母和数字的组合：
- 一个字母（不区分大小写） 
- 字母“A”或者“V”（不区分大小写） 
- 七个字母（不区分大小写）、数字或下划线字符 
- 一个字母（不区分大小写）

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_italy_drivers_license_number 找到与该模式匹配的内容。
- 找到 Keyword_italy_drivers_license_number 中的一个关键字。

```xml
<!-- Italy Driver's license Number -->
<Entity id="97d6244f-9157-41bd-8e0c-9d669a5c4d71" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_italy_drivers_license_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_italy_drivers_license_number" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_italy_drivers_license_number"></a>Keyword_italy_drivers_license_number

- numero di patente di guida 
- patente di guida 
   
## <a name="japan-bank-account-number"></a>日本银行帐号

### <a name="format"></a>Format

七个或八个数字

### <a name="pattern"></a>模式

银行帐号：
- 七个或八个数字
- 银行帐户分支代码：
- 四位数字 
- 空格或破折号（可选） 
- 三位数字

校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_jp_bank_account 找到与该模式匹配的内容。
- 找到 Keyword_jp_bank_account 中的一个关键字。
- 下列其中一项为真：
- 函数 Func_jp_bank_account_branch_code 找到与该模式匹配的内容。
- 找到 Keyword_jp_bank_branch_code 中的一个关键字。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_jp_bank_account 找到与该模式匹配的内容。
- 找到 Keyword_jp_bank_account 中的一个关键字。

```xml
<!-- Japan Bank Account Number -->
<Entity id="d354f95b-96ee-4b80-80bc-4377312b55bc" patternsProximity="300" recommendedConfidence="75">
  <Version minEngineVersion="15.01.0131.000">
    <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_jp_bank_account" />
          <Match idRef="Keyword_jp_bank_account" />
          <Any minMatches="1">
            <Match idRef="Func_jp_bank_account_branch_code" />
            <Match idRef="Keyword_jp_bank_branch_code" />
          </Any>
      </Pattern>
  </Version>    
     <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_bank_account" />
        <Match idRef="Keyword_jp_bank_account" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_jp_bank_account"></a>Keyword_jp_bank_account

- Checking Account Number 
- Checking Account 
- Checking Account # 
- Checking Acct Number 
- Checking Acct # 
- Checking Acct No. 
- Checking Account No. 
- Bank Account Number 
- Bank Account 
- Bank Account # 
- Bank Acct Number 
- Bank Acct # 
- Bank Acct No. 
- Bank Account No. 
- Savings Account Number 
- Savings Account 
- Savings Account # 
- Savings Acct Number 
- Savings Acct # 
- Savings Acct No. 
- Savings Account No. 
- Debit Account Number 
- Debit Account 
- Debit Account # 
- Debit Acct Number 
- Debit Acct # 
- Debit Acct No. 
- Debit Account No. 
- 口座番号を当座預金口座の確認 
- #アカウントの確認、勘定番号の確認 
- #勘定の確認 
- 勘定番号の確認 
- 口座番号の確認 
- 銀行口座番号 
- 銀行口座 
- 銀行口座＃ 
- 銀行の勘定番号 
- 銀行のacct＃ 
- 銀行の勘定いいえ 
- 銀行口座番号
- 普通預金口座番号 
- 預金口座 
- 貯蓄口座＃ 
- 貯蓄勘定の数 
- 貯蓄勘定＃ 
- 貯蓄勘定番号 
- 普通預金口座番号 
- 引き落とし口座番号 
- 口座番号 
- 口座番号＃ 
- デビットのacct番号 
- デビット勘定＃ 
- デビットACCTの番号 
- デビット口座番号 

#### <a name="keyword_jp_bank_branch_code"></a>Keyword_jp_bank_branch_code

Otemachi

## <a name="japan-drivers-license-number"></a>日本驾驶证号码

### <a name="format"></a>Format

12 个数字

### <a name="pattern"></a>模式

12 个连续的数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_jp_drivers_license_number 找到与该模式匹配的内容。
- 找到 Keyword_jp_drivers_license_number 中的一个关键字。

```xml
<!-- Japan Driver's License Number -->
<Entity id="c6011143-d087-451c-8313-7f6d4aed2270" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_drivers_license_number" />
        <Match idRef ="Keyword_jp_drivers_license_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_jp_drivers_license_number"></a>Keyword_jp_drivers_license_number

- 通讯# 
- 通讯 
- dls# 
- DLS 
- driver license 
- driver licenses 
- drivers license 
- driver's license 
- drivers licenses 
- driver's licenses 
- driving licence 
- .lic# 
- .LIC 
- driver'lics# 
- state id 
- state identification 
- state identification number 
- 低所得国＃ 
- 免許証 
- 状態ID
- 状態の識別 
- 状態の識別番号 
- 運転免許 
- 運転免許証 
- 運転免許証番号 
   
## <a name="japan-passport-number"></a>日本护照号码

### <a name="format"></a>Format

两个字母后跟七个数字

### <a name="pattern"></a>模式

两个字母（不区分大小写）后跟七个数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_jp_passport 找到与该模式匹配的内容。
- 找到 Keyword_jp_passport 中的一个关键字。

```xml
<!-- Japan Passport Number -->
<Entity id="75177310-1a09-4613-bf6d-833aae3743f8" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_passport" />
        <Match idRef="Keyword_jp_passport" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_jp_passport"></a>Keyword_jp_passport

- パスポート 
- パスポート番号 
- パスポートのNum 
- パスポート＃ 
   
## <a name="japan-resident-registration-number"></a>日本居民登记号码

### <a name="format"></a>Format

11 个数字

### <a name="pattern"></a>模式

11 个连续的数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_jp_resident_registration_number 找到与该模式匹配的内容。
- 找到 Keyword_jp_resident_registration_number 中的一个关键字。

```xml
<!-- Japan Resident Registration Number -->
<Entity id="01c1209b-6389-4faf-a5f8-3f7e13899652" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_resident_registration_number" />
        <Match idRef ="Keyword_jp_resident_registration_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_jp_resident_registration_number"></a>Keyword_jp_resident_registration_number

- Resident Registration Number
- Resident Register Number 
- Residents Basic Registry Number 
- Resident Registration No. 
- Resident Register No. 
- Residents Basic Registry No. 
- Basic Resident Register No. 
- 住民登録番号、登録番号をレジデント 
- 住民基本登録番号、登録番号 
- 住民基本レジストリ番号を常駐 
- 登録番号を常駐住民基本台帳登録番号 

   
## <a name="japan-social-insurance-number-sin"></a>日本社会保险号码 (SIN)

### <a name="format"></a>Format

7-12 个数字 

### <a name="pattern"></a>模式

7-12 位数字：
- 四位数字 
- 一个连字符（可选） 
- 六位数字或
- 7-12 个连续的数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_jp_sin 找到与该模式匹配的内容。
- 找到 Keyword_jp_sin 中的一个关键字。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_jp_sin_pre_1997 找到与该模式匹配的内容。
- 找到 Keyword_jp_sin 中的一个关键字。

```xml
<!-- Japan Social Insurance Number -->
<Entity id="c840e719-0896-45bb-84fd-1ed5c95e45ff" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_jp_sin" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_sin_pre_1997" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_jp_sin"></a>Keyword_jp_sin

- Social Insurance No. 
- Social Insurance Num 
- Social Insurance Number 
- 社会保険のテンキー 
- 社会保険番号 

## <a name="japanese-residence-card-number"></a>日本住宅电话卡号

### <a name="format"></a>Format

12个字母和数字

### <a name="pattern"></a>模式

12个字母和数字：
- 两个字母（不区分大小写） 
- 八个数字 
- 两个字母（不区分大小写） 

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_jp_residence_card_number 找到与该模式匹配的内容。
- 找到 Keyword_jp_residence_card_number 中的关键字。

```xml
<!--Japan Residence Card Number-->
-<Entity id="ac36fef2-a289-4e2c-bb48-b02366e89fc0" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_jp_residence_card_number"/>
      <Match idRef="Keyword_jp_residence_card_number"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_jp_residence_card_number"></a>Keyword_jp_residence_card_number

- 住宅电话卡号
- 住宅卡编号
- 住宅卡片#
- 在留カード番号
   
## <a name="malaysia-id-card-number"></a>马拉西亚身份证号码

### <a name="format"></a>Format

12 个数字（包含可选连字符）

### <a name="pattern"></a>模式

12 个数字：
- 六个数字，采用  YYMMDD 格式，代表出生日期  
- 一个短划线（可选）  
- 两个字母的出生地代码  
- 一个短划线（可选）  
- 三个随机数字  
- 一位性别代码

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_malaysia_id_card_number 找到与该模式匹配的内容。
- 找到 Keyword_malaysia_id_card_number 中的一个关键字。

```xml
<!-- Malaysia ID Card Number -->
</Entity>
      <Entity id="7f0e921c-9677-435b-aba2-bb8f1013c749" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
            <IdMatch idRef="Regex_malaysia_id_card_number" />
            <Match idRef="Keyword_malaysia_id_card_number" />
        </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字
   
#### <a name="keyword_malaysia_id_card_number"></a>Keyword_malaysia_id_card_number

- 数字应用程序卡
- i/c
- i/c 否
- ic
- 内部公司编号
- id card
- 标识卡
- identity card
- k/p
- k/p no
- kad akuan diri
- kad aplikasi 数字
- kad pengenalan 马来西亚
- kp
- kp no
- mykad
- mykas
- mykid
- mypr
- mytentera
- 马来西亚身份卡片
- 马来西亚身份卡片
- nric
- 个人标识卡
   
## <a name="netherlands-citizens-service-bsn-number"></a>荷兰公民服务 (BSN) 号码

### <a name="format"></a>Format

8-9 个数字（包含可选空格）

### <a name="pattern"></a>模式

8-9 个数字：
- 三个数字  
- 一个空格（可选）  
- 三个数字  
- 一个空格（可选）  
- 2-3 个数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_netherlands_bsn 找到与该模式匹配的内容。
- 找到 Keyword_netherlands_bsn 中的一个关键字。
- 函数 Func_eu_date2 找到正确日期格式的日期。
- 校验和通过。

```xml
<!-- Netherlands Citizen's Service (BSN) Number -->
<Entity id="c5f54253-ef7e-44f6-a578-440ed67e946d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
       <IdMatch idRef="Func_netherlands_bsn" /> 
       <Match idRef="Keyword_netherlands_bsn" /> 
       <Match idRef="Func_eu_date2" /> 
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_netherlands_bsn"></a>Keyword_netherlands_bsn

- Citizen service number 
- BSN 
- Burgerservicenummer 
- Sofinummer 
- Persoonsgebonden nummer 
- Persoonsnummer    

   
## <a name="new-zealand-ministry-of-health-number"></a>新西兰卫生部号码

### <a name="format"></a>Format

三个字母、一个空格（可选）以及四个数字

### <a name="pattern"></a>模式

三个字母（不区分大小写）一个空格（可选）四个数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_new_zealand_ministry_of_health_number 找到与该模式匹配的内容。
- 找到 Keyword_nz_terms 中的一个关键字。
- 校验和通过。

```xml
<!-- New Zealand Health Number -->
<Entity id="2b71c1c8-d14e-4430-82dc-fd1ed6bf05c7" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_new_zealand_ministry_of_health_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_nz_terms" />
        </Any>
    </Pattern>
</Entity>
```

关键字

Keyword_nz_terms

- NHI 
- New Zealand 
- 运行状况 
- 治疗 
   
## <a name="norway-identification-number"></a>挪威身份证号

### <a name="format"></a>Format

11 个数字

### <a name="pattern"></a>模式

11 个数字：
- 六个数字，采用  DDMMYY 格式，代表出生日期  
- 三位个人号码  
- 两个校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_norway_id_number 找到与该模式匹配的内容。
- 找到 Keyword_norway_id_number 中的一个关键字。
- 校验和通过。
- 在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_norway_id_numbe 找到与该模式匹配的内容。
- 校验和通过。

```xml
<!-- Norway Identification Number -->
<Entity id="d4c8a798-e9f2-4bd3-9652-500d24080fc3" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_norway_id_number"/>
     <Match idRef="Keyword_norway_id_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_norway_id_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_norway_id_number"></a>Keyword_norway_id_number

- Personal identification number
- Norwegian ID Number
- ID Number
- Id
- Personnummer
- Fødselsnummer

   
## <a name="philippines-unified-multi-purpose-id-number"></a>菲律宾统一多用途身份证号码

### <a name="format"></a>Format

12 个数字，通过连字符分隔 

### <a name="pattern"></a>模式

12 个数字：
- 四个数字 
- 一个连字符  
- 七个数字  
- 一个连字符  
- 一个数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_philippines_unified_id 找到与该模式匹配的内容。
- 找到 Keyword_philippines_id 中的一个关键字。

```xml
<!-- Philippines Unified Multi-Purpose ID number -->
<Entity id="019b39dd-8c25-4765-91a3-d9c6baf3c3b3" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_philippines_unified_id"/>
     <Match idRef="Keyword_philippines_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字
   
#### <a name="keyword_philippines_id"></a>Keyword_philippines_id

- Unified Multi-Purpose ID 
- UMID 
- Identity Card 
- Pinag-isang Multi-Layunin ID
   
## <a name="poland-identity-card"></a>波兰身份证

### <a name="format"></a>Format

三个字母和六个数字

### <a name="pattern"></a>模式

三个字母（不区分大小写）后跟六个数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

DLP 策略75% 确信在300个字符的邻近度内检测到此类型的敏感信息：函数 Func_polish_national_id 找到与该模式匹配的内容。
找到 Keyword_polish_national_id_passport_number 中的一个关键字。
校验和通过。

```xml
<!-- Poland Identity Card-->
<Entity id="25E64989-ED5D-40CA-A939-6C14183BB7BF" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_national_id" />
          <Match idRef="Keyword_polish_national_id_passport_number" />
      </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_polish_national_id_passport_number"></a>Keyword_polish_national_id_passport_number

- Dowód osobisty
- 器 dowodu osobistego
- Nazwa i 器 dowodu osobistego
- Nazwa i nr dowodu osobistego
- Nazwa i nr dowodu tożsamości
- Dowód Tożsamości
- dow. os.

   
## <a name="poland-national-id-pesel"></a>波兰国家/地区 ID (PESEL)

### <a name="format"></a>Format

11 个数字

### <a name="pattern"></a>模式

11 个连续的数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_pesel_identification_number 找到与该模式匹配的内容。
- 找到 Keyword_pesel_identification_number 中的一个关键字。
- 校验和通过。

```xml
<!-- Poland National ID (PESEL) -->      
<Entity id="E3AAF206-4297-412F-9E06-BA8487E22456" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_pesel_identification_number" />
          <Match idRef="Keyword_pesel_identification_number" />
      </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_pesel_identification_number"></a>Keyword_pesel_identification_number

- Nr PESEL
- PESEL   

   
## <a name="poland-passport"></a>波兰护照

### <a name="format"></a>Format

两个字母和七个数字

### <a name="pattern"></a>模式

两个字母（不区分大小写）后跟七个数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_polish_passport_number 找到与该模式匹配的内容。
- 找到 Keyword_polish_national_id_passport_number 中的一个关键字。
- 校验和通过。

```xml
<!-- Poland Passport Number -->
<Entity id="03937FB5-D2B6-4487-B61F-0F8BFF7C3517" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_passport_number" />
          <Match idRef="Keyword_polish_national_id_passport_number" />
      </Pattern>
</Entity>
</Version>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_polish_national_id_passport_number"></a>Keyword_polish_national_id_passport_number

- 器 paszportu
- Führerschein-nr. Paszportu
- Paszport

   
## <a name="portugal-citizen-card-number"></a>葡萄牙公民身份证号

### <a name="format"></a>Format

八个数字

### <a name="pattern"></a>模式

八个数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_portugal_citizen_card 找到与该模式匹配的内容。
- 找到 Keyword_portugal_citizen_card 中的一个关键字。

```xml
<!-- Portugal Citizen Card Number -->
<Entity id="91a7ece2-add4-4986-9a15-c84544d81ecd" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_portugal_citizen_card"/>
     <Match idRef="Keyword_portugal_citizen_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_portugal_citizen_card"></a>Keyword_portugal_citizen_card

- Citizen Card
- National ID Card
- CC
- Cartão de Cidadão
- Bilhete de Identidade
   
## <a name="saudi-arabia-national-id"></a>沙特阿拉伯国家 ID

### <a name="format"></a>Format

10 个数字

### <a name="pattern"></a>模式

10 个连续的数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_saudi_arabia_national_id 找到与该模式匹配的内容。
- 找到 Keyword_saudi_arabia_national_id 中的一个关键字。

```xml
<!-- Saudi Arabia National ID -->
<Entity id="8c5a0ba8-404a-41a3-8871-746aa21ee6c0" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_saudi_arabia_national_id" />
        <Any minMatches="1">
          <Match idRef="Keyword_saudi_arabia_national_id" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_saudi_arabia_national_id"></a>Keyword_saudi_arabia_national_id

- Identification Card 
- I card number 
- ID number 
- الوطنية الهوية بطاقة رقم 

   
## <a name="singapore-national-registration-identity-card-nric-number"></a>新加坡国家登记身份证 (NRIC) 号

### <a name="format"></a>Format

九个字母和数字

### <a name="pattern"></a>模式

- 九个字母和数字：
- 字母“F”、“G”、“S”或“T”（不区分大小写）  
- 七个数字  
- 一个字母校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_singapore_nric 找到与该模式匹配的内容。
- 找到 Keyword_singapore_nric 中的一个关键字。
- 校验和通过。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_singapore_nric 找到与该模式匹配的内容。
- 校验和通过。

```xml
<!-- Singapore National Registration Identity Card (NRIC) Number -->
<Entity id="cead390a-dd83-4856-9751-fb6dc98c34da" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_singapore_nric"/>
     <Match idRef="Keyword_singapore_nric"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_singapore_nric"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字
   
#### <a name="keyword_singapore_nric"></a>Keyword_singapore_nric

- National Registration Identity Card 
- Identity Card Number 
- NRIC 
- IC 
- Foreign Identification Number 
- FIN 
- 身份证 
- 證 
   
## <a name="south-africa-identification-number"></a>南非身份证号

### <a name="format"></a>Format

13 个数字（可能包含空格）

### <a name="pattern"></a>模式

13 个数字：
- 六个数字，采用  YYMMDD 格式，代表出生日期  
- 四个数字 
- 一位公民指示码  
- 数字“8”或“9”  
- 一个数字，是校验位

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_south_africa_identification_number 找到与该模式匹配的内容。
- 找到 Keyword_south_africa_identification_number 中的一个关键字。
- 校验和通过。

```xml
<!-- South Africa Identification Number -->
<Entity id="e2adf7cb-8ea6-4048-a2ed-d89eb65f2780" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_africa_identification_number"/>
     <Match idRef="Keyword_south_africa_identification_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字
   
#### <a name="keyword_south_africa_identification_number"></a>Keyword_south_africa_identification_number

- Identity card
- ID
- Id 
   
## <a name="south-korea-resident-registration-number"></a>韩国居民注册号码

### <a name="format"></a>Format

13 个数字（包含连字符）

### <a name="pattern"></a>模式

13 个数字：
- 六个数字，采用  YYMMDD 格式，代表出生日期  
- 一个连字符  
- 一个数字，由世纪和性别  
- 四位数字的出生地区代码  
- 一个数字，用于区分前面数字均相同的人  
- 一个校验位。

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_south_korea_resident_number 找到与该模式匹配的内容。
- 找到 Keyword_south_korea_resident_number 中的一个关键字。
- 校验和通过。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_south_korea_resident_number 找到与该模式匹配的内容。
- 校验和通过。

```xml
<!-- South Korea Resident Registration Number -->
<Entity id="5b802e18-ba80-44c4-bc83-bf2ad36ae36a" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_korea_resident_number"/>
     <Match idRef="Keyword_south_korea_resident_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_south_korea_resident_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字
   
#### <a name="keyword_south_korea_resident_number"></a>Keyword_south_korea_resident_number

- National ID card 
- Citizen's Registration Number 
- Jumin deungnok beonho 
- RRN 
- 주민등록번호
   
## <a name="spain-social-security-number-ssn"></a>西班牙社会保险号码 (SSN)

### <a name="format"></a>Format

11-12 个数字

### <a name="pattern"></a>模式

11-12 位数：
- 两位数字 
- 正斜杠（可选） 
- 7-8 位数字 
- 正斜杠（可选） 
- 两位数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_spanish_social_security_number 找到与该模式匹配的内容。
- 校验和通过。

```xml
<!-- Spain SSN -->
<Entity id="5df987c0-8eae-4bce-ace7-b316347f3070" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_spanish_social_security_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

无

## <a name="sql-server-connection-string"></a>SQL Server 连接字符串

### <a name="format"></a>Format

字符串 "User Id"、"User ID"、"uid" 或 "UserId"，后跟下面模式中所述的字符和字符串。

### <a name="pattern"></a>模式

- 字符串 "User Id"、"User ID"、"uid" 或 "UserId"
- 介于1-200 个字母、数字、符号、特殊字符或空格之间的任意组合
- 字符串 "Password" 或 "pwd"，其中 "pwd" 不以小写字母开头
- 等号（=）
- 任何不是美元符号（$）、百分比符号（%）、大于号（>）、符号（@）、引号（"）、分号（;)、左大括号（[）或左中括号（{）的字符
- 7-128 个字符的任意组合，不是分号（;)、正斜杠（/）或引号（"）
- 一个分号（;)或引号（"）

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 正则表达式 CEP_Regex_SQLServerConnectionString 找到与该模式匹配的内容。
- 找**不**到 CEP_GlobalFilter 中的关键字。
- 正则表达式**CEP_PasswordPlaceHolder 不会找到与**该模式匹配的内容。
- 正则表达式**CEP_CommonExampleKeywords 不会找到与**该模式匹配的内容。

```sql
<!---SQL Server Connection String>
<Entity id="e76b6205-d3cb-46f2-bd63-c90153f2f97d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_SQLServerConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_GlobalFilter" />
            <Match idRef="CEP_PasswordPlaceHolder" />
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="cep_globalfilter"></a>CEP_GlobalFilter

- 部分密码
- somepassword
- secretPassword
- 采用

#### <a name="cep_passwordplaceholder"></a>CEP_PasswordPlaceHolder

（请注意，从技术上讲，此敏感信息类型通过使用正则表达式（而不是关键字列表）来标识这些关键字。

- 密码或密码后跟0-2 个空格、一个等号（=）、0-2 个空格和一个星号（*）--或--
- 密码或密码后跟：
    - 等号（=）
    - 小于号（<）
    - 1-200 个字符的任意组合，这些字符为大写或小写字母、数字、星号（*）、连字符（-）、下划线（_）或空白字符
    - 大于号（>）

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

（请注意，从技术上讲，此敏感信息类型通过使用正则表达式（而不是关键字列表）来标识这些关键字。

- 尚未
- 送交
- 罗斯
- 沙盒
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int。<!--no-hyperlink-->netmeeting

## <a name="sweden-national-id"></a>瑞典国家 ID

### <a name="format"></a>Format

10 个或 12 个数字和一个可选分隔符

### <a name="pattern"></a>模式

10 或 12 位数字和可选的分隔符：
- 2-4 位数字（可选） 
- 采用日期格式 YYMMDD 的六位数字 
- “-”或“+”（可选）的分隔符，加
- 四个数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_swedish_national_identifier 找到与该模式匹配的内容。
- 校验和通过。

```xml
<!-- Sweden National ID -->
<Entity id="f69aaf40-79be-4fac-8f05-fd1910d272c8" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_swedish_national_identifier" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

否
   
## <a name="sweden-passport-number"></a>瑞典护照号码

### <a name="format"></a>Format

八个数字

### <a name="pattern"></a>模式

八个连续的数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_sweden_passport_number 找到与该模式匹配的内容。
- 下列其中一项为真：
    - 找到 Keyword_passport 中的一个关键字。
    - 找到 Keyword_sweden_passport 中的一个关键字。

```xml
<!-- Sweden Passport Number -->
<Entity id="ba4e7456-55a9-4d89-9140-c33673553526" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_sweden_passport_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_passport" />
          <Match idRef="Keyword_sweden_passport" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字
   
#### <a name="keyword_sweden_passport"></a>Keyword_sweden_passport

- visa requirements 
- Alien Registration Card 
- Schengen visas 
- Schengen visa 
- Visa Processing 
- Visa Type 
- Single Entry 
- Multiple Entry 
- G3 Processing Fees 

#### <a name="keyword_passport"></a>Keyword_passport

- Passport Number 
- Passport No 
- Passport # 
- 登记卡# 
- PassportID 
- Passportno 
- passportnumber 
- パスポート 
- パスポート番号 
- パスポートのNum 
- パスポート＃ 
- Numéro de passeport 
- Passeport n ° 
- Passeport Non 
- Passeport # 
- Passeport# 
- PasseportNon 
- Passeportn ° 
   
## <a name="swift-code"></a>SWIFT 代码

### <a name="format"></a>Format

四个字母后跟 5-31 个字母或数字

### <a name="pattern"></a>模式

四个字母后跟 5-31 个字母或数字：
- 四个字母的银行代码（不区分大小写） 
- 可选空格 
- 4-28 个字母或数字（基本银行账号 (BBAN)） 
- 可选空格 
- 1-3 个字母或数字（BBAN 的剩余内容）

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_swift 找到与该模式匹配的内容。
- 找到 Keyword_swift 中的一个关键字。

```xml
<Entity id="cb2ab58c-9cb8-4c81-baf8-a4e106791df4" patternsProximity="300" recommendedConfidence="75">
<Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_swift" />
        <Match idRef="Keyword_swift" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字
   
#### <a name="keyword_swift"></a>Keyword_swift

- international organization for standardization 9362 
- iso 9362 
- iso9362 
- 反应\# 
- swiftcode 
- swiftnumber 
- swiftroutingnumber 
- swift code 
- swift number # 
- swift routing number 
- bic number 
- bic code 
- numéro\# 
- numéro\# 
- bank identifier code 
- 標準化9362 
- 迅速＃ 
- SWIFTコード 
- SWIFT番号 
- 迅速なルーティング番号 
- BIC番号 
- BICコード 
- 銀行識別コードのための国際組織 
- Organisation internationale de normalisation 9362 
- rapide\# 
- code SWIFT 
- le numéro de swift 
- swift numéro d'acheminement 
- le numéro BIC 
- \#NUMÉRO 
- code identificateur de banque 
   
## <a name="taiwan-national-id"></a>台湾国家/地区 ID

### <a name="format"></a>Format

一个字母后跟九个数字

### <a name="pattern"></a>模式

一个字母后跟 9 位数字：
- 一个字母（英文，不区分大小写） 
- 数字“1”或“2” 
- 八位数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_taiwanese_national_id 找到与该模式匹配的内容。
- 找到 Keyword_taiwanese_national_id 中的一个关键字。
- 校验和通过。

```xml
<!-- Taiwanese National ID -->
<Entity id="4C7BFC34-8DD1-421D-8FB7-6C6182C2AF03" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_taiwanese_national_id" />
          <Match idRef="Keyword_taiwanese_national_id" />
      </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_taiwanese_national_id"></a>Keyword_taiwanese_national_id

- 身份證字號 
- 證 
- 身份證號碼 
- 身份證號 
- 身分證字號 
- 身分證 
- 身分證號碼 
- 身份證號 
- 身分證統一編號 
- 國民身分證統一編號 
- 簽名 
- 蓋章 
- 簽名或蓋章 
- 簽章   
   
## <a name="taiwan-passport-number"></a>	台湾护照号码

### <a name="format"></a>Format

- 生物识别护照号码：9个数字
- 不带生物的护照号码：9个数字

### <a name="pattern"></a>模式
生物识别护照号码：
- 数字“3”  
- 八个数字

不带生物的护照号码：
- 九个数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_taiwan_passport 找到与该模式匹配的内容。
- 找到 Keyword_taiwan_passport 中的一个关键字。

```xml
<!-- Taiwan Passport Number -->
<Entity id="e7251cb4-4c2c-41df-963e-924eb3dae04a" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_passport"/>
     <Match idRef="Keyword_taiwan_passport"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_taiwan_passport"></a>Keyword_taiwan_passport

- ROC passport number 
- Passport number 
- Passport no 
- Passport Num 
- Passport # 
- 护照 
- 中華民國護照 
- Zhōnghuá Mínguó hùzhào
   
## <a name="taiwan-resident-certificate-arctarc-number"></a>台湾居民证 (ARC/TARC) 号码

### <a name="format"></a>Format

10 letters and digits

### <a name="pattern"></a>模式

10 个字母和数字
- 两个字母（不区分大小写）  
- 八个数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_taiwan_resident_certificate 找到与该模式匹配的内容。
- 找到 Keyword_taiwan_resident_certificate 中的一个关键字。

```xml
<!-- Taiwan Resident Certificate (ARC/TARC) -->
<Entity id="48269fec-05ea-46ea-b326-f5623a58c6e9" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_resident_certificate"/>
     <Match idRef="Keyword_taiwan_resident_certificate"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_taiwan_resident_certificate"></a>Keyword_taiwan_resident_certificate

- Resident Certificate 
- Resident Cert 
- Resident Cert. 
- Identification card 
- Alien Resident Certificate 
- ARC 
- Taiwan Area Resident Certificate 
- TARC 
- 居留證 
- 外僑居留證 
- 台灣地區居留證 

## <a name="thai-population-identification-code"></a>泰语填充标识代码

### <a name="format"></a>Format

13 位数字

### <a name="pattern"></a>模式

13 个数字：
- 第一个数字不是0或9 
- 12 个数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_Thai_Citizen_Id 找到与该模式匹配的内容。
- 找到 Keyword_Thai_Citizen_Id 中的关键字。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_Thai_Citizen_Id 找到与该模式匹配的内容。

```xml
<!-- Thai Citizen ID -->
-<Entity id="44ca9e86-ead7-4c5d-884a-e2eaa401515e" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="85">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
      <Match idRef="Keyword_Thai_Citizen_Id"/>
   </Pattern>
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_thai_citizen_id"></a>Keyword_Thai_Citizen_Id

- ID Number
- 标识号码
- บัตรประชาชน
- รหัสบัตรประชาชน
- บัตรประชาชน
- รหัสบัตรประชาชน
  
## <a name="turkish-national-identification-number"></a>土耳其国家标识号码

### <a name="format"></a>Format

11 个数字

### <a name="pattern"></a>模式

11 个数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_Turkish_National_Id 找到与该模式匹配的内容。
- 找到 Keyword_Turkish_National_Id 中的关键字。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_Turkish_National_Id 找到与该模式匹配的内容。

```xml
<!-- Turkish National Identity -->
-<Entity id="fb621f20-3876-4cfc-acec-8c8e73ca32c7" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="85">
      <IdMatch idRef="Func_Turkish_National_Id"/>
      <Match idRef="Keyword_Turkish_National_Id"/>
   </Pattern>
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Func_Turkish_National_Id"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_turkish_national_id"></a>Keyword_Turkish_National_Id

- TC Kimlik No
- TC Kimlik numarası
- Vatandaşlık numarası
- Vatandaşlık no

## <a name="uk-drivers-license-number"></a>英国驾驶证号码

### <a name="format"></a>Format

特定格式的 18 个字母和数字组合

### <a name="pattern"></a>模式

18 个字母和数字：
- 用五个字母（不区分大小写）或数字“9”来代替一个字母 
- 一位数字 
- MMDDY 的日期格式的五个数字（如果驱动程序是女，第七个字符增加50，即51到62而不是01到12）
- 用两个字母（不区分大小写）或数字“9”来代替一个字母 
- 五位数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_uk_drivers_license 找到与该模式匹配的内容。
- 找到 Keyword_uk_drivers_license 中的一个关键字。
- 校验和通过。

```xml
<!-- U.K. Driver's License Number -->
<Entity id="f93de4be-d94c-40df-a8be-461738047551" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_uk_drivers_license" />
        <Match idRef="Keyword_uk_drivers_license" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_uk_drivers_license"></a>Keyword_uk_drivers_license

- DVLA 
- light vans 
- quadbikes 
- motor cars 
- 125cc 
- sidecar 
- tricycles 
- motorcycles 
- photocard licence 
- learner drivers 
- licence holder 
- licence holders 
- driving licences 
- driving licence 
- dual control car 
   
## <a name="uk-electoral-roll-number"></a>英国选民名册号码

### <a name="format"></a>Format

两个字母后跟 1-4 个数字

### <a name="pattern"></a>模式

两个字母（不区分大小写）后跟 1-4 个数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_uk_electoral 找到与该模式匹配的内容。
- 找到 Keyword_uk_electoral 中的一个关键字。

```xml
<!-- U.K. Electoral Number -->
<Entity id="a3eea206-dc0c-4f06-9e22-aa1be3059963" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_uk_electoral" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_electoral" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_uk_electoral"></a>Keyword_uk_electoral

- council nomination 
- nomination form 
- electoral register 
- electoral roll

   
## <a name="uk-national-health-service-number"></a>英国国家卫生服务号码

### <a name="format"></a>Format

10-17 个数字，通过空格分隔 

### <a name="pattern"></a>模式

10-17 位数字：
- 3 或 10 位数字 
- 一个空格 
- 三位数字 
- 一个空格 
- 四位数字

### <a name="checksum"></a>校验和

是

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_uk_nhs_number 找到与该模式匹配的内容。
- 下列其中一项为真：
    - 找到 Keyword_uk_nhs_number 中的一个关键字。
    - 找到 Keyword_uk_nhs_number1 中的一个关键字。
    - 找到 Keyword_uk_nhs_number_dob 中的一个关键字。
- 校验和通过。

```xml
<!-- U.K. NHS Number -->
<Entity id="3192014e-2a16-44e9-aa69-4b20375c9a78" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nhs_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_nhs_number" />
          <Match idRef="Keyword_uk_nhs_number1" />
          <Match idRef="Keyword_uk_nhs_number_dob" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字
   
#### <a name="keyword_uk_nhs_number"></a>Keyword_uk_nhs_number

- national health service 
- nhs 
- health services authority 
- health authority

#### <a name="keyword_uk_nhs_number1"></a>Keyword_uk_nhs_number1

- patient id 
- patient identification 
- patient no 
- patient number

#### <a name="keyword_uk_nhs_number_dob"></a>Keyword_uk_nhs_number_dob

- GP 
- DOB 
- D. B。 
- Date of Birth 
- Birth Date 
   
## <a name="uk-national-insurance-number-nino"></a>英国国家保险号码 (NINO)

### <a name="format"></a>Format

由空格或短划线分隔的7个字符或9个字符

### <a name="pattern"></a>模式

两种可能的模式：

- 两个字母（有效 NINOs 仅使用此前缀中的特定字符，此格式将对此进行验证; 不区分大小写）
- 六位数字
- "A"、"B"、"C" 或 "d" （与前缀一样，后缀中只允许有某些字符; 不区分大小写）

或

- 两个字母
- 一个空格或破折号
- 两位数字
- 一个空格或破折号
- 两位数字
- 一个空格或破折号
- 两位数字
- 一个空格或破折号
- 要么是 "A"、"B"、"C"，要么 ' d '

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_uk_nino 找到与该模式匹配的内容。
- 找到 Keyword_uk_nino 中的一个关键字。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_uk_nino 找到与该模式匹配的内容。
- 未找到 Keyword_uk_nino 中的关键字。

```xml
<!-- U.K. NINO -->
<Entity id="16c07343-c26f-49d2-a987-3daf717e94cc" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nino" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_nino" />
        </Any>
    </Pattern>    
     <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_uk_nino" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_uk_nino" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_uk_nino"></a>Keyword_uk_nino

- national insurance number 
- national insurance contributions 
- protection act 
- 方面 
- social security number 
- insurance application 
- medical application 
- social insurance 
- medical attention 
- social security 
- great britain 
- 方面    
   
## <a name="us--uk-passport-number"></a>美国/英国护照号码

### <a name="format"></a>Format

九个数字

### <a name="pattern"></a>模式

九个连续的数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_usa_uk_passport 找到与该模式匹配的内容。
- 找到 Keyword_passport 中的一个关键字。

```xml
<Entity id="178ec42a-18b4-47cc-85c7-d62c92fd67f8" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_usa_uk_passport" />
        <Match idRef="Keyword_passport" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_passport"></a>Keyword_passport

- Passport Number 
- Passport No 
- Passport # 
- 登记卡# 
- PassportID 
- Passportno 
- passportnumber 
- パスポート 
- パスポート番号 
- パスポートのNum 
- パスポート＃ 
- Numéro de passeport 
- Passeport n ° 
- Passeport Non 
- Passeport # 
- Passeport# 
- PasseportNon 
- Passeportn ° 
   
## <a name="us-bank-account-number"></a>美国银行帐号

### <a name="format"></a>Format

8-17 个数字

### <a name="pattern"></a>模式

8-17 个连续的数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 正则表达式 Regex_usa_bank_account_number 找到与该模式匹配的内容。
- 找到 Keyword_usa_Bank_Account 中的一个关键字。

```xml
<!-- U.S. Bank Account Number -->
<Entity id="a2ce32a8-f935-4bb6-8e96-2a5157672e2c" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_usa_bank_account_number" />
        <Match idRef="Keyword_usa_Bank_Account" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_usa_bank_account"></a>Keyword_usa_Bank_Account

- Checking Account Number 
- Checking Account 
- Checking Account # 
- Checking Acct Number 
- Checking Acct # 
- Checking Acct No. 
- Checking Account No. 
- Bank Account Number 
- Bank Account # 
- Bank Acct Number 
- Bank Acct # 
- Bank Acct No. 
- Bank Account No. 
- Savings Account Number 
- Savings Account. 
- Savings Account # 
- Savings Acct Number 
- Savings Acct # 
- Savings Acct No. 
- Savings Account No. 
- Debit Account Number 
- Debit Account 
- Debit Account # 
- Debit Acct Number 
- Debit Acct # 
- Debit Acct No. 
- Debit Account No. 
   
## <a name="us-drivers-license-number"></a>美国驾驶证号码

### <a name="format"></a>Format

取决于州

### <a name="pattern"></a>模式

取决于州 — 例如，纽约：
- 与 ddd ddd ddd 相匹配的9个数字的格式将会匹配。
- 诸如 dddddddd 的 9 个数字将不匹配。

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_new_york_drivers_license_number 找到与该模式匹配的内容。
- 找到 Keyword_[state_name]_drivers_license_name 中的一个关键字。
- 找到 Keyword_us_drivers_license 中的一个关键字。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 65% 确信它检测到这种类型的敏感信息：
- 函数 Func_new_york_drivers_license_number 找到与该模式匹配的内容。
- 找到 Keyword_[state_name]_drivers_license_name 中的一个关键字。
- 找到 Keyword_us_drivers_license_abbreviations 中的一个关键字。
- 未找到 Keyword_us_drivers_license 中的关键字。

```xml
<Entity id="dfeb356f-61cd-459e-bf0f-7c6d28b458c6 patternsProximity="300">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license" />
    </Pattern>
    <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license_abbreviations" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_us_drivers_license" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_us_drivers_license_abbreviations"></a>Keyword_us_drivers_license_abbreviations

- 通讯 
- DLS 
- 采用 
- CDLS 
- ID 
- Id 
- 通讯# 
- DLS# 
- 采用# 
- CDLS# 
- 号#
- Id# 
- ID number 
- ID numbers 
- .LIC 
- .LIC# 

#### <a name="keyword_us_drivers_license"></a>Keyword_us_drivers_license

- DriverLic 
- DriverLics 
- DriverLicense 
- DriverLicenses 
- Driver Lic 
- Driver Lics 
- Driver License 
- Driver Licenses 
- DriversLic 
- DriversLics 
- DriversLicense 
- DriversLicenses 
- Drivers Lic 
- Drivers Lics 
- Drivers License 
- Drivers Licenses 
- Driver'Lic 
- Driver'Lics 
- Driver'License 
- Driver'Licenses 
- Driver' Lic 
- Driver' Lics 
- Driver' License 
- Driver' Licenses
- Driver'sLic 
- Driver'sLics 
- Driver'sLicense 
- Driver'sLicenses 
- Driver's Lic 
- Driver's Lics 
- Driver's License 
- Driver's Licenses 
- identification number 
- identification numbers 
- identification # 
- id card 
- id cards 
- identification card 
- identification cards 
- DriverLic# 
- DriverLics# 
- DriverLicense# 
- DriverLicenses# 
- Driver Lic# 
- Driver Lics# 
- Driver License# 
- Driver Licenses# 
- DriversLic# 
- DriversLics# 
- DriversLicense# 
- DriversLicenses# 
- Drivers Lic# 
- Drivers Lics# 
- Drivers License# 
- Drivers Licenses# 
- Driver'Lic# 
- Driver'Lics# 
- Driver'License# 
- Driver'Licenses# 
- Driver' Lic# 
- Driver' Lics# 
- Driver' License# 
- Driver' Licenses# 
- Driver'sLic# 
- Driver'sLics# 
- Driver'sLicense# 
- Driver'sLicenses# 
- Driver's Lic# 
- Driver's Lics# 
- Driver's License# 
- Driver's Licenses# 
- id card# 
- id cards# 
- identification card# 
- identification cards# 


#### <a name="keyword_state_name_drivers_license_name"></a>Keyword_ [state_name] _drivers_license_name

- 州缩写（例如，“NY”） 
- 州名称（例如，“New York”）    
   
## <a name="us-individual-taxpayer-identification-number-itin"></a>美国单独的纳税人标识号 (ITIN)

### <a name="format"></a>Format

九个数字，以“9”开头，“7”或“8”作为第四个数字，可以采用空格或短划线格式

### <a name="pattern"></a>模式

格式
- 数字“9” 
- 两位数字 
- 一个空格或破折号 
- “7”或“8” 
- 一位数字 
- 一个空格或破折号 
- 四位数字

纯
- 数字“9” 
- 两位数字 
- “7”或“8” 
- 五位数字

### <a name="checksum"></a>校验和

否

### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_formatted_itin 找到与该模式匹配的内容。
- 下列至少其中一项为真：
    - 找到 Keyword_itin 中的一个关键字。
    - 函数 Func_us_address 找到正确日期格式的地址。
    - 函数 Func_us_date 找到正确日期格式的日期。
    - 找到 Keyword_itin_collaborative 中的一个关键字。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_unformatted_itin 找到与该模式匹配的内容。
- 下列至少其中一项为真：
    - 找到 Keyword_itin_collaborative 中的一个关键字。
    - 函数 Func_us_address 找到正确日期格式的地址。
    - 函数 Func_us_date 找到正确日期格式的日期。

```xml
<!-- U.S. Individual Taxpayer Identification Number (ITIN) -->
<Entity id="e55e2a32-f92d-4985-a35d-a0b269eb687b" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_formatted_itin" />
        <Any minMatches="1">
          <Match idRef="Keyword_itin" />
          <Match idRef="Func_us_address" />
          <Match idRef="Func_us_date" />
          <Match idRef="Keyword_itin_collaborative" />
        </Any>
    </Pattern>
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_itin" />
        <Match idRef="Keyword_itin" />
        <Any minMatches="1">
          <Match idRef="Keyword_itin_collaborative" />
          <Match idRef="Func_us_address" />
          <Match idRef="Func_us_date" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_itin"></a>Keyword_itin

- 报税 
- tax id 
- tax identification 
- itin 
- ssn 
- 锡 
- social security 
- tax payer 
- itins 
- taxid 
- individual taxpayer 

#### <a name="keyword_itin_collaborative"></a>Keyword_itin_collaborative

- 许可证 
- 通讯 
- DOB 
- 出生日期 
- 一定 
- Date of Birth 
   
## <a name="us-social-security-number-ssn"></a>美国社会保险号 (SSN)

### <a name="format"></a>Format

9 个数字，可以是格式化模式，也可以是非格式化模式

> [!NOTE]
> 如果在 2011 年中旬前发布，则 SSN 具有强格式，即数字的某部分必须介于某个有效的范围中（但是没有校验和）。

### <a name="pattern"></a>模式

四种不同模式中的 SSN 的四种函数外观：
- Func_ssn 查找具有 2011 年以前使用短划线或空格格式化的强格式的 SSN（ddd-dd-dddd 或 ddd dd dddd）
- Func_unformatted_ssn 查找具有 2011 年以前未格式化为 9 个连续数字的强格式的 SSN (ddddddddd)
- Func_randomized_formatted_ssn 查找 2011 年后使用短划线或空格（ddd-dd-dddd 或 ddd dd dddd）格式化的 SSN
- Func_randomized_unformatted_ssn 查找 2011 年后未格式化为 9 个连续数字 (ddddddddd) 的 SSN

### <a name="checksum"></a>校验和

否


### <a name="definition"></a>定义

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 85% 确信它检测到这种类型的敏感信息：
- 函数 Func_ssn 找到与该模式匹配的内容。
- 找到 Keyword_ssn 中的一个关键字。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 75% 确信它检测到这种类型的敏感信息：
- 函数 Func_unformatted_ssn 查找与该模式匹配的内容。
- 找到 Keyword_ssn 中的一个关键字。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 65% 确信它检测到这种类型的敏感信息：
- 函数 Func_randomized_formatted_ssn 找到与该模式匹配的内容。
- 找到 Keyword_ssn 中的一个关键字。

在 300 个字符的相似度内，如果出现以下情况，DLP 策略 55% 确信它检测到这种类型的敏感信息：
- 函数 Func_randomized_unformatted_ssn 找到与该模式匹配的内容。
- 找到 Keyword_ssn 中的一个关键字。


```xml
<!-- U.S. Social Security Number (SSN) -->
  <Entity id="a44669fe-0d48-453d-a9b1-2cc83f2cba77" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_randomized_formatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="55">
        <IdMatch idRef="Func_randomized_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
  </Entity>
```

### <a name="keywords"></a>关键字

#### <a name="keyword_ssn"></a>Keyword_ssn

- Social Security 
- Social Security# 
- Soc Sec 
- SSN 
- SSN 
- SSN# 
- SS# 
- SSID 
   
