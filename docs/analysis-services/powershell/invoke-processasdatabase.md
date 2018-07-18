---
title: Invoke-ProcessASDatabase | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 44a5654207e84f3488c66b3bc9cfab4778b51acb
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="invoke-processasdatabase"></a>Invoke-ProcessASDatabase
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Esegue l'operazione **Process** su un **Database** specificato con un valore **ProcessType** o **RefreshType** specifico a seconda dei valori dei metadati sottostanti.  
  
 Usare **ProcessType** per i database con metadati multidimensionali. Sono inclusi i database tabulari con livello di compatibilità 1050, 1100 o 1103.  
  
 Usare **RefreshType** per i database tabulari con livello di compatibilità 1200 o superiore.  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
## <a name="syntax"></a>Sintassi  
 `Invoke-ProcessASDatabase [-DatabaseName] <string> [-RefreshType] <RefreshType> {Full | ClearValues | Calculate |     DataOnly | Automatic | Add | Defragment} [-Server <string>] [-Credential <pscredential>] [-WhatIf] [-Confirm]     [<CommonParameters>]`  
  
 `Invoke-ProcessASDatabase [-DatabaseName] <string> [-ProcessType] <ProcessType> {ProcessFull | ProcessAdd |     ProcessUpdate | ProcessIndexes | ProcessData | ProcessDefault | ProcessClear | ProcessStructure |     ProcessClearStructureOnly | ProcessScriptCache | ProcessRecalc | ProcessDefrag} [-Server <string>] [-Credential     <pscredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Il cmdlet **Invoke-ProcessASDatabase** elabora un database al livello specificato. Per i database tabulari con livello di compatibilità 1200, ad esempio, l'impostazione di **RefreshType** su **Full** consente di sovrascrivere i dati esistenti con i nuovi dati.  
  
 Il tipo di elaborazione (multidimensionale) o il tipo di aggiornamento (tabulare) è obbligatorio e può essere specificato prima o dopo i parametri del database e del server:  
  
-   Per il modello multidimensionale, vedere [Opzioni e impostazioni di elaborazione &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
-   Per il modello tabulare, vedere [Elaborare database, tabelle o partizioni &#40;Analysis Services&#41;](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md).  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-databasename-string"></a>-DatabaseName \<stringa >  
 Specifica il database tabulare o multidimensionale da elaborare.  
  
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
  
### <a name="-refreshtype-microsoftanalysisservicesrefreshtype"></a>-RefreshType \<Microsoft.AnalysisServices.RefreshType >  
 Specifica il tipo di processo per un database tabulare.  I valori validi sono Full, ClearValues, Calculate, DataOnly, Automatic, Add e Defragment. Per descrizioni e indicazioni, vedere [Elaborare database, tabelle o partizioni &#40;Analysis Services&#41;](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md).  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|1|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-processtype-microsoftanalysisservicesprocesstype"></a>-ProcessType \<Microsoft.AnalysisServices.ProcessType>  
 Specifica il tipo di elaborazione per un database multidimensionale con livello di compatibilità da 1050 a 1103. I valori validi sono ProcessFull, ProcessAdd, ProcessUpdate, ProcessIndexes, ProcessData, ProcessDefault, ProcessClear, ProcessStructure, ProcessCelarStructureOnly, ProcessScriptCache o ProcessRecalc. Per descrizioni e indicazioni, vedere [Opzioni e impostazioni di elaborazione &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
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
  
## <a name="-whatif"></a>-Whatif  
 Includere questo parametro per ottenere informazioni sull'impatto dell'operazione prima di eseguirla.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
## <a name="-confirm"></a>-Confirm  
 Includere questo parametro per confermare l'operazione in modo interattivo con una risposta di tipo Sì/No prima di eseguirla.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?||  
|Valore predefinito||  
|Accettare input da pipeline?||  
|Accettare caratteri jolly?|false|  
  
## <a name="example-1-sqlas-provider"></a>Esempio 1 (provider SQLAS)  
 Questo esempio usa il provider **SQLAS** per impostare il contesto sull'elenco di database in un'istanza predefinita.  Se si elenca il contenuto della directory dei database, verranno visualizzati tutti i database con il relativo stato del processo e la modalità di lettura-scrittura.  
  
 Dalla cartella di database, è possibile eseguire **Invoke-ProcessASDatabase** specificando solo il nome del database.  
  
```  
PS > import-module SQLPS -DisableNameChecking  
PS  SQL Server > cd sqlas\ssas-srv-01\default\databases  
PS SQLSERVER:\sqlas\ssas-srv-01\default\databases> dir  
. . . .  
PS SQLSERVER:\sqlas\ssas-srv-01\default\databases> Invoke-ProcessASDatabase "adventureworks"  
  
```  
  
 A seconda del tipo di database, verrà richiesto di specificare un valore **RefreshType** o **ProcessType**.  
  
 L'elaborazione viene confermata dalla presenza di un oggetto di impatto nell'istruzione return: Microsoft.AnalysisServices.Tabular.ObjectImpact.  
  
 Si noti che le informazioni sullo stato dell'oggetto a volte vengono memorizzate nella cache. Questo significa che se si elenca il contenuto di una directory dopo il completamento dell'elaborazione, lo stato del database mantiene il relativo descrittore 'non elaborato' originale. L'informazione è fuorviante perché la restituzione di ObjectImpact indica che il database è stato in effetti elaborato.  
  
 È possibile verificare il completamento dell'elaborazione nella pagina delle proprietà del database in Management Studio, avviando una nuova sessione oppure tramite la restituzione dello stato di elaborazione da un oggetto database (tramite [Microsoft.AnalysisServices.ProcessableMajorObject.LastProcessed](https://msdn.microsoft.com/library/microsoft.analysisservices.processablemajorobject.lastprocessed.aspx)).  
  
## <a name="example-2"></a>Esempio 2  
 Questo esempio illustra la stessa operazione usando però solo il cmdlet senza il provider. Sono necessari ulteriori parametri per specificare il tipo di server e il tipo di elaborazione.  
  
```  
PS > import-module SQLPS -DisableNameChecking  
PS  SQL Server >  Invoke-ProcessASDatabase -databasename "AdventureWorks" -server '\\server-name\instancename' –ProcessType "ProcessFull"  
  
```  
  
  
  
