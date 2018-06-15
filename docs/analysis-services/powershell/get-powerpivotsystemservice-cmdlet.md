---
title: Il cmdlet Get-PowerPivotSystemService | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c2a955a9d9b91521adc6abfcdd5af4109958fa8f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037485"
---
# <a name="get-powerpivotsystemservice-cmdlet"></a>Cmdlet Get-PowerPivotSystemService
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Restituisce le proprietà globali dell'oggetto del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in una farm. 

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
 **Applicabile a:** SharePoint 2010 e SharePoint 2013.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Get-PowerPivotSystemService [-Identity <PowerPivotMidTierServicePipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Il cmdlet Get-PowerPivotSystemService restituisce le proprietà globali dell'oggetto del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in una farm. È presente un oggetto padre per farm, ma ogni farm può avere più istanze del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in esecuzione nei singoli server applicazioni nella farm. L'oggetto padre indica le impostazioni a livello di farm che non variano in base all'istanza. Se nella farm sono incluse più installazioni di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint, un elenco delimitato da virgole delle istanze indica il numero di istanze del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] presenti nella farm.  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-identity-powerpivotmidtierservicepipebind"></a>-Identity \<PowerPivotMidTierServicePipeBind >  
 Specifica l'oggetto padre da ottenere. Il valore deve essere un GUID valido tramite cui si identifica in modo univoco l'oggetto nella farm.  
  
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
C:\PS>Get-PowerPivotSystemService  
```  
  
 Questo esempio restituisce le proprietà globali dell'oggetto padre, mostrando le proprietà condivise da tutte le istanze del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm.  
  
  
