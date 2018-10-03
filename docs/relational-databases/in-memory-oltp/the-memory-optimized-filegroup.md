---
title: Filegroup con ottimizzazione per la memoria | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 14106cc9-816b-493a-bcb9-fe66a1cd4630
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 31c66aaacdcebfeabf43cc6466659e25d47d4d05
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47606939"
---
# <a name="the-memory-optimized-filegroup"></a>Filegroup con ottimizzazione per la memoria
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Per creare tabelle ottimizzate per la memoria, è necessario creare prima un filegroup ottimizzato per la memoria. Nel filegroup ottimizzato per la memoria è presente uno o più contenitori. Ogni contenitore include file di dati o file differenziali o entrambi.  
  
 Anche se le righe di dati delle tabelle SCHEMA_ONLY non sono persistenti e i metadati per le tabelle ottimizzate per la memoria e le stored procedure compilate a livello nativo vengono archiviati nei cataloghi tradizionali, il motore [!INCLUDE[hek_2](../../includes/hek-2-md.md)] richiede comunque un filegroup ottimizzato per la memoria per le tabelle ottimizzate per la memoria SCHEMA_ONLY per fornire un'esperienza uniforme per i database con tabelle ottimizzate per la memoria.  
  
 Il filegroup ottimizzato per la memoria è basato sul filegroup filestream, con le differenze seguenti:  
  
-   È possibile creare un solo filegroup ottimizzato per la memoria per database. È necessario contrassegnare in modo esplicito il filegroup come contenente memory_optimized_data. È possibile creare il filegroup durante la creazione del database o è possibile aggiungerlo successivamente:  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA  
    ```  
  
-   È necessario aggiungere uno o più contenitori al filegroup `MEMORY_OPTIMIZED_DATA`. Ad esempio  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod  
    ```  
  
-   Non è necessario abilitare il filestream ([Abilitare e configurare FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)) per creare un filegroup ottimizzato per la memoria. Il mapping al filestream viene eseguito dal motore [!INCLUDE[hek_2](../../includes/hek-2-md.md)] .  
  
-   È possibile aggiungere nuovi contenitori a un filegroup ottimizzato per la memoria. Potrebbe essere necessario un nuovo contenitore per espandere l'archiviazione necessaria per la tabella ottimizzata per la memoria durevole nonché per distribuire i dati IO tra più contenitori.  
  
-   Lo spostamento di dati a un filegroup ottimizzato per la memoria è ottimizzato in una configurazione del gruppo di disponibilità AlwaysOn. Diversamente dai file filestream inviati alle repliche secondarie, i file del checkpoint (dati e differenziali) nel filegroup ottimizzato per la memoria non vengono inviati alle repliche secondarie. I file di dati e differenziali vengono costruiti utilizzando il log delle transazioni sulla replica secondaria.  
  
Di seguito sono riportate le limitazioni da applicare al filegroup ottimizzato per la memoria:  
  
-   Dopo aver creato un filegroup ottimizzato per la memoria è possibile rimuoverlo solo eliminando il database. In un ambiente di produzione, è improbabile che si renda necessario rimuovere il filegroup ottimizzato per la memoria.  
  
-   Non è possibile eliminare un contenitore non vuoto o spostare le coppie di file di dati e differenziali in un altro contenitore del filegroup ottimizzato per la memoria.  
  
-   Non è possibile specificare `MAXSIZE` per il contenitore.  
  
## <a name="configuring-a-memory-optimized-filegroup"></a>Configurazione di un filegroup con ottimizzazione per la memoria  
 È consigliabile creare più contenitori nel filegroup ottimizzato per la memoria e distribuirli in unità differenti per ottenere più larghezza di banda per trasmettere i dati in memoria.  
  
 Nel configurare l'archiviazione, è necessario fornire uno spazio libero su disco quattro volte superiore alla dimensione delle tabelle ottimizzate per la memoria durevoli. È anche necessario verificare che il sottosistema di I/O supporti le operazioni di I/O al secondo necessarie per il carico di lavoro. Se le coppie di file di dati e differenziali vengono popolati in un'operazione di IOPS specifica, tale IOPS è necessaria 3 volte per le operazioni di merge e archiviazione. È possibile aggiungere capacità di archiviazione e IOPS aggiungendo uno o più contenitori al filegroup ottimizzato per la memoria.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione e gestione dell'archiviazione per gli oggetti con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
 [Filegroup e file di database](../../relational-databases/databases/database-files-and-filegroups.md) 
  
