---
title: "Cmdlet New-PowerPivotSystemServiceInstance | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 7ea94113-c0f1-4cca-9228-f1a034fba5db
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Cmdlet New-PowerPivotSystemServiceInstance
  Aggiunge una nuova istanza del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] a un server applicazioni.  
  
 **Applicabile a:** SharePoint 2010 e SharePoint 2013.  
  
## Sintassi  
  
```  
New-PowerPivotSystemServiceInstance [[-ParentService] <PowerPivotMidTierServicePipeBind>] [-SystemServiceInstanceName <string>] [-Provision] [<CommonParameters>]  
```  
  
## Description  
 Con il cmdlet New-PowerPivotSystemServiceInstance è possibile effettuare il provisioning di un nuovo oggetto PowerPivotSystemService a livello di farm dopo aver usato il programma di installazione di SQL Server per installare [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint nel server applicazioni locale. È possibile eseguire il provisioning di una sola istanza del servizio in ogni server applicazioni.  Se è già stato eseguito il provisioning del servizio, non è possibile eseguire questo cmdlet.  
  
## Parametri  
  
### -ParentService \<PowerPivotMidTierServicePipeBind>  
 Specifica il GUID dell'oggetto padre del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm. In questa versione, è consentito un solo oggetto padre. È possibile utilizzare Get-PowerPivotSystemService per restituire l'oggetto servizio o il relativo GUID.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|true|  
|Accettare caratteri jolly?|false|  
  
### -SystemServiceInstanceName \<string>  
 Specifica un nome che identifica l'oggetto.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|1|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### Provision [\<SwitchParameter>]  
 Rende disponibile il servizio in SharePoint. I valori validi sono $true o $false.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### \<CommonParameters>  
 Questo cmdlet supporta i parametri comuni, ovvero Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer e OutVariable. Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|Nessuno|  
|Output|nessuna.|  
  
## Esempio 1  
  
```  
C:\PS>New-PowerPivotSystemServiceInstance -Provision:$true  
```  
  
 In questo esempio si illustra la forma più comune del cmdlet. Registra il servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nel server applicazioni locale con la farm.  
  
## Esempio 2  
  
```  
C:\PS>New-PowerPivotSystemServiceInstance -SystemServiceInstanceName "MyPSSInstance" -provision:$false  
```  
  
 In questo esempio si assegna un nome all'istanza del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], ma senza effettuarne il provisioning. Se non si fornisce un nome, viene utilizzato il nome predefinito, Istanza del servizio di sistema SQL Server Analysis Services. La creazione di un nome personalizzato per il servizio è facoltativa. È possibile assegnare un nome al servizio per supportare scenari di test oppure se si dispone di uno strumento personalizzato o di uno script che consente di eseguire il provisioning dell'istanza in un passaggio successivo.  
  
  