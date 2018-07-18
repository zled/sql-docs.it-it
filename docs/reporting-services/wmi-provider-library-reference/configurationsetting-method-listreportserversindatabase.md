---
title: Metodo ListReportServersInDatabase (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- ListReportServersInDatabase (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- ListReportServersInDatabase method
ms.assetid: a4bf5968-c46f-484f-a510-65e2dde65a0d
caps.latest.revision: 18
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: dfb91a3cc4326f1fa52661002b2a9d8c69c6e52a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33030178"
---
# <a name="configurationsetting-method---listreportserversindatabase"></a>Metodo ConfigurationSetting - ListReportServersInDatabase
  Restituisce l'elenco di installazioni del server di report presenti nel database del server di report, indipendentemente dal fatto che tali installazioni accedano a informazioni protette.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub ListReportServersInDatabase(ByRef MachineNames() As String, _  
    ByRef InstanceNames() As String, ByRef InstallationIDs() As String, _  
    ByRef IsInitialized() As Boolean, ByRef Length As Int32, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] MachineNames,   
    out string[] InstanceNames, out string[] InstallationIDs,   
    out Boolean[] IsInitialized,out Int32 Length, out Int32 HRESULT,    
    out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Parametri  
 *MachineNames[]*  
 [out] Matrice che contiene i nomi di computer per le installazioni del server di report nel database.  
  
 *InstanceNames[]*  
 [out] Matrice che contiene i nomi delle istanze di ognuna delle installazioni del server di report nel database.  
  
 *InstallationIDs[]*  
 [out] Matrice che contiene gli ID di installazione di ogni installazione del server di report nel database.  
  
 *IsInitialized[]*  
 [out] Matrice che contiene lo stato di inizializzazione di ogni installazione del server di report nel database.  
  
 *Lunghezza*  
 [out] Lunghezza delle matrici restituite dal metodo. Tutte le matrici restituite hanno la stessa lunghezza.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
 *ExtendedErrors[]*  
 [out] Matrice di stringhe che contiene errori aggiuntivi restituiti dalla chiamata.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## <a name="remarks"></a>Remarks  
 ListReportServersInDatabase elenca le installazioni del server di report presenti nel database del server di report, indipendentemente dal fatto che tali installazioni accedano a informazioni protette e restituisce un set di matrici corrispondente in cui sono contenute le informazioni su ciascuna installazione.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
