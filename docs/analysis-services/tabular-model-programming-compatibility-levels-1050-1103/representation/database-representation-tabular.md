---
title: Database (tabulare) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 16a233fb-f83b-4ca1-acb5-6186eca0a62c
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 69ca2b7cadbb70a8728fda2e631d5df57efbda76
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="database-representationtabular"></a>Rappresentazione del database(tabulare)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
In modalità tabulare, il database è il contenitore per tutti gli oggetti nel modello tabulare.  
  
## <a name="database-representation"></a>Rappresentazione di un database  
 Il database è il posto dove si trovano tutti gli oggetti che formano un modello tabulare. All'interno del database lo sviluppatore trova oggetti come connessioni, tabelle, ruoli e molti altri ancora.  
  
### <a name="database-in-amo"></a>Database in AMO  
 Quando si utilizza AMO (Analysis Management Objects) per gestire un database modello tabulare, l'oggetto <xref:Microsoft.AnalysisServices.Database> ha una corrispondenza uno-a-uno in AMO (Analysis Management Objects) con l'oggetto logico del database in un modello tabulare.  
  
> [!NOTE]  
>  Per accedere a un oggetto di database, in AMO (Analysis Management Objects) l'utente deve avere accesso a un oggetto server e connettersi.  
  
### <a name="database-in-adomdnet"></a>Database in ADOMD.Net  
 Quando si utilizza ADOMD per consultare ed eseguire una query su un database modello tabulare, la connessione a un database specifico si ottiene mediante l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 È possibile connettersi direttamente a un determinato database utilizzando il seguente frammento di codice:  
  
```csharp  
using ADOMD = Microsoft.AnalysisServices.AdomdClient;  
…  
   ADOMD.AdomdConnection currrentCnx = new ADOMD.AdomdConnection("Data Source=<<server\instance>>;Catalog=<<database>>");  
   currrentCnx.Open();  
…  
  
```  
  
 Inoltre, tramite un oggetto connessione esistente (che non è stato chiuso) è possibile passare dal database corrente a un altro come mostrato nel seguente frammento di codice:  
  
```csharp  
currentCnx.ChangeDatabase("myOtherDatabase");  
  
```  
  
## <a name="database-in-amo"></a>Database in AMO  
 Quando si utilizza AMO per gestire un oggetto di database, iniziare con un oggetto <xref:Microsoft.AnalysisServices.Server>. Quindi cercare il database nella raccolta di database oppure creare un nuovo database aggiungendone uno alla raccolta.  
  
 Nel frammento di codice seguente vengono illustrati i passaggi per connettersi a un server e creare un database vuoto, dopo avere verificato che il database non esista già:  
  
```  
  
AMO.Server CurrentServer = new AMO.Server();  
try  
{  
    CurrentServer.Connect(currentServerName);  
}  
catch (Exception cnxException)  
{  
    MessageBox.Show(string.Format("Error while trying to connect to server: [{0}]\nError message: {1}", currentServerName, cnxException.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    return;  
}  
newDatabaseName = DatabaseName.Text;  
if (CurrentServer.Databases.Contains(newDatabaseName))  
{  
    return;  
}  
try  
{  
    AMO.Database newDatabase = CurrentServer.Databases.Add(newDatabaseName);  
  
    CurrentServer.Update();  
}  
catch (Exception createDBxc)  
{  
    MessageBox.Show(String.Format("Database [{0}] couldn't be created.\n{1}", newDatabaseName, createDBxc.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    newDatabaseAvailable = false;  
}  
  
```  
  
 Per comprendere come utilizzare AMO per creare e modificare le rappresentazioni di database, vedere il codice sorgente nell'esempio di Tabular AMO 2012; in particolare controllare nel seguente file di origine: Database.cs. L'esempio è disponibile in Codeplex. Il codice di esempio viene fornito solo come supporto ai concetti logici illustrati in questo argomento e non deve essere utilizzato in un ambiente di produzione.  
  
  
