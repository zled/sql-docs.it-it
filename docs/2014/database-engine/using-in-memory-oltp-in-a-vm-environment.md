---
title: Uso di OLTP In memoria in un ambiente di macchina virtuale | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 27ec7eb3-3a24-41db-aa65-2f206514c6f9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ad9e70e78229821197fdd80724d8e0924818bb30
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103281"
---
# <a name="using-in-memory-oltp-in-a-vm-environment"></a>Uso di OLTP in memoria in un ambiente di VM
  La virtualizzazione del server può aiutare a ridurre i costi operativi e il capitale IT aumentandone l'efficienza grazie a provisioning di applicazioni, manutenzione, disponibilità e processi di backup/recupero migliorati. Grazie ai recenti progressi tecnologici, ora è possibile consolidare più rapidamente complessi carichi di lavoro del database utilizzando la virtualizzazione. Questo argomento illustra le procedure consigliate per l'uso di [!INCLUDE[hek_1](../includes/hek-1-md.md)] in un ambiente virtualizzato.  
  
##  <a name="bkmk_memoryPreAllocation"></a> Preallocazione di memoria  
 Per la memoria in un ambiente virtualizzato, prestazioni e supporto migliorati sono fattori molto importanti. È necessario essere in grado di allocare rapidamente la memoria alle macchine virtuali a seconda dei requisiti e dei carichi di lavoro nonché di fare in modo che non ci siano sprechi di memoria. La funzionalità di memoria dinamica di Hyper-V migliora la flessibilità nell'allocazione e gestione della memoria tra le macchine virtuali in esecuzione in un host.  
  
 Quando si esegue la virtualizzazione di un database con tabelle ottimizzate per la memoria è necessario modificare alcune procedure consigliate per la virtualizzazione e la gestione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Senza tabelle ottimizzate per la memoria, due delle procedure consigliate sono:  
  
-   Se si usa MIN_SERVER_MEMORY, è consigliabile assegnare solo la quantità di memoria necessaria in modo che rimanga memoria sufficiente per altri processi (evitando quindi il paging).  
  
-   Non impostare un valore di preallocazione della memoria troppo elevato. In caso contrario, è possibile che non ci sia memoria sufficiente per altri processi che la richiedono, con conseguente paging della memoria.  
  
 Se si seguono le procedure sopra indicate per un database con tabelle ottimizzate per la memoria, un tentativo di ripristinare e recuperare un database potrebbe far sì che il database rimanga nello stato "Recupero in sospeso", anche se la quantità di memoria è sufficiente per il recupero del database. Il motivo è che all'avvio di [!INCLUDE[hek_2](../includes/hek-2-md.md)] i dati vengono inseriti nella memoria in maniera più drastica rispetto all'allocazione della memoria al database da parte dell'allocazione dinamica della memoria.  
  
 **Risoluzione**  
  
 Per risolvere questo problema, preallocare al database una quantità di memoria sufficiente per il recupero o il riavvio del database, anziché un valore minimo che si basa sulla memoria dinamica per ottenere memoria aggiuntiva se necessario.  
  
## <a name="see-also"></a>Vedere anche  
 [OLTP in memoria &#40;ottimizzazione per la memoria&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
