---
title: Il cmdlet Get-PowerPivotServiceApplication | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 99e4faa1-2f87-43c6-b7ec-a97d4112c5ac
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: df1c2c4108ad29164ab096fde95bc760a0c7ccb0
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="get-powerpivotserviceapplication-cmdlet"></a>Cmdlet Get-PowerPivotServiceApplication
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Restituisce uno o più [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] applicazioni di servizio.  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
 **Applicabile a:** SharePoint 2010 e SharePoint 2013.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Get-PowerPivotServiceApplication [[-Identity] <SPGeminiServiceApplicationPipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Con il cmdlet Get-PowerPivotServiceApplication viene restituita l'applicazione di servizio specificata dal parametro Identity. Se non è specificato alcun parametro, il cmdlet restituisce tutte le applicazioni del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm. Ogni applicazione viene identificata dal nome visualizzato, dal tipo di applicazione e dal GUID. Per visualizzare proprietà aggiuntive di un'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , aggiungere l'opzione format-list al cmdlet.  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-identity-spgeminiserviceapplicationpipebind"></a>-Identity \<SPGeminiServiceApplicationPipeBind >  
 Specifica l'applicazione di servizio da ottenere. Il valore deve essere un GUID valido tramite cui si identifica in modo univoco l'oggetto nella farm.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|true|  
|Accettare caratteri jolly?|false|  
  
### <a name="commonparameters"></a>\<Parametricomuni >  
 Questo cmdlet supporta i parametri comuni, ovvero Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer e OutVariable. Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|Nessuno|  
|Output|Nessuno|  
  
## <a name="example-1"></a>Esempio 1  
  
```  
C:\PS>Get-PowerPivotServiceApplication  
```  
  
 In questo esempio si restituiscono una o più applicazioni di servizio nella farm.  
  
## <a name="example-2"></a>Esempio 2  
  
```  
C:\PS>Get-PowerPivotServiceApplication | format-list  
```  
  
 Questo esempio restituisce tutte le proprietà di un'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
## <a name="example-3"></a>Esempio 3  
  
```  
C:\PS>get-PowerPivotServiceApplication -Identity 1234567-890a-bcde-fghijklm  
```  
  
 In questo esempio viene restituita una singola applicazione di servizio, mostrando il nome visualizzato, il tipo di applicazione e il GUID dell'applicazione. Se il nome visualizzato è lungo, viene troncato. Utilizzare l'opzione format-list per visualizzare il nome completo.  
  
  
