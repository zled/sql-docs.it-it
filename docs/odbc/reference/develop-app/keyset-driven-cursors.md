---
title: Cursori basati su keyset | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- keyset-driven cursors [ODBC]
- cursors [ODBC], key-set driven
ms.assetid: 01769f43-1d9c-4685-84fa-15a6465335e9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 13bb740a6d76ae97541f39b73d1cecf60bef61fa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912446"
---
# <a name="keyset-driven-cursors"></a>Cursori basati su keyset
Un cursore gestito da keyset è compresa tra un valore statico e un cursore dinamico, la possibilità di rilevare le modifiche apportate. Un cursore statico, non sempre rileva le modifiche per l'appartenenza e l'ordine del set di risultati. È un cursore dinamico, di rilevare le modifiche ai valori delle righe nel set (soggetti a livello di isolamento della transazione, come impostato dall'attributo di connessione SQL_ATTR_TXN_ISOLATION) di risultati.  
  
 Quando viene aperto un cursore gestito da keyset, Salva le chiavi per l'intero set di risultati; Questa correzione risolve l'apparente appartenenza e l'ordine del set di risultati. Quando il cursore è scorre il set di risultati, utilizza le chiavi in questo *keyset* per recuperare i valori di dati corrente per ogni riga. Si supponga, ad esempio, un cursore gestito da keyset e recupera una riga e un'altra applicazione, quindi aggiorna tale riga. Se il cursore recupera nuovamente la riga, i valori rilevati sono i nuovi file perché refetched la riga tramite la relativa chiave. Per questo motivo, i cursori basati su keyset sempre di rilevare le modifiche apportate da se stessi e altri utenti.  
  
 Quando il cursore tenta di recuperare una riga che è stata eliminata, questa riga viene visualizzato come "foro" nel set di risultati: la chiave per la riga esiste nel keyset, ma la riga non esiste più nel set di risultati. Se vengono aggiornati i valori di chiave in una riga, la riga viene considerata sono stati eliminati e quindi inserite, tali righe vengono visualizzati anche come fori nel set di risultati. Mentre un cursore gestito da keyset sempre è in grado di individuare le righe eliminate da altri utenti, anche possibile rimuovere le chiavi per le righe si elimina automaticamente da keyset. Cursori basati su keyset di eseguire tale operazione non è in grado di rilevare le righe eliminate. Se un determinato cursore basati su keyset rileva il proprio eliminazioni viene segnalato tramite l'opzione SQL_STATIC_SENSITIVITY in **SQLGetInfo**.  
  
 Le righe inserite da altri utenti sono visibili a un cursore gestito da keyset mai perché è disponibile alcuna chiave per le righe nel keyset. Tuttavia, un cursore gestito da keyset, facoltativamente, aggiungere le chiavi per le righe viene inserito per il keyset. Cursori basati su keyset di eseguire tale operazione consente di rilevare i propri inserimenti. Se un determinato cursore basati su keyset rileva i proprio inserimenti viene segnalato tramite l'opzione SQL_STATIC_SENSITIVITY in **SQLGetInfo**.  
  
 La matrice di stato di riga specificata dall'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR può contenere SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO o SQL_ROW_ERROR per ogni riga. Restituisce SQL_ROW_UPDATED, SQL_ROW_DELETED o SQL_ROW_ADDED per le righe che rileva come aggiornate, eliminate o inserite.  
  
 Cursori basati su keyset in genere vengono implementati mediante la creazione di una tabella temporanea che contiene le chiavi per ogni riga nel set di risultati. Poiché il cursore è inoltre necessario determinare che se sono state aggiornate le righe, questa tabella contiene anche una colonna con informazioni relative al controllo delle versioni delle righe.  
  
 Per scorrere il set di risultati originale, il cursore gestito da keyset viene aperto un cursore statico tramite la tabella temporanea. Per recuperare una riga nel set di risultati originale, il cursore Recupera innanzitutto la chiave appropriata dalla tabella temporanea e quindi recupera i valori per la riga correnti. Se si utilizzano cursori a blocchi, il cursore deve recuperare più righe e le chiavi.
