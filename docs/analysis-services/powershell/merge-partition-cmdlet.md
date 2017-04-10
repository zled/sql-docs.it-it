---
title: "Cmdlet Merge-Partition | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 15c7b069-897d-4bc8-a808-59cbeeabe4d8
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Cmdlet Merge-Partition
  Unisce i dati di una o più partizioni di origine in una partizione di destinazione, quindi elimina le partizioni di origine.  
  
## Sintassi  
 `Merge-ASDatabase [-Name] <string> [-SourcePartitions] <System.String[]> -Database <string> -Cube <string> -MeasureGroup <string> [-Server <string>] [-Credentials <PSCredential>] [<CommonParameters>]`  
  
 `Merge-ASDatabase -TargetPartition <Microsoft.AnalysisServices.Partition> [-SourcePartitions] <System.String[]> -Database <string> -Cube <string> -MeasureGroup <string> [-Server <string>] [-Credentials <PSCredential>] [<CommonParameters>]`  
  
## Description  
 Il cmdlet Merge-Partition unisce i dati di una o più partizioni di origine in una partizione di destinazione, quindi elimina le partizioni di origine. Le partizioni possono essere unite solo se soddisfano tutti i criteri seguenti:  
  
-   Appartenenza delle partizioni allo stesso gruppo di misure.  
  
-   Appartenenza delle partizioni allo stesso computer.  
  
-   Condivisione della stessa modalità di archiviazione da parte delle partizioni (MOLAP, HOLAP e ROLAP per i database multidimensionali).  
  
## Parametri  
  
### -Name \<string>  
 Specifica la partizione di destinazione in cui verranno uniti i dati della partizione di origine. È necessario che la partizione esista già.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -SourcePartition \<string>  
 Specifica la partizione di origine che verrà unita alla partizione di destinazione. È possibile creare un elenco delimitato da virgole delle partizioni che si desidera unire. Utilizzare una variabile per archiviare l'elenco. Ad esempio, $Sources=”Sales_2008”, “Sales_2009”, “Sales_2010”.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|1|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Database \<string>  
 Specifica il database a cui appartengono le partizioni.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Cube \<string>  
 Specifica il cubo a cui appartengono le partizioni.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -MeasureGroup \<string>  
 Specifica il gruppo di misure a cui appartiene la partizione.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Server \<string>  
 Specifica l'istanza di Analysis Services a cui il cmdlet deve connettersi per l'esecuzione. Se non viene fornito alcun nome del server, la connessione viene effettuata a localhost. Per le istanze predefinite è sufficiente specificare il nome del server, mentre per quelle denominate, utilizzare il formato nomeserver\nomeistanza. Per le connessioni HTTP, utilizzare il formato http[s]://server[:porta]/virtualdirectory/msmdpump.dll.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|localhost|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### -Credential \<PSCredential>  
 Questo parametro è utilizzato per passare un nome utente e una password quando si utilizza una connessione HTTP a un'istanza di Analysis Services, se configurata per l'accesso HTTP. Per altre informazioni, vedere [Configurare l'accesso HTTP ad Analysis Services in Internet Information Services &#40;IIS&#41; 8.0](../../analysis-services/instances/configure http access to analysis services on iis 8.0.md) e [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md) (Script di PowerShell in Analysis Services) per le connessioni HTTP.  
  
 Se si specifica questo parametro, il nome utente e la password saranno utilizzati per connettersi all'istanza di Analysis Services specificata. Se non viene specificata alcuna credenziale, verrà utilizzato l'account predefinito di Windows dell'utente che sta eseguendo lo strumento.  
  
 Per usare questo parametro, creare innanzitutto un oggetto PSCredential usando Get-Credential per specificare il nome utente e la password, ad esempio, `$Cred=Get-Credential “adventure-works\bobh”`. Successivamente è possibile inoltrare tramite pipe questo oggetto al parametro -Credential `(-Credential:$Cred`.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|True (ByValue)|  
|Accettare caratteri jolly?|false|  
  
### -TargetPartition \<Microsoft.AnalysisServices.Partition>  
 Specifica la partizione di destinazione a cui verranno unite le partizioni di origine.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|true|  
|Accettare caratteri jolly?|false|  
  
### \<CommonParameters>  
 In questo cmdlet vengono supportati i parametri comuni: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable. Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|System.string|  
|Output|Nessuno|  
  
## Esempio 1  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups\sales orders\partitions> $Source=”Total_Orders_2001”, “Total_Orders_2002”, “Total_Orders_2003”` `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups\sales orders\partitions> Merge-Partition –Name “Total_Orders_2004” –SourcePartitions:$Source –database “AWTEST” –cube “Adventure Works” –MeasureGroup “Sales Orders”`  
  
 Questo comando unisce le partizioni del 2001, 2002 e 2003 nella partizione del 2004, quindi elimina le partizioni degli anni precedenti.  
  
## Vedere anche  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Post sulla gestione dei modelli tabulari tramite PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  