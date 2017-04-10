---
title: "Cmdlet Get-PowerPivotServiceApplication | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 99e4faa1-2f87-43c6-b7ec-a97d4112c5ac
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Cmdlet Get-PowerPivotServiceApplication
  Restituisce una o più applicazioni del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
 **Applicabile a:** SharePoint 2010 e SharePoint 2013.  
  
## Sintassi  
  
```  
Get-PowerPivotServiceApplication [[-Identity] <SPGeminiServiceApplicationPipeBind>] [<CommonParameters>]  
```  
  
## Description  
 Con il cmdlet Get-PowerPivotServiceApplication viene restituita l'applicazione di servizio specificata dal parametro Identity. Se non è specificato alcun parametro, il cmdlet restituisce tutte le applicazioni del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm. Ogni applicazione viene identificata dal nome visualizzato, dal tipo di applicazione e dal GUID. Per visualizzare proprietà aggiuntive di un'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], aggiungere l'opzione format-list al cmdlet.  
  
## Parametri  
  
### -Identity \<SPGeminiServiceApplicationPipeBind>  
 Specifica l'applicazione di servizio da ottenere. Il valore deve essere un GUID valido tramite cui si identifica in modo univoco l'oggetto nella farm.  
  
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
|Output|Nessuno|  
  
## Esempio 1  
  
```  
C:\PS>Get-PowerPivotServiceApplication  
```  
  
 In questo esempio si restituiscono una o più applicazioni di servizio nella farm.  
  
## Esempio 2  
  
```  
C:\PS>Get-PowerPivotServiceApplication | format-list  
```  
  
 Questo esempio restituisce tutte le proprietà di un'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
## Esempio 3  
  
```  
C:\PS>get-PowerPivotServiceApplication -Identity 1234567-890a-bcde-fghijklm  
```  
  
 In questo esempio viene restituita una singola applicazione di servizio, mostrando il nome visualizzato, il tipo di applicazione e il GUID dell'applicazione. Se il nome visualizzato è lungo, viene troncato. Utilizzare l'opzione format-list per visualizzare il nome completo.  
  
  