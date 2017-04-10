---
title: "Cmdlet Get-PowerPivotSystemService | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 33231250-3880-4d75-936b-d70662a01855
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Cmdlet Get-PowerPivotSystemService
  Restituisce le proprietà globali dell'oggetto del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in una farm.  
  
 **Applicabile a:** SharePoint 2010 e SharePoint 2013.  
  
## Sintassi  
  
```  
Get-PowerPivotSystemService [-Identity <PowerPivotMidTierServicePipeBind>] [<CommonParameters>]  
```  
  
## Description  
 Il cmdlet Get-PowerPivotSystemService restituisce le proprietà globali dell'oggetto del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in una farm. È presente un oggetto padre per farm, ma ogni farm può avere più istanze del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in esecuzione nei singoli server applicazioni nella farm. L'oggetto padre indica le impostazioni a livello di farm che non variano in base all'istanza. Se nella farm sono incluse più installazioni di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint, un elenco delimitato da virgole delle istanze indica il numero di istanze del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] presenti nella farm.  
  
## Parametri  
  
### -Identity \<PowerPivotMidTierServicePipeBind>  
 Specifica l'oggetto padre da ottenere. Il valore deve essere un GUID valido tramite cui si identifica in modo univoco l'oggetto nella farm.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|true|  
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
C:\PS>Get-PowerPivotSystemService  
```  
  
 Questo esempio restituisce le proprietà globali dell'oggetto padre, mostrando le proprietà condivise da tutte le istanze del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm.  
  
  