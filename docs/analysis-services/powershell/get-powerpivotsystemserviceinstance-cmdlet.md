---
title: Il cmdlet Get-PowerPivotSystemServiceInstance | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 56027a8e-1949-4349-b616-68c8b1d2963c
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 569f03f0a1444d610462317a5ee19dc60f314d31
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="get-powerpivotsystemserviceinstance-cmdlet"></a>Cmdlet Get-PowerPivotSystemServiceInstance

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Restituisce una o più istanze di Servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in esecuzione nei server applicazioni nella farm.  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
 **Applicabile a:** SharePoint 2010 e SharePoint 2013.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Get-PowerPivotSystemServiceInstance [-Identity <PowerPivotMidTierServiceInstancePipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Il cmdlet Get-PowerPivotSystemServiceInstance restituisce le proprietà di una o più istanze di Servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in esecuzione nella farm. Il cmdlet fornisce informazioni su tipo di applicazione, stato (online o offline) e identità. Per visualizzare proprietà aggiuntive di un'istanza specifica, aggiungere il parametro Identity e l'opzione format-list al cmdlet.  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-identity-powerpivotmidtierserviceinstancepipebind"></a>-Identity \<PowerPivotMidTierServiceInstancePipeBind >  
 Specifica l'istanza del servizio da ottenere. Il valore deve essere un GUID valido che identifica in modo univoco l'oggetto nella farm.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|true|  
|Accettare caratteri jolly?|false|  
  
### <a name="commonparameters"></a>\<Parametricomuni >  
 Questo cmdlet supporta i parametri comuni, ovvero Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer e OutVariable. Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)  
  
## <a name="inputs-and-outputs"></a>Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|Nessuno|  
|Output|Nessuno|  
  
## <a name="example-1"></a>Esempio 1  
  
```  
C:\PS>Get-PowerPivotSystemServiceInstance -Identity 1234567-890a-bcde-fghijklm | format-list| format-list  
```  
  
 In questo esempio si restituiscono proprietà aggiuntive dell'istanza specificata, inclusi il nome, la versione e lo stato di aggiornamento del server.  
  
  
