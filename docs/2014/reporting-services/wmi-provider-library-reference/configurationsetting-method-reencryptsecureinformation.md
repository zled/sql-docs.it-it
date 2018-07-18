---
title: Metodo ReencryptSecureInformation (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
api_name:
- ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ReencryptSecureInformation method
ms.assetid: 8a487497-c207-45b2-8c92-87c58cc68716
caps.latest.revision: 18
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7cdd5ce30bd23f871eb1ad88e1953f1316f7c56a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37222861"
---
# <a name="reencryptsecureinformation-method-wmi-msreportserverconfigurationsetting"></a>Metodo ReencryptSecureInformation (MSReportServer_ConfigurationSetting WMI)
  Genera una nuova chiave di crittografia e la utilizza per crittografare nuovamente tutte le informazioni protette contenute nel catalogo.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub ReencryptSecureInformation(ByRef HRESULT as Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ReencryptSecureInformation (out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Parametri  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
 *ExtendedErrors[]*  
 [out] Matrice di stringhe che contiene errori aggiuntivi restituiti dalla chiamata.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## <a name="remarks"></a>Note  
 Il metodo ReencryptSecureInformation consente all'amministratore di sostituire la chiave di crittografia esistente con una nuova chiave.  
  
 Quando viene richiamato questo metodo, il server di report genera una nuova chiave di crittografia e scorre tutto il contenuto crittografato per crittografarlo nuovamente con la nuova chiave di crittografia.  
  
 Le estensioni per il recapito possono archiviare informazioni protette nelle relative strutture delle impostazioni per il recapito. Quando viene chiamato ReencryptSecureInformation, il server di report carica ciascuna sottoscrizione e l'estensione per il recapito corrispondente per crittografare nuovamente le informazioni archiviate nelle impostazioni associate.  
  
 Se questo metodo viene eseguito in un computer in una distribuzione con scalabilità orizzontale, ciascun computer nella distribuzione dovrà essere inizializzato nuovamente.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
