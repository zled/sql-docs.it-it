---
title: Metodo GetDatabaseVersionDisplayName (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- GetDatabaseVersionDisplayName method
ms.assetid: e1286424-7043-4f12-a7ad-1cf69e81baa4
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a5f5d95fc55ef9a60e1cb79cd45ef70f72cdff53
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33030838"
---
# <a name="configurationsetting-method---getdatabaseversiondisplayname"></a>Metodo di ConfigurationSetting - GetDatabaseVersionDisplayName
  Ottiene il nome visualizzato di una stringa di versione di un database del server di report specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub GetDatabaseVersionDisplayName(Version As String, DisplayName As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetDatabaseVersionDisplayName(string Version, string DisplayName, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *Version*  
 Stringa che contiene la stringa di versione per un database del server di report.  
  
 *DisplayName*  
 [out] Stringa che contiene il nome visualizzato che corrisponde alla versione fornita.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## <a name="remarks"></a>Remarks  
 Nella tabella seguente viene mostrato il mapping dalla versione del database alla stringa visualizzata.  
  
|**Versione**|**Versione**|**Nome visualizzato**|  
|-----------------|-----------------|----------------------|  
|RS 2005 SP2|@DBVersion = 'C.0.8.54'|SQL Server 2005 SP2|  
|RS 2005 SP1|@DBVersion = 'C.0.8.43'|SQL Server 2005 SP1|  
|RS 2005 RTM|@DBVersion = 'C.0.8.40'|SQL Server 2005|  
|RS 2000 SP2|@DBVersion = 'C.0.6.54'|SQL Server 2000 SP2|  
|RS 2000 SP1|@DBVersion = 'C.0.6.51'|SQL Server 2000 SP1|  
|RS 2000 RTM|@DBVersion = 'C.0.6.43'|SQL Server 2000|  
|Hotfix||Versione applicabile più vicina|  
  
 Per un valore di *Version* antecedente a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 viene restituito un valore HRESULT di ACT_E_BAD_VERSION.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
