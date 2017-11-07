---
title: Il cmdlet Remove-PowerPivotSystemServiceInstance | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bc46094a-5584-47ba-8883-77dc79373a5d
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e44d28106db0c14c293c463d91125b262190350d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="remove-powerpivotsystemserviceinstance-cmdlet"></a>Cmdlet Remove-PowerPivotSystemServiceInstance

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Rimuove un'istanza del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dalla farm.  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
 **Applicabile a:** SharePoint 2010 e SharePoint 2013.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Remove-PowerPivotSystemServiceInstance [-Confirm <switch>] [-DeleteLocal <switch>] [-Identity <PowerPivotMidTierServiceInstancePipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Con il cmdlet Remove-PowerPivotSystemServiceInstance è possibile rimuovere informazioni sull'istanza relative al servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dalla farm. Non vengono rimossi i file di programma. Per rimuovere in modo permanente i file di programma, è necessario disinstallarli.  
  
 Se si rimuove il servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , assicurarsi di eseguire anche Remove-PowerPivotEngineServiceInstance per rimuovere l'istanza di Analysis Services associata, seguito da Remove-PowerPivotServiceApplication per eliminare tutte le applicazioni PowerPivotservice. Le applicazioni di servizio non verranno più eseguite dopo la rimozione dei servizi.  
  
 Per annullare questa modifica, è possibile eseguire New-PowerPivotSystemServiceInstance -Provision:$true per abilitare nuovamente le informazioni sull'istanza.  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-identity-powerpivotmidtierserviceinstancepipebind"></a>-Identity \<PowerPivotMidTierServiceInstancePipeBind >  
 Specifica il GUID dell'istanza del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] da rimuovere. È disponibile una sola istanza del servizio in ogni server applicazioni con un'installazione di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|true|  
|Accettare caratteri jolly?|false|  
  
### <a name="-deletelocal-switch"></a>-DeleteLocal \<passare >  
 Elimina l'istanza del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] installata nel computer locale, permettendo di rimuovere l'istanza senza dover specificare un'identità dell'oggetto.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-confirm-switch"></a>-Confirm \<passare >  
 Richiede la conferma dell'utente prima dell'esecuzione del comando. Questo valore è abilitato per impostazione predefinita. Per ignorare la risposta di conferma in un comando, specificare Confirm:$false nel comando.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
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
C:\PS>Remove-PowerPivotSystemServiceInstance -deletelocal  
```  
  
 In questo esempio si illustra come rimuovere l'istanza del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in esecuzione nel server applicazioni locale.  
  
## <a name="example-2"></a>Esempio 2  
  
```  
C:\PS>Remove-PowerPivotSystemServiceInstance -identity 1234567-890a-bcde-fghijklmn  
```  
  
 Questo esempio mostra come eliminare un servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] specifico in base alla relativa identità.  
  
  

