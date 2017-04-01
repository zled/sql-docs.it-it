---
title: "Metodo SetServiceState (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs"
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
  - "SetServiceState (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "SetServiceState - metodo"
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
caps.latest.revision: 20
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Metodo SetServiceState (MSReportServer_ConfigurationSetting WMI)
  Attiva e disattiva i servizi Windows ReportServer e Web ReportServer.  
  
## Sintassi  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## Parametri  
 *EnableWindowsService*  
 Valore **booleano** che indica lo stato del servizio Windows. Un valore **true** avvia il servizio Windows ReportServer; un valore **false** arresta il servizio Windows.  
  
 *EnableWebService*  
 Valore **booleano** che indica lo stato del servizio Web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Un valore **true** avvia il servizio Windows ReportServer; un valore **false** arresta il servizio Web  
  
 *EnableReportManager*  
 Valore **booleano** che indica lo stato desiderato per Gestione report.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## Osservazioni  
  
## Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  