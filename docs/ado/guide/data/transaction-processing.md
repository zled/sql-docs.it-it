---
title: L'elaborazione delle transazioni | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [ADO]
- data updates [ADO], transaction processing
- updating data [ADO], transaction processing
- nested transactions [ADO]
ms.assetid: 74ab6706-e2dc-42cb-af77-dbc58a9cf4ce
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d4879ea2bc89552409e29847ed39c9418ba668c8
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="transaction-processing"></a>Elaborazione delle transazioni
Oggetto *transazione* delimita l'inizio e alla fine di una serie di operazioni di accesso ai dati eseguito attraverso una connessione. Soggetto alle funzionalità transazionali dell'origine dati, il **connessione** oggetto consente inoltre di creare e gestire le transazioni. Ad esempio, utilizza il Provider Microsoft OLE DB per SQL Server per accedere a un database in Microsoft SQL Server, è possibile creare più transazioni nidificate per i comandi da eseguire.  
  
 ADO assicura che le modifiche a un'origine dati risultanti da operazioni in una transazione si verificano correttamente oppure nessuna.  
  
 Se si annulla la transazione o una delle relative operazioni non riesce, il risultato sarà come se nessuna delle operazioni nella transazione si è verificato. L'origine dati rimane rispetto a prima dell'inizio della transazione.  
  
 ADO fornisce i metodi seguenti per il controllo delle transazioni: **BeginTrans**, **CommitTrans**, e **RollbackTrans**. Utilizzare questi metodi con un **connessione** oggetto quando si desidera salvare o annullare una serie di modifiche apportate ai dati di origine come singola unità. Ad esempio, per trasferire denaro tra conti, sottrarre un importo sia aggiungere la stessa quantità a altra. Se l'aggiornamento ha esito negativo, l'account non è più bilanciare. Queste modifiche all'interno di una transazione aperta garantisce che tutte o nessuna delle modifiche passino.  
  
> [!NOTE]
>  Non tutti i provider supportano le transazioni. Verificare che la proprietà definito dal provider "**Transaction DDL**" viene visualizzato nel **connessione** dell'oggetto [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta, che indica che il provider supporta transazioni. Se il provider non supporta le transazioni, una chiamata a uno di questi metodi restituirà un errore.  
  
 Dopo aver chiamato il **BeginTrans** metodo, il provider eseguirà non immediatamente il commit le modifiche apportate fino a quando non si chiama **CommitTrans** o **RollbackTrans** per terminare il transazione.  
  
 La chiamata di **CommitTrans** metodo salva le modifiche apportate all'interno di una transazione aperta per la connessione e termina la transazione. La chiamata di **RollbackTrans** metodo inverte le modifiche apportate all'interno di una transazione aperta e termina la transazione. Chiamare il metodo quando non sono presenti transazioni aperte genera un errore.  
  
 A seconda di **connessione** dell'oggetto [attributi](../../../ado/reference/ado-api/attributes-property-ado.md) proprietà, una chiamata al **CommitTrans** o **RollbackTrans** potrebbe (metodo) Avvia automaticamente una nuova transazione. Se il **attributi** è impostata su **adXactCommitRetaining**, il provider avvia automaticamente una nuova transazione dopo un **CommitTrans** chiamare. Se il **attributi** è impostata su **adXactAbortRetaining**, il provider avvia automaticamente una nuova transazione dopo un **RollbackTrans** chiamare.  
  
## <a name="transaction-isolation-level"></a>Livello di isolamento delle transazioni  
 Utilizzare il **IsolationLevel** proprietà per impostare il livello di isolamento di una transazione in un **connessione** oggetto. L'impostazione non ha effetto fino alla chiamata successiva di [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) metodo. Se il livello di isolamento che richiesto non è disponibile, il provider può restituire il successivo livello più alto di isolamento. Consultare la **IsolationLevel** proprietà nel riferimento del programmatore di ADO per ulteriori informazioni sui valori validi.  
  
## <a name="nested-transactions"></a>Transazioni nidificate  
 Per i provider che supportano le transazioni nidificate, la chiamata di **BeginTrans** metodo all'interno di una transazione aperta avvia una transazione nidificata. Il valore restituito indica il livello di annidamento: indica di un valore restituito pari a "1" è stata aperta una transazione di primo livello (ovvero, la transazione non sia annidata all'interno di un'altra transazione), "2" indica che è stata aperta una transazione di secondo livello (a transazione annidata all'interno di una transazione di primo livello), e così via. La chiamata **CommitTrans** o **RollbackTrans** interessa solo la maggior parte delle transazioni aperti di recente, è necessario chiudere o il rollback della transazione corrente prima che è possibile risolvere le transazioni di livello superiore.

