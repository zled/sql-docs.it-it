---
title: "Metodo SetSecureConnectionLevel (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs"
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
  - "SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "metodo SetSecureConnectionLevel"
ms.assetid: 0fac7d5e-2670-4657-9439-331e7d93babb
caps.latest.revision: 21
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Metodo SetSecureConnectionLevel (MSReportServer_ConfigurationSetting WMI)
  Imposta il livello di connessione protetta del server di report.  
  
## Sintassi  
  
```vb  
Public Sub SetSecureConnectionLevel(Level as Integer, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Int32 Level,   
    out Int32 HRESULT);  
```  
  
## Parametri  
 *Level*  
 Valore intero che rappresenta un livello di connessione protetta.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## Osservazioni  
 Quando viene chiamata, la proprietà SecureConnectionLevel del server di report è impostata sul valore specificato. Il valore 0 indica che SSL è disattivato. Il valore maggiore di o pari a 1 indica che SSL è abilitato.  
  
-   Quando il valore è impostato, l'elemento SecureConnectionLevel del file di configurazione del server di report viene modificato e l'elemento **URLRoot** del file di configurazione viene impostato per usare "https://" se il valore specificato per *Level* è maggiore o uguale a 1 oppure "http://" se il valore specificato per *Level* è 0.  
  
 In [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SecureConnectionLevel diventa un'opzione di attivazione/disattivazione. Il valore predefinito è 0. Per qualsiasi valore maggiore o uguale a 1 passato tramite l'API del metodo SetSecureConnectionLevel, SSL viene considerato abilitato e la proprietà di configurazione SecureConnectionLevel viene impostata di conseguenza nel file rsreportserver.config. I valori 2 e 3 sono ancora consentiti per la compatibilità con le versioni precedenti.  
  
## Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  