---
title: Attività File system di Azure Data Lake Store | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
caps.latest.revision: 3
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.openlocfilehash: 240780efd1b12596b0ebb6156ad98c508f0e8051
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054568"
---
# <a name="azure-data-lake-store-file-system-task"></a>Attività File system di Azure Data Lake Store
Il **attività di Azure Data Lake archivio File System** consente agli utenti di eseguire varie operazioni del file system sul [Azure Data Lake archivio (ADLS)](https://azure.microsoft.com/en-us/services/data-lake-store/).

Per aggiungere un'attività File System di Azure Data Lake Store a un pacchetto, trascinarla dalla casella degli strumenti SSIS ai canvas di progettazione. Quindi fare doppio clic su attività, o l'attività e scegliere **modifica**, per aprire la finestra di dialogo Editor dell'attività.

La proprietà **Operation** specifica l'operazione del file system da eseguire. Sono supportate le operazioni seguenti.

* **CopyToADLS** per caricare file in ADLS.
* **CopyFromADLS** per scaricare file da ADLS.

Per qualsiasi operazione è necessario specificare una gestione della connessione di Azure Data Lake.

Di seguito sono riportate le descrizioni delle proprietà specifiche per ogni operazione.

## <a name="copytoadls"></a>CopyToADLS
* **LocalDirectory:** specifica la directory di origine che contiene file da caricare.
* **FileNamePattern:** specifica un filtro di nome file per i file di origine. Verranno caricati solo i file il cui nome corrisponde al criterio specificato. Sono supportati i caratteri jolly `*` e `?`.
* **SearchRecursively:** specifica se cercare in modo ricorsivo i file da caricare all'interno della directory di origine.
* **AzureDataLakeDirectory:** specifica la directory di destinazione di ADLS in cui caricare i file.
* **FileExpiry:** specifica una data di scadenza e l'ora per i file caricati di ADLS o lasciare vuoto per indicare che i file non scadono mai questa proprietà.

## <a name="copyfromadls"></a>CopyFromADLS
* **AzureDataLakeDirectory:** specifica la directory di origine di ADLS che contiene i file da scaricare.
* **SearchRecursively:** specifica se cercare in modo ricorsivo i file da scaricare all'interno della directory di origine.
* **LocalDirectory:** specifica la directory di destinazione in cui archiviare i file scaricati.
