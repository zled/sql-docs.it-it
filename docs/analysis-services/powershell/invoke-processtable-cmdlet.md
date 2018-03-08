---
title: Cmdlet Invoke-ProcessTable | Documenti Microsoft
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
ms.assetid: 865e6d06-b99a-41f3-9d6f-c3c97b529b23
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e2a7f1392931ec5edd41803f6df6d98aa95403dd
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="invoke-processtable-cmdlet"></a>Cmdlet Invoke-ProcessTable
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Esegue l'operazione **Processo** su una **tabella** con uno specifico valore di **RefreshType**.  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
## <a name="syntax"></a>Sintassi  
 `Invoke-ProcessTable [-DatabaseName] <string> [-TableName] <string> [-RefreshType] <RefreshType> {Full |     ClearValues | Calculate | DataOnly | Automatic | Add | Defragment} [-Server <string>] [-Credential <pscredential>     [-WhatIf] [-Confirm]  [<CommonParameters>]`  
  
 `Invoke-ProcessTable -RefreshType <RefreshType> {Full | ClearValues | Calculate | DataOnly | Automatic | Add |     Defragment} -Table <Table> [-Server <string>] [-Credential <pscredential>] [-WhatIf] [-Confirm]     [<CommonParameters>]`  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-tablename-string"></a>-TableName \<stringa >  
 Nome della tabella a cui appartiene la partizione che deve essere elaborata.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-databasename-string"></a>-DatabaseName \<stringa >  
 Specifica il database a cui appartiene la tabella.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-servermicrosoftanalysissevicesserver"></a>-Server\<Microsoft.AnalysisSevices.Server>  
 Specifica facoltativamente l'istanza del server a cui connettersi se non si usa la directory del provider **SQLAS** per il contesto.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-refreshtype-microsoftanalysisservicesrefreshtype"></a>-RefreshType \<Microsoft.AnalysisServices.RefreshType>  
 Specifica il tipo di processo per un database tabulare.  I valori validi sono Full, ClearValues, Calculate, DataOnly, Automatic, Add e Defragment. Per descrizioni e indicazioni, vedere [Elaborare database, tabelle o partizioni &#40;Analysis Services&#41;](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md).  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|1|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-credential"></a>-Credential  
 Se questo parametro viene specificato, il nome utente e la password passati verranno usati per la connessione all'istanza di Analysis Services. Se non vengono specificate credenziali, verrà usato l'account di Windows predefinito dell'utente che esegue lo script.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-whatif"></a>-Whatif  
 Includere questo parametro per ottenere informazioni sull'impatto dell'operazione prima di eseguirla.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-confirm"></a>-Confirm  
 Includere questo parametro per confermare l'operazione in modo interattivo con una risposta di tipo Sì/No prima di eseguirla.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?||  
|Valore predefinito||  
|Accettare input da pipeline?||  
|Accettare caratteri jolly?|false|  
  
## <a name="example-1"></a>Esempio 1  
 `PS SQLSERVER:\SQLAS\MachineName\Instance\Databases\DB1\> Invoke-ProcessTable -TableName "myTable" -Database "DB1"  -RefreshType "Full"`  
  
 Questo comando invia pipe nell'identità della tabella da elaborare.  
  
## <a name="example-2"></a>Esempio 2  
 `PS SQLSERVER:\SQLAS\MachineName\Instance\Databases\DB1\> Invoke-ProcessTable -TableName "myTable" -Database "DB1"  -RefreshType [Microsoft.AnalysisServices.Tabular.RefreshType]::Full`  
  
 Questo comando elabora una tabella di metadati tabulari usando un tipo di aggiornamento **enum** .  
  
  
