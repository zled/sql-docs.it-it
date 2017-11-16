---
title: Cmdlet merge-Partition | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 15c7b069-897d-4bc8-a808-59cbeeabe4d8
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4103154c133a430d3725aa30c073ab5e386f5c3f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="merge-partition-cmdlet"></a>Cmdlet Merge-Partition

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Unisce i dati di una o più partizioni di origine in una partizione di destinazione, quindi elimina le partizioni di origine.  

>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
## <a name="syntax"></a>Sintassi  
 `Merge-ASDatabase [-Name] <string> [-SourcePartitions] <System.String[]> -Database <string> -Cube <string> -MeasureGroup <string> [-Server <string>] [-Credentials <PSCredential>] [<CommonParameters>]`  
  
 `Merge-ASDatabase -TargetPartition <Microsoft.AnalysisServices.Partition> [-SourcePartitions] <System.String[]> -Database <string> -Cube <string> -MeasureGroup <string> [-Server <string>] [-Credentials <PSCredential>] [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Il cmdlet Merge-Partition unisce i dati di una o più partizioni di origine in una partizione di destinazione, quindi elimina le partizioni di origine. Le partizioni possono essere unite solo se soddisfano tutti i criteri seguenti:  
  
-   Appartenenza delle partizioni allo stesso gruppo di misure.  
  
-   Appartenenza delle partizioni allo stesso computer.  
  
-   Condivisione della stessa modalità di archiviazione da parte delle partizioni (MOLAP, HOLAP e ROLAP per i database multidimensionali).  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-name-string"></a>-Nome \<stringa >  
 Specifica la partizione di destinazione in cui verranno uniti i dati della partizione di origine. È necessario che la partizione esista già.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-sourcepartition-string"></a>-SourcePartition \<stringa >  
 Specifica la partizione di origine che verrà unita alla partizione di destinazione. È possibile creare un elenco delimitato da virgole delle partizioni che si desidera unire. Utilizzare una variabile per archiviare l'elenco. Ad esempio, $Sources=”Sales_2008”, “Sales_2009”, “Sales_2010”.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|1|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-database-string"></a>-Database \<stringa >  
 Specifica il database a cui appartengono le partizioni.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-cube-string"></a>-Cubo \<stringa >  
 Specifica il cubo a cui appartengono le partizioni.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-measuregroup-string"></a>MeasureGroup - \<stringa >  
 Specifica il gruppo di misure a cui appartiene la partizione.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-server-string"></a>-Server \<stringa >  
 Specifica l'istanza di Analysis Services a cui il cmdlet deve connettersi per l'esecuzione. Se non viene fornito alcun nome del server, la connessione viene effettuata a localhost. Per le istanze predefinite è sufficiente specificare il nome del server, mentre per quelle denominate, utilizzare il formato nomeserver\nomeistanza. Per le connessioni HTTP, utilizzare il formato http[s]://server[:porta]/virtualdirectory/msmdpump.dll.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|localhost|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-credential-pscredential"></a>-Credential \<PSCredential >  
 Questo parametro è utilizzato per passare un nome utente e una password quando si utilizza una connessione HTTP a un'istanza di Analysis Services, se configurata per l'accesso HTTP. Per ulteriori informazioni, vedere [configura l'accesso HTTP ad Analysis Services in Internet Information Services &#40; IIS &#41; 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md) per le connessioni HTTP.  
  
 Se si specifica questo parametro, il nome utente e la password saranno utilizzati per connettersi all'istanza di Analysis Services specificata. Se non viene specificata alcuna credenziale, verrà utilizzato l'account predefinito di Windows dell'utente che sta eseguendo lo strumento.  
  
 Per usare questo parametro, creare innanzitutto un oggetto PSCredential usando Get-Credential per specificare il nome utente e la password, ad esempio, `$Cred=Get-Credential “adventure-works\bobh”`. Successivamente è possibile inoltrare tramite pipe questo oggetto al parametro -Credential `(-Credential:$Cred`.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|True (ByValue)|  
|Accettare caratteri jolly?|false|  
  
### <a name="-targetpartition-microsoftanalysisservicespartition"></a>-TargetPartition \<AnalysisServices >  
 Specifica la partizione di destinazione a cui verranno unite le partizioni di origine.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|true|  
|Accettare caratteri jolly?|false|  
  
### <a name="commonparameters"></a>\<Parametricomuni >  
 In questo cmdlet vengono supportati i parametri comuni: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable. Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|System.string|  
|Output|Nessuno|  
  
## <a name="example-1"></a>Esempio 1  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups\sales orders\partitions> $Source=”Total_Orders_2001”, “Total_Orders_2002”, “Total_Orders_2003”` `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups\sales orders\partitions> Merge-Partition –Name “Total_Orders_2004” –SourcePartitions:$Source –database “AWTEST” –cube “Adventure Works” –MeasureGroup “Sales Orders”`  
  
 Questo comando unisce le partizioni del 2001, 2002 e 2003 nella partizione del 2004, quindi elimina le partizioni degli anni precedenti.  
  

  

