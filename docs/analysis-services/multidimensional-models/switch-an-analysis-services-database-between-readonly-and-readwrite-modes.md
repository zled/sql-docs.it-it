---
title: "Passare a un database di Analysis Services tra le modalità ReadOnly e ReadWrite | Documenti Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ReadOnly property
- ReadWriteMode command
- operations [Analysis Services - multidimensional data]
ms.assetid: 4eff8181-08dd-4fad-b091-d400fc21a020
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 11eaa65564dcd59442bd8b111c0de009b00e8fd4
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="switch-an-analysis-services-database-between-readonly-and-readwrite-modes"></a>Passare un database di Analysis Services tra le modalità ReadOnly e ReadWrite
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Gli amministratori del database possono cambiare la modalità di lettura/scrittura di un database tabulare o multidimensionale nell'ambito di un'operazione di più ampio respiro per la distribuzione di un carico di lavoro di query tra più server usati solo per le query.  
  
 In un database è possibile passare da una modalità all'altra in vari modi. In questo documento vengono illustrati gli scenari comuni seguenti:  
  
-   In modo interattivo tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   A livello di programmazione tramite AMO  
  
-   Tramite script usando XMLA o TMSL  
  
## <a name="switch-the-readwrite-mode-of-a-database-interactively-using-management-studio"></a>Attivare la modalità lettura/scrittura di un database in modo interattivo tramite Management Studio  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse sul database, quindi scegliere **Proprietà**.  
  
     Prendere nota del percorso. Un percorso di archiviazione del database vuoto indica che la cartella del database si trova nella cartella di dati del server.  
  
2.  Fare clic con il pulsante destro del mouse sul database, quindi scegliere **Scollega**  
  
3.  Assegnare una password al database da scollegare, quindi fare clic su **OK** per eseguire il comando.  
  
4.  In Esplora oggetti fare clic con il pulsante destro del mouse sulla cartella **Database** e scegliere **Collega**  
  
5.  Nella casella di testo **cartella** digitare il percorso originale della cartella del database. In alternativa, è possibile usare il pulsante Sfoglia (**...**) per individuare la cartella del database.  
  
6.  Selezionare la modalità di lettura/scrittura per il database.  
  
7.  Digitare la password e fare clic su **OK** per eseguire il comando di collegamento.  
  
## <a name="switch-the-readwrite-mode-to-a-database-programmatically-using-amo"></a>Attivare la modalità lettura/scrittura di un database a livello di programmazione tramite AMO  
 Nell'applicazione C# richiamare `SwitchReadWrite()` con i parametri necessari. Compilare ed eseguire il codice per spostare il database.  
  
```  
private void SwitchReadWrite(Server server, string dbName, ReadWriteMode dbReadWriteMode)  
{  
    if (server.Databases.ContainsName(dbName))  
    {  
        Database db;  
        string databaseLocation;  
        db = server.Databases[dbName];  
        databaseLocation = db.DbStorageLocation;  
  
              if (databaseLocation == null)  
            {  
                 string dataDir = server.ServerProperties["DataDir"].Value;  
                 string dataDir = server.ServerProperties["DataDir"].Value;  
                 string dataDir = server.ServerProperties["DataDir"].Value;  
  
    String[] possibleFolders = Directory.GetDirectories(dataDir, string.Concat(dbName,"*"), SearchOption.TopDirectoryOnly);  
  
   if (possibleFolders.Length > 1)  
         {  
         List<String> sortedFolders = new List<string>(possibleFolders.Length);  
         sortedFolders.AddRange(possibleFolders);  
         sortedFolders.Sort();  
         databaseLocation = sortedFolders[sortedFolders.Count - 1];  
         }  
         else  
         {  
         databaseLocation = possibleFolders[0];  
          }  
        }  
    db.Detach();  
    server.Attach(databaseLocation, dbReadWriteMode);  
    }  
}  
  
```  
  
## <a name="switch-the-readwrite-mode-to-a-database-by-script-using-xmla"></a>Attivare la modalità lettura/scrittura di un database tramite script usando XMLA  
 Le istruzioni seguenti si applicano a database multidimensionali e tabulari in modalità di compatibilità 1050, 1100 o 1103.  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse sul database, quindi scegliere **Proprietà**.  
  
     Prendere nota del percorso. Un percorso di archiviazione del database vuoto indica che la cartella del database si trova nella cartella di dati del server.  
  
2.  Fare clic con il pulsante destro del mouse sul database, quindi scegliere **Scollega**  
  
3.  Aprire una nuova scheda XMLA in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
4.  Copiare il modello di script seguente per XMLA:  
  
    ```  
    <Detach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
       <Object>  
          <DatabaseID>%dbName%</DatabaseID>  
          <Password>%password%</Password>  
       </Object>  
    </Detach>  
    ```  
  
5.  Sostituire `%dbName%` con il nome del database e `%password%` con la password. I caratteri % fanno parte del modello e devono essere rimossi.  
  
6.  Eseguire il comando XMLA.  
  
7.  Copiare il modello di script seguente per XMLA in una nuova scheda XMLA:  
  
    ```  
    <Attach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
       <Folder>%dbFolder%</Folder>  
       <ReadWriteMode xmlns="http://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>  
    </Attach>  
    ```  
  
8.  Sostituire `%dbFolder%` con il percorso completo in formato UNC della cartella del database, `%ReadOnlyMode%` con il valore **ReadOnly** o **ReadWrite**corrispondente e `%password%` con la password. I caratteri % fanno parte del modello e devono essere rimossi.  
  
9. Eseguire il comando XMLA.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Disponibilità elevata e scalabilità in Analysis Services](../../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md)   
 [Collegamento e scollegamento di database di Analysis Services](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Percorso di archiviazione del database](../../analysis-services/multidimensional-models/database-storage-location.md)   
 [Proprietà readwritemode del database](../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Elemento Attach](../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [Elemento Detach](../../analysis-services/xmla/xml-elements-commands/detach-element.md)   
 [Elemento ReadWriteMode](../../analysis-services/xmla/xml-elements-properties/readwritemode-element.md)   
 [Dbstoragelocation-elemento](../../analysis-services/xmla/xml-elements-properties/dbstoragelocation-element.md)  
  
  

