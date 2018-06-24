---
title: Proprietà DatabaseLogonType (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- DatabaseLogonType
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
caps.latest.revision: 24
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 30c6961f915789c358ba8d38ad0d18e164e072cf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054693"
---
# <a name="databaselogontype-property-wmi-msreportserverconfigurationsetting"></a>Proprietà DatabaseLogonType (MSReportServer_ConfigurationSetting WMI)
  Specifica se il server di report usa un account del servizio [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, un account utente di Windows o un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per accedere al database del server di report. Di sola lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a>Valori della proprietà  
 Oggetto `integer` che rappresenta il tipo di accesso.  
  
## <a name="example-code"></a>Codice di esempio  
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Remarks  
 I valori possibili sono:  
  
-   0 per l'account di accesso di Windows  
  
-   1 per l'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   2 per accedere come servizio  
  
 Se si specifica 0 (Windows), è necessario impostare il valore [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) proprietà a un oggetto corrispondente a un account utente di Windows valido.  
  
 Se si specifica 1 (SQL Server), assicurarsi che il valore di [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) corrisponde a un valore valido [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso.  
  
 Se si specifica 2 (servizio Windows), il server di report usa un account di [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] e l'account del servizio Windows per accedere al database del server di report. La proprietà DatabaseLogonAccount viene ignorata.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  