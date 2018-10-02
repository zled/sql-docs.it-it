---
title: Proprietà DatabaseLogonType (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- DatabaseLogonType
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d9d20259ec79532db2ccbb04da4f83d66f3e2abd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47608595"
---
# <a name="configurationsetting-property---databaselogontype"></a>Proprietà ConfigurationSetting - DatabaseLogonType
  Specifica se il server di report usa un account del servizio [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, un account utente di Windows o un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per accedere al database del server di report. Di sola lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a>Valori della proprietà  
 Oggetto **integer** che rappresenta il tipo di accesso.  
  
## <a name="example-code"></a>Codice di esempio  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Remarks  
 I valori possibili sono:  
  
-   0 per l'account di accesso di Windows  
  
-   1 per l'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   2 per accedere come servizio  
  
 Se si specifica 0 (Windows), è necessario impostare il valore nella proprietà [DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogonaccount.md) su un account utente di Windows valido corrispondente.  
  
 Se si specifica 1 (SQL Server), accertarsi che il valore di [DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogonaccount.md) corrisponda a un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valido.  
  
 Se si specifica 2 (servizio Windows), il server di report usa un account di [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] e l'account del servizio Windows per accedere al database del server di report. La proprietà DatabaseLogonAccount viene ignorata.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
