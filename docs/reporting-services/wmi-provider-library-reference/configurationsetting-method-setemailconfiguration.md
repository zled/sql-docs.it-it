---
title: Metodo SetEmailConfiguration (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname: SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting Class)
apilocation: reportingservices.mof
apitype: MOFDef
helpviewer_keywords: SetEmailConfiguration method
ms.assetid: b40a2224-2c90-4d32-892f-1fe73a0591ca
caps.latest.revision: "19"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: c69a54107955301b2c97aa1bd7c64d156a65c697
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="configurationsetting-method---setemailconfiguration"></a>Metodo ConfigurationSetting - SetEmailConfiguration
  Configura l'estensione per il recapito tramite posta elettronica utilizzata dal server di report per l'invio di messaggi di posta elettronica.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub SetEmailConfiguration(ByVal SendUsingSMTPServer As Boolean, _  
    ByVal SMTPServer As String, ByVal SenderEmailAddress As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetEmailConfiguration (Boolean SendUsingSMTPServer,   
   string SMTPServer, string SenderEmailAddress,   
   out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *SendUsingSMTPServer*  
 Valore booleano che indica se il server deve utilizzare il server SMTP per inviare posta elettronica. Questo valore può essere impostato solo su True. Il valore predefinito è false.  
  
 *SMTPServer*  
 Stringa che contiene il nome o l'indirizzo IP di un server SMTP.  
  
 *SenderEmailAddress*  
 Indirizzo di posta elettronica utilizzato nel campo 'Da:' dei messaggi di posta elettronica inviati dal server di report.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## <a name="remarks"></a>Osservazioni  
 Quando il parametro *SendUsingSMTPServer* è impostato su **true**, la voce **SendUsing** nel file di configurazione del server di report viene impostata su 1. Quando *SendUsingSMTPServer* è impostato su **false**, la voce **SendUsing** non è configurata.  
  
 Questo metodo non fornisce agli utenti un modo per impostare la voce **SendUsing** del file di configurazione del server di report su un valore diverso da 1. Per configurare il server di report per qualsiasi elemento diverso dalla posta SMTP, è necessario modificare manualmente il file di configurazione.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
