---
title: Il cmdlet Update-PowerPivotSystemService | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a90f1158-68d3-4330-98c1-fb0f81e13328
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 92b1c88166578605f0060ac65278d13ab4c42864
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="update-powerpivotsystemservice-cmdlet"></a>Cmdlet Update-PowerPivotSystemService

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Aggiorna l'oggetto padre del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm.  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
 **Applicabile a:** SharePoint 2010 e SharePoint 2013.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Update-PowerPivotSystemService [-Confirm <switch>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Con il cmdlet **Update-PowerPivotSystemService** è possibile eseguire una serie di azioni di aggiornamento sull'oggetto padre di Servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , sulle istanze e sulle applicazioni del servizio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm. Tutti i servizi e le applicazioni di livello intermedio in una distribuzione di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint devono essere in esecuzione allo stesso livello funzionale. Questo cmdlet consente di eseguire le azioni di aggiornamento su tutti questi oggetti.  
  
 Eseguire questo cmdlet dopo il programma di installazione di SQL Server per installare una versione più recente di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint oppure se è stato applicato un aggiornamento cumulativo nel server. Per controllare se è necessario un aggiornamento, eseguire `Get-PowerPivotSystemService` per analizzare la proprietà **NeedsUpgrade** . Se **NeedsUpgrade** è true, è consigliabile eseguire il cmdlet per aggiornare gli oggetti [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] di livello intermedio nella farm.  
  
 Dal momento che in una distribuzione di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint sono inclusi servizi dati di livello intermedio e di back-end, è necessario eseguire **Update-PowerPivotEngineService** quando si esegue **Update-PowerPivotSystemService** per assicurarsi che entrambi i livelli abbiano la stessa versione nella farm.  
  
 Non è possibile eseguire il rollback dell'aggiornamento alla versione precedente. Se è necessario ripristinare una versione precedente, rimuovere [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dalla farm di SharePoint e reinstallare il software. Per verificare se l'operazione di aggiornamento viene completata correttamente, eseguire `Get-PowerPivotSystemService` per analizzare le proprietà globali per informazioni sulla versione e per verificare che la proprietà **NeedsUpgrade** non sia più impostata su true.  
  
## <a name="parameters"></a>Parametri  
  
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
 Questo cmdlet supporta i parametri seguenti:  
  
-   Dettagliato  
  
-   Debug  
  
-   ErrorAction  
  
-   ErrorVariable  
  
-   WarningAction  
  
-   WarningVariable  
  
-   OutBuffer  
  
-   OutVariable  
  
 Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|Nessuno|  
|Output|Nessuno|  
  
  
