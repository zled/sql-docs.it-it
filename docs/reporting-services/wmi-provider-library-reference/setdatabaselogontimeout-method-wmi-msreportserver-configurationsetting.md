---
title: "Metodo SetDatabaseLogonTimeout (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "SetDatabaseLogonTimeout (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "metodo SetDatabaseLogonTimeout"
ms.assetid: b8773596-5b98-4355-a4ab-4412e1317c67
caps.latest.revision: 19
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Metodo SetDatabaseLogonTimeout (MSReportServer_ConfigurationSetting WMI)
  Specifica il valore di timeout predefinito per le connessioni al database del server di report.  
  
## Sintassi  
  
```vb  
Public Sub SetDatabaseLogonTimeout(LogonTimeout as Int32, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetDatabaseLogonTimeout(Int32 LogonTimeout,   
    out Int32 HRESULT);  
```  
  
## Parametri  
 *LogonTimeout*  
 Valore di timeout predefinito, espresso in secondi, per le connessioni al database del server di report.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  