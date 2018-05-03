---
title: Cmdlet New-PowerPivotSystemServiceInstance | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b5d24b48d2c7b68f7408b5a3ad1da224cc992c3e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="new-powerpivotsystemserviceinstance-cmdlet"></a>Cmdlet New-PowerPivotSystemServiceInstance
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Aggiunge una nuova istanza del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] a un server applicazioni.  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
 **Applicabile a:** SharePoint 2010 e SharePoint 2013.  
  
## <a name="syntax"></a>Sintassi  
  
```  
New-PowerPivotSystemServiceInstance [[-ParentService] <PowerPivotMidTierServicePipeBind>] [-SystemServiceInstanceName <string>] [-Provision] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Con il cmdlet New-PowerPivotSystemServiceInstance è possibile effettuare il provisioning di un nuovo oggetto PowerPivotSystemService a livello di farm dopo aver usato il programma di installazione di SQL Server per installare [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint nel server applicazioni locale. È possibile eseguire il provisioning di una sola istanza del servizio in ogni server applicazioni.  Se è già stato eseguito il provisioning del servizio, non è possibile eseguire questo cmdlet.  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-parentservice-powerpivotmidtierservicepipebind"></a>-ParentService \<PowerPivotMidTierServicePipeBind >  
 Specifica il GUID dell'oggetto padre del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nella farm. In questa versione, è consentito un solo oggetto padre. È possibile utilizzare Get-PowerPivotSystemService per restituire l'oggetto servizio o il relativo GUID.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|true|  
|Accettare caratteri jolly?|false|  
  
### <a name="-systemserviceinstancename-string"></a>-SystemServiceInstanceName \<string>  
 Specifica un nome che identifica l'oggetto.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|1|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="provision-switchparameter"></a>Eseguire il provisioning [\<SwitchParameter >]  
 Rende disponibile il servizio in SharePoint. I valori validi sono $true o $false.  
  
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
C:\PS>New-PowerPivotSystemServiceInstance -Provision:$true  
```  
  
 In questo esempio si illustra la forma più comune del cmdlet. Registra il servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nel server applicazioni locale con la farm.  
  
## <a name="example-2"></a>Esempio 2  
  
```  
C:\PS>New-PowerPivotSystemServiceInstance -SystemServiceInstanceName "MyPSSInstance" -provision:$false  
```  
  
 In questo esempio si assegna un nome all'istanza del servizio di sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , ma senza effettuarne il provisioning. Se non si fornisce un nome, viene utilizzato il nome predefinito, Istanza del servizio di sistema SQL Server Analysis Services. La creazione di un nome personalizzato per il servizio è facoltativa. È possibile assegnare un nome al servizio per supportare scenari di test oppure se si dispone di uno strumento personalizzato o di uno script che consente di eseguire il provisioning dell'istanza in un passaggio successivo.  
  
  
