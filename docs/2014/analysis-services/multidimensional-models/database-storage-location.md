---
title: Percorso di archiviazione del database | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], storage location
ms.assetid: cf88c62e-581e-42f2-846f-a9bf1d7c3292
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 15b50e0cd8b030c6026dfa46c92a2d52dbcb2e5a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48216541"
---
# <a name="database-storage-location"></a>Percorso di archiviazione dei database
  Spesso, un amministratore del database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] desidera che un determinato database risieda al di fuori della cartella di dati del server. Queste situazioni sono il più delle volte determinate da esigenze aziendali, ad esempio il miglioramento delle prestazioni o l'ampliamento dello spazio di archiviazione. Questi casi, il `DbStorageLocation` consente di proprietà del database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dba per specificare il percorso del database in un dispositivo disco o nella rete locale.  
  
## <a name="dbstoragelocation-database-property"></a>Proprietà di database DbStorageLocation  
 Il `DbStorageLocation` proprietà database consente di specificare la cartella in cui [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] crea e gestisce tutti i dati e metadati di file di database. Tutti i file di metadati vengono archiviati nella `DbStorageLocation` cartella, ad eccezione del file di metadati del database, che viene archiviato nella cartella di dati del server. Esistono due importanti considerazioni quando si imposta il valore di `DbStorageLocation` proprietà di database:  
  
-   Il `DbStorageLocation` proprietà di database deve essere impostata su un percorso di cartella UNC esistente o una stringa vuota. Una stringa vuota è il valore predefinito per la cartella di dati del server. Se la cartella non esiste, quando si esegue un comando `Create`, `Attach` o `Alter` verrà generato un errore.  
  
-   Il `DbStorageLocation` proprietà di database non può essere impostata in modo che punti alla cartella di dati del server o a una delle relative sottocartelle. Se il percorso punta alla cartella di dati del server o a una delle relative sottocartelle, quando si esegue un comando `Create`, `Attach` o `Alter` verrà generato un errore.  
  
> [!IMPORTANT]  
>  È consigliabile impostare il percorso UNC per l'utilizzo di una rete SAN (Storage Area Network) basata su iSCSI o di un disco collegato localmente. Qualsiasi percorso UNC di una condivisione di rete o qualsiasi soluzione di archiviazione remota a latenza elevata produce un'installazione non supportata.  
  
### <a name="dbstoragelocation-compared-to-storagelocation"></a>Confronto tra DbStorageLocation e StorageLocation  
 `DbStorageLocation` specifica la cartella in cui risiedono tutti i file di dati e di metadati del database, mentre `StorageLocation` specifica la cartella in cui risiedono una o più partizioni di un cubo. `StorageLocation` può essere impostata in modo indipendente da `DbStorageLocation`. Si tratta di una decisione dell'amministratore di database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in base ai risultati previsti. Spesso le due proprietà vengono usate in modo sovrapposto.  
  
## <a name="dbstoragelocation-usage"></a>Utilizzo di DbStorageLocation  
 Il `DbStorageLocation` proprietà del database viene utilizzata come parte di un `Create` comando di database un `Detach` / `Attach` database Command sequenziare, in un `Backup` / `Restore` sequenza di comandi di database , o in un `Synchronize` comando di database. La modifica della proprietà di database `DbStorageLocation` è considerata una modifica strutturale nell'oggetto di database, ovvero è necessario ricreare tutti i metadati e rielaborare tutti i dati.  
  
> [!IMPORTANT]  
>  Non è consigliabile modificare il percorso di archiviazione dei database tramite un comando `Alter`. È invece consigliabile usare una sequenza di `Detach` / `Attach` comandi di database (vedere [spostare un Database di Analysis Services](move-an-analysis-services-database.md), [collegamento e scollegamento database di Analysis Services](attach-and-detach-analysis-services-databases.md)).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Collegamento e scollegamento di database di Analysis Services](attach-and-detach-analysis-services-databases.md)   
 [Spostare un Database di Analysis Services](move-an-analysis-services-database.md)   
 [Elemento DbStorageLocation](../xmla/xml-elements-properties/dbstoragelocation-element.md)   
 [Creare l'elemento &#40;XMLA&#41;](../xmla/xml-elements-commands/create-element-xmla.md)   
 [Elemento Attach](../xmla/xml-elements-commands/attach-element.md)   
 [Elemento Synchronize &#40;XMLA&#41;](../xmla/xml-elements-commands/synchronize-element-xmla.md)  
  
  
