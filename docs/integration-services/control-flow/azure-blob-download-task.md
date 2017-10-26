---
title: "Attività di Download di Blob di Azure | Documenti Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/25/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpblobdltask.f1
- sql14.dts.designer.afpblobdltask.f1
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 95ea7de4600551cc994e82dd3408cb4ea608685c
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="azure-blob-download-task"></a>Attività di download di BLOB di Azure
L'attività di download di BLOB di Azure consente a un pacchetto di SSIS di scaricare file da un archivio BLOB di Azure.

Per aggiungere un' **attività di download di BLOB di Azure**, trascinare l'attività in Progettazione SSIS e farvi doppio clic oppure clic con il pulsante destro del mouse, quindi scegliere **Modifica** per visualizzare la finestra di dialogo seguente relativa all' **editor dell'attività di download di BLOB di Azure** .  
  
 Il **attività di Download Blob di Azure** è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  
  
 La tabella seguente fornisce una descrizione dei campi della finestra di dialogo.  
  
|||  
|-|-|  
|**Campo**|**Description**|  
|AzureStorageConnection|Consente di specificare un'istanza esistente di Gestione connessioni dell'archiviazione di Azure o di creare una nuova istanza che fa riferimento a un account di archiviazione di Azure che indica la posizione in cui sono ospitati i file BLOB.|  
|BlobContainer|Consente di specificare il nome del contenitore BLOB che include i file BLOB da scaricare.|  
|BlobDirectory|Consente di specificare il nome della directory BLOB che include i file BLOB da scaricare. La directory BLOB è una struttura gerarchica virtuale.|  
|LocalDirectory|Specifica la directory locale in cui sono archiviati i file blob.|  
|FileName|Consente di specificare un filtro per nomi per la selezione di file con il modello di nome specificato. Ad esempio, `MySheet*.xls\*` include file quali `MySheet001.xls` e `MySheetABC.xlsx`.|  
|TimeRangeFrom/TimeRangeTo|Consente di specificare un filtro basato su un intervallo di tempo. I file modificati dopo **TimeRangeFrom** e prima **TimeRangeTo** sono inclusi.|  
  
  

