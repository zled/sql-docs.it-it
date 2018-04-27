---
title: Attività di caricamento BLOB di Azure | Microsoft Docs
ms.custom: ''
ms.date: 07/25/2016
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: control-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpblobuptask.f1
- sql14.dts.designer.afpblobuptask.f1
ms.assetid: 6ea068b0-4cd8-45b5-b89d-09b8f25040c0
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8caf8a55fd29286dd46067a54e95e75ad0c88b54
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="azure-blob-upload-task"></a>Attività di caricamento BLOB di Azure
L' **attività di caricamento BLOB di Azure** consente a un pacchetto SSIS di caricare file in un archivio BLOB di Azure.
    
Per aggiungere un' **attività di caricamento BLOB di Azure**, trascinare l'attività in Progettazione SSIS e fare doppio clic oppure clic con il pulsante destro del mouse e quindi scegliere **Modifica** per visualizzare la finestra di dialogo seguente relativa all' **editor dell'attività di caricamento BLOB di Azure** .  
  
 **Attività di caricamento BLOB di Azure** è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
 La tabella seguente fornisce le descrizioni dei campi della finestra di dialogo.  
  
|||  
|-|-|  
|**Campo**|**Descrizione**|  
|AzureStorageConnection|Consente di specificare un'istanza esistente di Gestione connessioni dell'archiviazione di Azure o di creare una nuova istanza che fa riferimento a un account di archiviazione di Azure che indica la posizione in cui sono ospitati i file BLOB.|  
|BlobContainer|Specifica il nome del contenitore BLOB che contiene i file caricati come BLOB.|  
|BlobDirectory|Specifica la directory BLOB in cui viene archiviato il file caricato come BLOB in blocchi. La directory BLOB è una struttura gerarchica virtuale. Se il BLOB esiste già, viene sostituito.|  
|LocalDirectory|Specifica il nome della directory locale che contiene i file da caricare.|  
|FileName|Consente di specificare un filtro per nomi per la selezione di file con il modello di nome specificato. Ad esempio, `MySheet*.xls\*` include file come `MySheet001.xls` e `MySheetABC.xlsx`.|  
|TimeRangeFrom/TimeRangeTo|Consente di specificare un filtro basato su un intervallo di tempo. Sono inclusi i file modificati dopo **TimeRangeFrom** e prima di **TimeRangeTo**.|  
  
  
