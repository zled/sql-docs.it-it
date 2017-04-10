---
title: "Attivit&#224; di caricamento BLOB di Azure | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.afpblobuptask.f1"
  - "sql14.dts.designer.afpblobuptask.f1"
ms.assetid: 6ea068b0-4cd8-45b5-b89d-09b8f25040c0
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 12
---
# Attivit&#224; di caricamento BLOB di Azure
  L'**attività di caricamento BLOB di Azure** consente a un pacchetto SSIS di caricare file in un archivio BLOB di Azure.
  
>   [!NOTE] Per assicurarsi che Gestione della connessione di archiviazione di Azure e i componenti da cui è usato, ossia l'origine BLOB, la destinazione BLOB e le attività di caricamento e download di BLOB, riescano a connettersi a entrambi gli account di archiviazione generici e agli account di archiviazione BLOB, scaricare [qui](https://www.microsoft.com/download/details.aspx?id=49492) la versione più recente del Feature Pack di Azure. Per altre informazioni su questi due tipi di account di archiviazione, vedere [Introduzione ad Archiviazione di Microsoft Azure](https://azure.microsoft.com/en-us/documentation/articles/storage-introduction/#general-purpose-storage-accounts). 
    
Per aggiungere un'**attività di caricamento BLOB di Azure**, trascinare l'attività in Progettazione SSIS e fare doppio clic oppure clic con il pulsante destro del mouse e quindi scegliere **Modifica** per visualizzare la finestra di dialogo seguente relativa all'**editor dell'attività di caricamento BLOB di Azure**.  
  
 L'**attività di caricamento BLOB di Azure** è un componente del Feature Pack di SQL Server Integration Services (SSIS) per Azure per SQL Server 2016. Scaricare il Feature Pack [qui](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
 La tabella seguente fornisce le descrizioni dei campi della finestra di dialogo.  
  
|||  
|-|-|  
|**Campo**|**Description**|  
|AzureStorageConnection|Consente di specificare un'istanza esistente di Gestione connessioni dell'archiviazione di Azure o di creare una nuova istanza che fa riferimento a un account di archiviazione di Azure che indica la posizione in cui sono ospitati i file BLOB.|  
|BlobContainer|Specifica il nome del contenitore BLOB che conterrà i file caricati come BLOB.|  
|BlobDirectory|Specifica la directory BLOB in cui verrà archiviato il file caricato come BLOB in blocchi. La directory BLOB è una struttura gerarchica virtuale. Se il BLOB esiste già, verrà sostituito.|  
|LocalDirectory|Specifica il nome della directory locale che contiene i file da caricare.|  
|FileName|Consente di specificare un filtro per nomi per la selezione di file con il modello di nome specificato. Ad esempio, MySheet*.xls\* include file quali MySheet001.xls e MySheetABC.xlsx.|  
|TimeRangeFrom/TimeRangeTo|Consente di specificare un filtro basato su un intervallo di tempo. Vengono inclusi i file modificati dopo **TimeRangeFrom** e prima di **TimeRangeTo**.|  
  
  