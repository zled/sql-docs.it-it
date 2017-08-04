---
title: Connettersi all'archiviazione Blob di Azure (SQL Server importazione / esportazione guidata) | Documenti Microsoft
ms.custom: 
ms.date: 02/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2e482b8-5f90-48c5-93fb-b412ed52659f
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 36b992b5141799d4e168b2e990643e6a515a8d69
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-azure-blob-storage-sql-server-import-and-export-wizard"></a>Connettersi all'archiviazione Blob di Azure (SQL Server importazione / esportazione guidata)
In questo argomento viene illustrato come connettersi a un **archiviazione Blob di Azure** dell'origine dati dal **scegliere un'origine dati** o **scegliere una destinazione** pagina di SQL Server di importazione / esportazione guidata.

>   [!NOTE]
> Per utilizzare l'origine Blob di Azure o la destinazione, è necessario installare il Feature Pack di Azure per SQL Server Integration Services.
> - Per scaricare il Feature Pack, vedere [Microsoft SQL Server 2016 Integration Services Feature Pack per Azure](https://www.microsoft.com/download/details.aspx?id=49492).
>
> - Per altre informazioni, vedere [Azure Feature Pack for Integration Services &#40;SSIS&#41;](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

La schermata seguente mostra le opzioni da configurare per una connessione di archiviazione Blob di Azure.

![Connessione all'archiviazione BLOB di Azure](../../integration-services/import-export-data/media/azure-blob-storage-connection.png)

## <a name="options-to-specify"></a>Opzioni per specificare

> [!NOTE]
> Le opzioni di connessione per il provider di dati sono gli stessi se archiviazione Blob di Azure è l'origine o destinazione. Ovvero le opzioni disponibili sono gli stessi in entrambi i **scegliere un'origine dati** e **scegliere una destinazione** pagine della procedura guidata.

 **Usa account Azure**  
 Consente di specificare se usare un account online.
  
 **Nome dell'account di archiviazione**  
 Immettere il nome dell'account di archiviazione Azure.  
  
**Chiave dell'account**  
Immettere la chiave per l'account di archiviazione di Azure.  
  
 **Usa HTTPS**  
 Specificare se usare HTTP o HTTPS per connettersi all'account di archiviazione.  
  
 **Usa account per sviluppatore locale**  
 Specificare se usare l'emulatore di archiviazione nel computer locale.  
  
 **Nome del contenitore BLOB**  
 Selezionare dall'elenco dei contenitori di archiviazione disponibili nell'account di archiviazione specificato.  
  
 **Formato del file BLOB**  
 Selezionare il formato di file Testo o Avro.  
  
 **Carattere delimitatore di colonna**  
 Se si seleziona il formato di testo, immettere il carattere delimitatore di colonna.  
  
 **Usa la prima riga come nomi di colonna**  
 Specificare se la prima riga di dati contiene nomi di colonna.  

## <a name="see-also"></a>Vedere anche
[Scegliere un'origine dati](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Scegliere una destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


