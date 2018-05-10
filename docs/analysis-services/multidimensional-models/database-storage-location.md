---
title: Percorso di archiviazione del database | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f3b40e3d3a674b3e6005db13957c98c0029209bc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="database-storage-location"></a>Percorso di archiviazione dei database
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Spesso, un amministratore del database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] desidera che un determinato database risieda al di fuori della cartella di dati del server. Queste situazioni sono il più delle volte determinate da esigenze aziendali, ad esempio il miglioramento delle prestazioni o l'ampliamento dello spazio di archiviazione. In questi casi, la proprietà di database **DbStorageLocation** consente all'amministratore di database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] di specificare il percorso dei database in un disco locale o in un dispositivo di rete.  
  
## <a name="dbstoragelocation-database-property"></a>Proprietà di database DbStorageLocation  
 La proprietà di database **DbStorageLocation** specifica la cartella in cui vengono creati e gestiti tutti i file di dati e di metadati dei database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Tutti i file di metadati vengono archiviati nella cartella **DbStorageLocation** , ad eccezione del file di metadati del database, che viene archiviato nella cartella di dati del server. Per l'impostazione del valore della proprietà di database **DbStorageLocation** , è necessario considerare due fattori importanti:  
  
-   La proprietà di database **DbStorageLocation** deve essere impostata su un percorso di cartella in formato UNC esistente o su una stringa vuota. Una stringa vuota è il valore predefinito per la cartella di dati del server. Se la cartella non esiste, quando si esegue un comando **Create**, **Attach**o **Alter** verrà generato un errore.  
  
-   Inoltre, la proprietà di database **DbStorageLocation** non può essere impostata in modo che punti a una cartella di dati del server o a una delle relative sottocartelle. Se il percorso punta alla cartella di dati del server o a una delle relative sottocartelle, quando si esegue un comando **Create**, **Attach**o **Alter** verrà generato un errore.  
  
> [!IMPORTANT]  
>  È consigliabile impostare il percorso UNC per l'utilizzo di una rete SAN (Storage Area Network) basata su iSCSI o di un disco collegato localmente. Qualsiasi percorso UNC di una condivisione di rete o qualsiasi soluzione di archiviazione remota a latenza elevata produce un'installazione non supportata.  
  
### <a name="dbstoragelocation-compared-to-storagelocation"></a>Confronto tra DbStorageLocation e StorageLocation  
 **DbStorageLocation** specifica la cartella in cui risiedono tutti i file di dati e di metadati del database, mentre **StorageLocation** specifica la cartella in cui risiedono una o più partizioni di un cubo. **StorageLocation** può essere impostata in modo indipendente da **DbStorageLocation**. Si tratta di una decisione dell'amministratore di database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in base ai risultati previsti. Spesso le due proprietà vengono usate in modo sovrapposto.  
  
## <a name="dbstoragelocation-usage"></a>Utilizzo di DbStorageLocation  
 La proprietà di database **DbStorageLocation** viene usata come parte di un comando di database **Create** , in una sequenza di comandi di database **Detach**/**Attach** , in una sequenza di comandi di database **Backup**/**Restore** o in un comando di database **Synchronize** . La modifica della proprietà di database **DbStorageLocation** è considerata una modifica strutturale nell'oggetto di database, ovvero è necessario ricreare tutti i metadati e rielaborare tutti i dati.  
  
> [!IMPORTANT]  
>  Non è consigliabile modificare il percorso di archiviazione dei database tramite un comando **Alter** . È invece consigliabile usare una sequenza di comandi di database **Detach**/**Attach** comandi di (vedere [Spostare un database di Analysis Services](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md), [Collegamento e scollegamento di database di Analysis Services](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Collegamento e scollegamento di database di Analysis Services](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Spostare un Database di Analysis Services](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [Dbstoragelocation-elemento](../../analysis-services/xmla/xml-elements-properties/dbstoragelocation-element.md)   
 [Creare l'elemento & #40; XMLA & #41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)   
 [Elemento Attach](../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [Sincronizzare elemento & #40; XMLA & #41;](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)  
  
  
