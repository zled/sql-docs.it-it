---
title: "Cmdlet Remove-PowerPivotServiceApplication | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 2742b2a3-927c-4e7c-bd7d-43c072fa01ab
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 11
---
# Cmdlet Remove-PowerPivotServiceApplication
  Elimina un'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
 **Applicabile a:** SharePoint 2010 e SharePoint 2013.  
  
## Sintassi  
  
```  
Remove-PowerPivotServiceApplication [-Identity <SPGeminiServiceApplicationPipeBind>] [-DeleteAll <switch>] [-RemoveData <switch>] [-Confirm <switch>] [<CommonParameters>]  
```  
  
## Description  
 Con il cmdlet Remove-PowerPivotServiceApplication è possibile eliminare un'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dalla farm. Utilizzare DeleteAll per eliminare immediatamente tutte le applicazioni di servizio oppure utilizzare il parametro Identity per rimuovere una singola istanza. Per ottenere informazioni sull'istanza, eseguire Get-PowerPivotServiceApplication per restituire tutte le istanze nella farm.  
  
 Utilizzare il parametro RemoveData per rimuovere facoltativamente i database dell'applicazione di servizio e i file memorizzati nella cache. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] - Le cartelle di lavoro rimangono nelle raccolte contenuto, ma non sono più funzionali dopo la rimozione dell'applicazione del servizio.  
  
## Parametri  
  
### -Identity \<SPGeminiServiceApplicationPipeBind>  
 Specifica il GUID di una singola applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm. È necessario specificare il GUID se si desidera rimuovere solo un'applicazione, lasciando invariate le altre applicazioni di servizio.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|true|  
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
  
### -DeleteAll \<switch>  
 Elimina tutte le applicazioni del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] senza eliminare il database dell'applicazione del servizio, né gli oggetti dell'istanza del servizio nella farm. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Le istanze degli oggetti del servizio di sistema e del servizio motore [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] rimangono, ma gli oggetti non possono essere usati dopo la rimozione delle applicazioni del servizio.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -RemoveData \<switch>  
 Consente di rimuovere il database dell'applicazione di servizio contenente le pianificazioni di aggiornamento dati, i dati di utilizzo delle cartelle di lavoro, le mappe dell'istanza utilizzate per tenere traccia dei database caricati e altri dati interni.  
  
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
C:\PS>Remove-PowerPivotServiceApplication -identity 12345678-90ab-cdef-ghijklmnop  
```  
  
 Questo esempio elimina una singola applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], ma non il relativo database o la cache. Se non si specifica un'identità, viene richiesto di fornirne una.  
  
## Esempio 2  
  
```  
C:\PS>Remove-PowerPivotServiceApplication -DeleteAll  
```  
  
 Questo esempio elimina tutte le applicazioni del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm. Database e cache non vengono eliminati.  
  
## Esempio 3  
  
```  
CC:\PS>Remove-PowerPivotServiceApplication -identity 12345678-90ab-cdef-ghijklmnop -RemoveData  
```  
  
 Questo esempio elimina una singola applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] insieme ai relativi database e file di cache.  
  
  