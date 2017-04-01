---
title: "Metodo RestoreEncryptionKey (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs"
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
  - "RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "metodo RestoreEncryptionKey"
ms.assetid: 37e949f5-15af-4858-848a-f482ee94fcd9
caps.latest.revision: 18
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Metodo RestoreEncryptionKey (MSReportServer_ConfigurationSetting WMI)
  Riapplica la chiave di crittografia specificata al database del server di report.  
  
## Sintassi  
  
```vb  
Public Sub RestoreEncryptionKey(ByRef KeyFile() As Integer, _  
    ByRef Length As Int32, ByVal Password As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void RestoreEncryptionKey(out Byte[] KeyFile, out Int32 Length,   
            string Password, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## Parametri  
 *KeyFile[]*  
 [out] Matrice che contiene la chiave di crittografia crittografata.  
  
 *Lunghezza*  
 [out] Lunghezza della matrice restituita dal metodo.  
  
 *Password*  
 Stringa utilizzata per crittografare la chiave di crittografia.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
 *ExtendedErrors[]*  
 [out] Matrice di stringhe che contiene errori aggiuntivi restituiti dalla chiamata.  
  
## Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## Osservazioni  
 Se nel database del server di report esiste già una voce per il server di report , viene eliminata. La nuova voce viene quindi creata utilizzando la chiave di crittografia specificata e la chiave pubblica del server di report.  
  
 Il metodo è più efficace se viene chiamato dopo il metodo [DeleteEncryptionKey](../../reporting-services/wmi-provider-library-reference/deleteencryptionkey-method-wmi-msreportserver-configurationsetting.md), che svuota l'elenco delle chiavi di crittografia.  
  
## Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  