---
title: "Cmdlet Remove-PowerPivotSystemServiceInstance | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: bc46094a-5584-47ba-8883-77dc79373a5d
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Cmdlet Remove-PowerPivotSystemServiceInstance
  Rimuove un'istanza del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dalla farm.  
  
 **Applicabile a:** SharePoint 2010 e SharePoint 2013.  
  
## Sintassi  
  
```  
Remove-PowerPivotSystemServiceInstance [-Confirm <switch>] [-DeleteLocal <switch>] [-Identity <PowerPivotMidTierServiceInstancePipeBind>] [<CommonParameters>]  
```  
  
## Description  
 Con il cmdlet Remove-PowerPivotSystemServiceInstance è possibile rimuovere informazioni sull'istanza relative al servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dalla farm. Non vengono rimossi i file di programma. Per rimuovere in modo permanente i file di programma, è necessario disinstallarli.  
  
 Se si rimuove il servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], assicurarsi di eseguire anche Remove-PowerPivotEngineServiceInstance per rimuovere l'istanza di Analysis Services associata, seguito da Remove-PowerPivotServiceApplication per eliminare tutte le applicazioni PowerPivotservice. Le applicazioni di servizio non verranno più eseguite dopo la rimozione dei servizi.  
  
 Per annullare questa modifica, è possibile eseguire New-PowerPivotSystemServiceInstance -Provision:$true per abilitare nuovamente le informazioni sull'istanza.  
  
## Parametri  
  
### -Identity \<PowerPivotMidTierServiceInstancePipeBind>  
 Specifica il GUID dell'istanza del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] da rimuovere. È disponibile una sola istanza del servizio in ogni server applicazioni con un'installazione di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|true|  
|Accettare caratteri jolly?|false|  
  
### -DeleteLocal \<switch>  
 Elimina l'istanza del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] installata nel computer locale, permettendo di rimuovere l'istanza senza dover specificare un'identità dell'oggetto.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Confirm \<switch>  
 Richiede la conferma dell'utente prima dell'esecuzione del comando. Questo valore è abilitato per impostazione predefinita. Per ignorare la risposta di conferma in un comando, specificare Confirm:$false nel comando.  
  
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
|Output|Nessuno|  
  
## Esempio 1  
  
```  
C:\PS>Remove-PowerPivotSystemServiceInstance -deletelocal  
```  
  
 In questo esempio si illustra come rimuovere l'istanza del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in esecuzione nel server applicazioni locale.  
  
## Esempio 2  
  
```  
C:\PS>Remove-PowerPivotSystemServiceInstance -identity 1234567-890a-bcde-fghijklmn  
```  
  
 Questo esempio mostra come eliminare un servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] specifico in base alla relativa identità.  
  
  