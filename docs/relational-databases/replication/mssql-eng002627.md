---
title: MSSQL_ENG002627 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG002627 error
ms.assetid: 7f4136ac-3784-4a41-a98c-8a02308e4883
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 78422797a35ae9bf66941aa987795a07c6e68726
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47621899"
---
# <a name="mssqleng002627"></a>MSSQL_ENG002627
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2627|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico|N/D|  
|Testo del messaggio|Violazione del vincolo %ls '%.*ls'. Non è possibile inserire la chiave duplicata nell'oggetto '%.\*ls'.|  
  
## <a name="explanation"></a>Spiegazione  
 Questo errore generale può essere generato indipendentemente dal fatto che un database venga o meno replicato. Nei database replicati l'errore viene di solito generato in quanto le chiavi primarie non sono state gestite correttamente nella topologia. In un ambiente distribuito è fondamentale garantire che lo stesso valore non venga inserito in una colonna chiave primaria o in qualsiasi altra colonna univoca in più di un nodo. Le cause possibile includono:  
  
-   Le operazioni di inserimento e aggiornamento su una riga vengono eseguite in più di un nodo. Sebbene la replica di tipo merge e le sottoscrizioni aggiornabili per la replica transazionale consentano il rilevamento e la risoluzione dei conflitti, è preferibile inserire o aggiornare una determinata riga in un unico nodo. La replica transazionale di tipo peer-to-peer non fornisce funzioni di rilevamento e risoluzione dei conflitti e richiede il partizionamento degli inserimenti e degli aggiornamenti.  
  
-   È stata inserita una riga in un Sottoscrittore che dovrebbe essere di sola lettura. I Sottoscrittori delle pubblicazioni snapshot devono essere considerati come di sola lettura, analogamente ai Sottoscrittori delle pubblicazioni transazionali a meno che non vengano utilizzate sottoscrizioni aggiornabili o una replica transazione peer-to-peer.  
  
-   Viene utilizzata una tabella con una colonna Identity, ma la colonna non è gestita in modo appropriato.  
  
## <a name="user-action"></a>Azione dell'utente  
 L'azione richiesta dipende dal motivo per il quale è stato generato l'errore:  
  
-   Le operazioni di inserimento e aggiornamento su una riga vengono eseguite in più di un nodo.  
  
     Indipendentemente dal tipo di replica utilizzato, è consigliabile partizionare inserimenti e aggiornamenti quando possibile, in modo da ridurre l'elaborazione richiesta per il rilevamento e la risoluzione dei conflitti. Per la replica transazionale peer-to-peer, è richiesto il partizionamento di inserimenti e aggiornamenti. Per altre informazioni, vedere [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
-   È stata inserita una riga in un Sottoscrittore che dovrebbe essere di sola lettura.  
  
     Non inserire o aggiornare righe nel Sottoscrittore a meno che non si stia utilizzando la replica di tipo merge, la replica transazionale con sottoscrizioni aggiornabili o la replica transazionale peer-to-peer.  
  
-   Viene utilizzata una tabella con una colonna Identity, ma la colonna non è gestita in modo appropriato.  
  
     Per la replica di tipo merge e la replica transazionale con sottoscrizioni aggiornabili, le colonne Identity devono essere gestite automaticamente dalla replica. Per la replica transazionale peer-to-peer, devono invece essere gestite manualmente. Per altre informazioni, vedere [Replicare colonne Identity](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Replica di tipo merge](../../relational-databases/replication/merge/merge-replication.md)   
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Sottoscrizioni aggiornabili per la replica transazionale](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
