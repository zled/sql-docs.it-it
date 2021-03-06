---
title: Attività di download di BLOB di Azure | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdltask.f1
- sql11.dts.designer.afpblobdltask.f1
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0c4b50078f1d0192dd039ce17b3d4dd6c8d4524e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48092441"
---
# <a name="azure-blob-download-task"></a>Attività di download di BLOB di Azure
  L'attività di download di BLOB di Azure consente a un pacchetto di SSIS di scaricare file da un archivio BLOB di Azure.   
Per aggiungere un' **attività di download di BLOB di Azure**, trascinare l'attività in Progettazione SSIS e farvi doppio clic oppure clic con il pulsante destro del mouse, quindi scegliere **Modifica** per visualizzare la finestra di dialogo seguente relativa all' **editor dell'attività di download di BLOB di Azure** .  
  
 La tabella seguente fornisce una descrizione dei campi della finestra di dialogo.  
  
|||  
|-|-|  
|**Campo**|**Descrizione**|  
|AzureStorageConnection|Consente di specificare un'istanza esistente di Gestione connessioni dell'archiviazione di Azure o di creare una nuova istanza che fa riferimento a un account di archiviazione di Azure che indica la posizione in cui sono ospitati i file BLOB.|  
|BlobContainer|Consente di specificare il nome del contenitore BLOB che include i file BLOB da scaricare.|  
|BlobDirectory|Consente di specificare il nome della directory BLOB che include i file BLOB da scaricare. La directory BLOB è una struttura gerarchica virtuale.|  
|LocalDirectory|Consente di specificare la directory locale in cui verranno archiviati i file BLOB.|  
|FileName|Consente di specificare un filtro per nomi per la selezione di file con il modello di nome specificato. Ad esempio, MySheet*.xls\* include file quali MySheet001.xls e MySheetABC.xlsx.|  
|TimeRangeFrom/TimeRangeTo|Consente di specificare un filtro basato su un intervallo di tempo. Saranno inclusi i file modificati dopo **TimeRangeFrom** e prima di **TimeRangeTo** .|  
  
  
