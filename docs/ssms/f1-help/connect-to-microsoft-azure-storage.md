---
title: Connettersi al servizio di archiviazione Microsoft Azure | Microsoft Docs
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-f1
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.windowsazurestorage.connect.f1
- SQL13.SWB.WINDOWSAZURESTORAGE.CONNECT.F1
ms.assetid: ''
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b97950c37c5cff52f049253bbd85a60d5373d724
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38980053"
---
# <a name="connect-to-microsoft-azure-storage"></a>Connetti ad Archiviazione di Microsoft Azure
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Usare la finestra di dialogo di **connessione di archiviazione Microsoft Azure** per specificare un account di archiviazione e convalidare la connessione a Microsoft Azure.  
  
## <a name="options"></a>Opzioni  
Specificare le informazioni seguenti sull'account di Microsoft Azure e fare clic su **Avanti** per continuare.  
  
1.  **Account di archiviazione** - specificare il nome dell'account di archiviazione.

   >[!NOTE]
   > È possibile connettersi solo agli [account di archiviazione di uso generico](https://docs.microsoft.com/azure/storage/storage-introduction#introducing-the-azure-storage-services). La connessione ad altri tipi di account di archiviazione può causare un errore simile al seguente:
   >
   >  Il valore per una delle intestazioni HTTP non è nel formato corretto. (Microsoft.SqlServer.StorageClient).
   >
   >  Il server remoto ha restituito un errore: richiesta non valida (400). (Sistema)

2.  **Chiave account** - specificare la chiave account per l'account di archiviazione specificato.  
  
3.  **Usa endpoint sicuri (HTTPS)** - questa opzione usa la comunicazione crittografata e l'identificazione sicura di un server Web di rete.  
  
4.  **Salva chiave account** - questa opzione salva la password in un file crittografato.  
  
