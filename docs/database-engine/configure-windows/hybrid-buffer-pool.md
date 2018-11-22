---
title: Pool di buffer ibrido | Microsoft Docs
ms.custom: ''
ms.date: 11/06/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ''
author: DBArgenis
ms.author: argenisf
manager: craigg
ms.openlocfilehash: a8098c38b72ba44ab973fe5564b93740252bafc6
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2018
ms.locfileid: "51560308"
---
# <a name="hybrid-buffer-pool"></a>Pool di buffer ibrido
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Con SQL Server 2019 CTP 2.1 è stata introdotta una nuova funzionalità nel motore di database di SQL Server che consente di accedere direttamente alle pagine di dati nei file di database archiviate nei dispositivi con memoria persistente. 

In un sistema tradizionale senza memoria persistente, SQL Server memorizza nella cache le pagine di dati del pool di buffer. Con il pool di buffer ibrido, SQL Server non esegue una copia della pagina nella parte di memoria basata su DRAM del pool di buffer, ma fa riferimento alla pagina direttamente nel file di database che si trova nel dispositivo con memoria persistente. Per il pool di buffer, l'accesso ai file di dati nella memoria persistente avviene tramite I/O mappato alla memoria, noto anche come riconoscimento.

In un dispositivo con memoria persistente è possibile fare riferimento solo alle pagine clean. Se una pagina è dirty, rimane nella DRAM ed eventualmente viene riscritta nel dispositivo con memoria persistente.

Questa funzionalità è disponibile sia in Windows sia in Linux.

## <a name="enable-hybrid-buffer-pool"></a>Abilitare il pool di buffer ibrido

Nella versione CTP 2.1 è necessario abilitare il flag di traccia di avvio 809 per poter usare il pool di buffer ibrido.

## <a name="best-practices-for-hybrid-buffer-pool"></a>Procedure consigliate per il pool di buffer ibrido

* Durante la formattazione del dispositivo con memoria persistente in Windows, usare le dimensioni di unità di allocazione più grandi disponibili per NTFS (2 MB in Windows Server 2019) e assicurarsi che nel dispositivo sia abilitato DAX (DirectAccess)
  