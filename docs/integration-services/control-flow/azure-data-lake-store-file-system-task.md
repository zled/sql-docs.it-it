---
title: "Attività File System di archivio Azure Data Lake | Documenti Microsoft"
ms.custom: 
ms.date: 08/22/2017
ms.prod: sql-server-2016
ms.reviewer: douglasl
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSTASK.F1
- SQL14.DTS.DESIGNER.AFPADLSTASK.F1
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 4cb0585acf73e734662847401c60686b54ae6410
ms.contentlocale: it-it
ms.lasthandoff: 10/10/2017

---
# <a name="azure-data-lake-store-file-system-task"></a>Attività File System di archivio Azure Data Lake

L'attività di sistema Azure Data Lake archivio File consente agli utenti di eseguire varie operazioni del file system su [Azure Data Lake archivio (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

L'attività di sistema Azure Data Lake archivio File è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

## <a name="configure-the-azure-data-lake-store-file-system-task"></a>Configurare l'attività di sistema di File di archivio Azure Data Lake

Per aggiungere un'attività di sistema File di archivio Azure Data Lake a un pacchetto, trascinarlo dalla casella degli strumenti SSIS ai canvas di progettazione. Quindi fare doppio clic su attività, o l'attività e scegliere **modifica**per aprire la **Editor di attività di Azure Data Lake archivio File System** la finestra di dialogo.

Il **operazione** proprietà specifica l'operazione di file system da eseguire. Selezionare una delle operazioni seguenti:

- **CopyToADLS:** caricare file di ADLS.
- **CopyFromADLS:** scaricare file da ADLS.

Per qualsiasi operazione, è necessario specificare una gestione connessione di Azure Data Lake.

Di seguito sono riportate le proprietà specifiche per ogni operazione:

### <a name="copytoadls"></a>CopyToADLS
- **LocalDirectory:** specifica la directory di origine locale che contiene i file da caricare.
- **FileNamePattern:** specifica un filtro di nome file per file di origine. Vengono caricati solo i file il cui nome corrisponde al criterio specificato. I caratteri jolly `*` e `?` sono supportati.
- **SearchRecursively:** specifica se eseguire la ricerca in modo ricorsivo all'interno della directory di origine per i file da caricare.
- **AzureDataLakeDirectory:** specifica la directory di destinazione per caricare i file di ADLS.
- **FileExpiry:** specifica una data di scadenza e l'ora per i file caricati di ADLS. Lasciare vuoto per indicare che i file non scadono mai questa proprietà.

### <a name="copyfromadls"></a>CopyFromADLS
- **AzureDataLakeDirectory:** specifica la directory di origine ADLS che contiene i file da scaricare.
- **SearchRecursively:** specifica se eseguire la ricerca in modo ricorsivo all'interno della directory di origine per i file da scaricare.
- **LocalDirectory:** specifica la directory di destinazione per archiviare i file scaricati.
