---
title: Filegroup con ottimizzazione per la memoria | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14106cc9-816b-493a-bcb9-fe66a1cd4630
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: e68b94ce70e24d16ac1cc94274b9dac05974dbe7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069389"
---
# <a name="the-memory-optimized-filegroup"></a>Filegroup con ottimizzazione per la memoria
  Per creare tabelle ottimizzate per la memoria, è necessario creare prima un filegroup ottimizzato per la memoria. Nel filegroup ottimizzato per la memoria è presente uno o più contenitori. Ogni contenitore include file di dati o file differenziali o entrambi.  
  
 Anche se le righe di dati delle tabelle SCHEMA_ONLY non sono persistenti e i metadati per le tabelle ottimizzate per la memoria e le stored procedure compilate a livello nativo vengono archiviati nei cataloghi tradizionali, il motore [!INCLUDE[hek_2](../../includes/hek-2-md.md)] richiede comunque un filegroup ottimizzato per la memoria per le tabelle ottimizzate per la memoria SCHEMA_ONLY per fornire un'esperienza uniforme per i database con tabelle ottimizzate per la memoria.  
  
 Il filegroup ottimizzato per la memoria è basato sul filegroup filestream, con le differenze seguenti:  
  
-   È possibile creare un solo filegroup ottimizzato per la memoria per database. È necessario contrassegnare in modo esplicito il filegroup come contenente memory_optimized_data. È possibile creare il filegroup durante la creazione del database o è possibile aggiungerlo successivamente:  
  
    ```  
    ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA  
    ```  
  
-   È necessario aggiungere uno o più contenitori al filegroup MEMORY_OPTIMIZED_DATA. Esempio:  
  
    ```  
    ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod  
    ```  
  
-   Non è necessario abilitare il filestream ([Abilitare e configurare FILESTREAM](../blob/enable-and-configure-filestream.md)) per creare un filegroup ottimizzato per la memoria. Il mapping al filestream viene eseguito dal motore [!INCLUDE[hek_2](../../includes/hek-2-md.md)] .  
  
-   È possibile aggiungere nuovi contenitori a un filegroup ottimizzato per la memoria. Potrebbe essere necessario un nuovo contenitore per espandere l'archiviazione necessaria per la tabella ottimizzata per la memoria durevole nonché per distribuire i dati IO tra più contenitori.  
  
-   Lo spostamento di dati a un filegroup ottimizzato per la memoria è ottimizzato in una configurazione del gruppo di disponibilità AlwaysOn. Diversamente dai file filestream inviati alle repliche secondarie, i file del checkpoint (dati e differenziali) nel filegroup ottimizzato per la memoria non vengono inviati alle repliche secondarie. I file di dati e differenziali vengono costruiti utilizzando il log delle transazioni sulla replica secondaria.  
  
 Di seguito sono riportate le limitazioni del filegroup ottimizzato per la memoria.  
  
-   Dopo aver creato un filegroup ottimizzato per la memoria è possibile rimuoverlo solo eliminando il database. In un ambiente di produzione, è improbabile che si renda necessario rimuovere il filegroup ottimizzato per la memoria.  
  
-   Non è possibile eliminare un contenitore non vuoto o spostare le coppie di file di dati e differenziali in un altro contenitore del filegroup ottimizzato per la memoria.  
  
-   Non è possibile specificare MAXSIZE per il contenitore.  
  
## <a name="configuring-a-memory-optimized-filegroup"></a>Configurazione di un filegroup con ottimizzazione per la memoria  
 È consigliabile creare più contenitori nel filegroup ottimizzato per la memoria e distribuirli in unità differenti per ottenere più larghezza di banda per trasmettere i dati in memoria.  
  
 Nel configurare l'archiviazione, è necessario fornire uno spazio libero su disco quattro volte superiore alla dimensione delle tabelle ottimizzate per la memoria durevoli. È inoltre necessario assicurarsi che il sottosistema IO supporti le operazioni di IOPS necessarie per il carico di lavoro. Se le coppie di file di dati e differenziali vengono popolati in un'operazione di IOPS specifica, tale IOPS è necessaria 3 volte per le operazioni di merge e archiviazione. È possibile aggiungere capacità di archiviazione e IOPS aggiungendo uno o più contenitori al filegroup ottimizzato per la memoria.  
  
 In uno scenario con più contenitori e più unità, i file di dati e differenziali vengono allocati in contenitori con un meccanismo round robin. Il primo file di dati viene allocato dal primo contenitore e il file differenziale viene allocato dal contenitore successivo e questo modello di allocazione si ripete. Questo schema di allocazione distribuisce i file di dati e differenziali uniformemente nei contenitori se si dispone di un numero dispari di unità, ciascuna con il mapping a un solo contenitore. Tuttavia, se si dispone di un numero pari di unità, ciascuna con il mapping a un contenitore, è possibile che si verifichi un'archiviazione sbilanciata con i file di dati per cui è stato eseguito il mapping alle unità dispari e i file differenziali per cui è stato eseguito il mapping alle unità pari. Per ottenere un flusso bilanciato di IO per il recupero, inserire coppie di file di dati e differenziali negli stessi spindle/archiviazione come descritto nell'esempio seguente.  
  
 **Esempio:** prendere in considerazione un filegroup con ottimizzazione per la memoria con due contenitori: il contenitore 1 nell'unità X e il contenitore 2 nell'unità Y. Dal momento che l'allocazione dei file di dati e differenziali viene eseguita in modo round robin, il contenitore 1 avrà solo file di dati e contenitore 2 avrà solo file differenziali, determinando una persistenza sbilanciata per l'archiviazione, nonché operazioni di input/output al secondo, come file di dati sono significativamente maggiori i file differenziali. Per distribuire i file di dati e differenziali in modo uniforme tra unità X e Y, creare quattro contenitori anziché due ed eseguire il mapping i primi due contenitori all'unità X e i due contenitori successivi all'unità Y. Con allocazione round robin, i dati primo e primo file differenziale verranno allocati dal contenitore 1 e 2 contenitore rispettivamente cui viene eseguito il mapping all'unità X. Analogamente, il file di dati e differenziali successivo verrà allocato dal contenitore 3 e 4 contenitori per cui viene eseguito il mapping all'unità Y. In questo modo la distribuzione di file di dati e differenziali tra due unità in modo uniforme.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione e gestione dell'archiviazione per gli oggetti con ottimizzazione per la memoria](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  