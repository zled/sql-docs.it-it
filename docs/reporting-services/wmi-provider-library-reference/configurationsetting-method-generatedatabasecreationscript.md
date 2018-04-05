---
title: Metodo di ConfigurationSetting - GenerateDatabaseCreationScript | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: ''
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
caps.latest.revision: 25
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 668be602cce0b74e0d2662021b3e4306405c4fb7
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="configurationsetting-method---generatedatabasecreationscript"></a>Metodo di ConfigurationSetting - GenerateDatabaseCreationScript
  Genera uno script SQL che può essere utilizzato per creare un database del server di report.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub GenerateDatabaseCreationScript(ByVal DatabaseName As String, _  
    ByVal Lcid As Int32, ByVal IsSharePointMode As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseCreationScript(string DatabaseName, Int32 Lcid,   
    Boolean IsSharePointMode, out string Script, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *Databasename*  
 Stringa che contiene il nome del database del server di report da creare.  
  
 *LCID*  
 Valore utilizzato per localizzazione dei nomi di ruolo.  
  
 *IsSharePointMode*  
 Indica se creare database in modalità nativa o in modalità SharePoint.  
  
> [!IMPORTANT]  
>  A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], *IsSharePointMode*=**True** non è supportato poiché, in modalità SharePoint, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è un servizio condiviso SharePoint e non è controllato dal provider WMI. Questo parametro deve essere impostato sempre su **False**.  
  
 *Script*  
 [out] Stringa che contiene lo script SQL generato.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## <a name="remarks"></a>Remarks  
 Questo metodo genera uno script SQL che crea database del server di report per la versione del server di report attualmente connessa.  
  
 Il valore fornito nel parametro *DatabaseName* deve essere conforme alle convenzioni di denominazione dei database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Il metodo non verifica l'esistenza del database al momento della generazione dello script.  
  
 Questo metodo non verifica l'esistenza del database del server di report al momento della generazione dello script.  
  
 Lo script generato supporta [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 e [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
