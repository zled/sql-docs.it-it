---
title: Connettersi al servizio di archiviazione Microsoft Azure | Microsoft Docs
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.windowsazurestorage.connect.f1
- SQL13.SWB.WINDOWSAZURESTORAGE.CONNECT.F1
ms.assetid: 
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: ea0fbb6f0297dfdbe94974de472c7a48ce8ce831
ms.openlocfilehash: b673559a735d3b28d6055a1440183861b3db692a
ms.contentlocale: it-it
ms.lasthandoff: 07/12/2017

---
# Connetti ad Archiviazione di Microsoft Azure
<a id="connect-to-microsoft-azure-storage" class="xliff"></a>
Usare la finestra di dialogo di **connessione di archiviazione Microsoft Azure** per specificare un account di archiviazione e convalidare la connessione a Microsoft Azure.  
  
## Opzioni
<a id="options" class="xliff"></a>  
Specificare le informazioni seguenti sull'account di Microsoft Azure e fare clic su **Avanti** per continuare.  
  
1.  **Account di archiviazione** - specificare il nome dell'account di archiviazione.

   >[!NOTE]
   > È possibile connettersi solo agli [account di archiviazione di uso generico](https://docs.microsoft.com/en-us/azure/storage/storage-introduction#introducing-the-azure-storage-services). La connessione ad altri tipi di account di archiviazione può causare un errore simile al seguente:
   >
   >  Il valore per una delle intestazioni HTTP non è nel formato corretto. (Microsoft.SqlServer.StorageClient).
   >
   >  Il server remoto ha restituito un errore: richiesta non valida (400). (Sistema)

2.  **Chiave account** - specificare la chiave account per l'account di archiviazione specificato.  
  
3.  **Usa endpoint sicuri (HTTPS)** - questa opzione usa la comunicazione crittografata e l'identificazione sicura di un server Web di rete.  
  
4.  **Salva chiave account** - questa opzione salva la password in un file crittografato.  
  

