---
title: Il cmdlet Remove-PowerPivotServiceApplication | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2742b2a3-927c-4e7c-bd7d-43c072fa01ab
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7078a7733c7764b77667628071c66c8313aae85a
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="remove-powerpivotserviceapplication-cmdlet"></a>Cmdlet Remove-PowerPivotServiceApplication
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Elimina un'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
 **Applicabile a:** SharePoint 2010 e SharePoint 2013.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Remove-PowerPivotServiceApplication [-Identity <SPGeminiServiceApplicationPipeBind>] [-DeleteAll <switch>] [-RemoveData <switch>] [-Confirm <switch>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Con il cmdlet Remove-PowerPivotServiceApplication è possibile eliminare un'applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dalla farm. Utilizzare DeleteAll per eliminare immediatamente tutte le applicazioni di servizio oppure utilizzare il parametro Identity per rimuovere una singola istanza. Per ottenere informazioni sull'istanza, eseguire Get-PowerPivotServiceApplication per restituire tutte le istanze nella farm.  
  
 Utilizzare il parametro RemoveData per rimuovere facoltativamente i database dell'applicazione di servizio e i file memorizzati nella cache. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] - Le cartelle di lavoro rimangono nelle raccolte contenuto, ma non sono più funzionali dopo la rimozione dell'applicazione del servizio.  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-identity-spgeminiserviceapplicationpipebind"></a>-Identity \<SPGeminiServiceApplicationPipeBind >  
 Specifica il GUID di una singola applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm. È necessario specificare il GUID se si desidera rimuovere solo un'applicazione, lasciando invariate le altre applicazioni di servizio.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|true|  
|Accettare caratteri jolly?|false|  
  
### <a name="-confirm-switch"></a>-Confirm \<switch>  
 Richiede la conferma dell'utente prima dell'esecuzione del comando. Questo valore è abilitato per impostazione predefinita. Per ignorare la risposta di conferma in un comando, specificare Confirm:$false nel comando.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-deleteall-switch"></a>DeleteAll - \<passare >  
 Elimina tutte le applicazioni del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] senza eliminare il database dell'applicazione del servizio, né gli oggetti dell'istanza del servizio nella farm. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Le istanze degli oggetti del servizio di sistema e del servizio motore [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] rimangono, ma gli oggetti non possono essere usati dopo la rimozione delle applicazioni del servizio.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-removedata-switch"></a>-RemoveData \<switch>  
 Consente di rimuovere il database dell'applicazione di servizio contenente le pianificazioni di aggiornamento dati, i dati di utilizzo delle cartelle di lavoro, le mappe dell'istanza utilizzate per tenere traccia dei database caricati e altri dati interni.  
  
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
C:\PS>Remove-PowerPivotServiceApplication -identity 12345678-90ab-cdef-ghijklmnop  
```  
  
 Questo esempio elimina una singola applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , ma non il relativo database o la cache. Se non si specifica un'identità, viene richiesto di fornirne una.  
  
## <a name="example-2"></a>Esempio 2  
  
```  
C:\PS>Remove-PowerPivotServiceApplication -DeleteAll  
```  
  
 Questo esempio elimina tutte le applicazioni del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm. Database e cache non vengono eliminati.  
  
## <a name="example-3"></a>Esempio 3  
  
```  
CC:\PS>Remove-PowerPivotServiceApplication -identity 12345678-90ab-cdef-ghijklmnop -RemoveData  
```  
  
 Questo esempio elimina una singola applicazione del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] insieme ai relativi database e file di cache.  
  
  
