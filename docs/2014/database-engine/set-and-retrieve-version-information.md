---
title: Impostare e recuperare le informazioni sulla versione | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- historical information [SQL Server]
- source controls [SQL Server Management Studio], version information
- retrieving version information
- current file version information
- version control services [SQL Server], retrieving version information
- version control services [SQL Server], setting version information
- status information [SQL Server], source control files
- historical information [SQL Server], source control files
ms.assetid: c3f253c4-4e3d-48e8-8d90-bd6ee899faf7
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: da9b33474449140cb31b6dcfd752a5112ebb9d4e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158035"
---
# <a name="set-and-retrieve-version-information"></a>Impostazione e recupero delle informazioni sulla versione
  Le informazioni sulla versione comprendono la cronologia e lo stato corrente di un file incluso nel controllo del codice sorgente. Per ogni file incluso nel controllo del codice sorgente, [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe conserva una cronologia completa che consente di tenere traccia dell'evoluzione di uno o più file nel tempo. È inoltre possibile utilizzare queste informazioni per recuperare una copia locale di qualsiasi versione del file oppure eseguire il confronto tra due versioni qualsiasi del file.  
  
 Nella cronologia di un file sono inclusi:  
  
-   Il numero della versione, che ne identifica la sequenza rispetto ad altre versioni dello stesso file.  
  
-   L'azione eseguita. Tra le operazioni rilevate vi sono la creazione, l'archiviazione e l'eliminazione del file.  
  
-   Il nome dell'utente che ha eseguito un'azione sul file.  
  
-   La data e l'ora in cui l'operazione è stata eseguita.  
  
 In Visual SourceSafe vengono inoltre conservate le informazioni relative alla soluzione attualmente caricata. Queste informazioni offrono uno snapshot dello stato attuale del file, inclusi:  
  
-   L'identità dell'utente il cui file viene estratto.  
  
-   Il numero dell'ultima versione del file selezionato.  
  
-   La data in cui la versione è stata creata.  
  
-   Il commento dell'utente associato alla versione.  
  
-   I percorsi dei progetti con cui il file viene condiviso.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Visualizzare la cronologia File](../../2014/database-engine/view-file-history.md)  
  
-   [Visualizzare cronologia progetti](../../2014/database-engine/view-project-history.md)  
  
-   [Visualizzare lo stato di File](../../2014/database-engine/view-file-status.md)  
  
-   [Recuperare i file](../../2014/database-engine/retrieve-files.md)  
  
-   [Specificare una versione come ultima versione](../../2014/database-engine/specify-a-version-as-the-latest-version.md)  
  
-   [Confrontare i file](../../2014/database-engine/compare-files.md)  
  
-   [Condivisione di file](../../2014/database-engine/share-files.md)  
  
-   [Creazione della cronologia e i rapporti di stato](../../2014/database-engine/create-history-and-status-reports.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali di controlli di origine](../../2014/database-engine/source-control-basics.md)  
  
  