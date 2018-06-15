---
title: Codici restituiti | Documenti Microsoft
description: Codici restituiti
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- OLE DB Driver for SQL Server, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 84927b3d26233e9d21f175850a5b11c2c2bea56b
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2018
ms.locfileid: "35665961"
---
# <a name="return-codes"></a>Codici restituiti
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Al livello più elementare, una funzione membro può avere esito positivo o negativo. A un livello più approfondito, una funzione può avere esito positivo, ma tale esito potrebbe non corrispondere alle previsioni dello sviluppatore dell'applicazione.  
  
 Per ulteriori informazioni sui codici restituiti OLE DB, vedere [codici restituiti (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Quando un Driver OLE DB per la funzione membro di SQL Server viene restituito S_OK, la funzione ha avuto esito positivo.  
  
 Quando un Driver OLE DB per la funzione membro di SQL Server non restituisce S_OK, le macro OLE/COM HRESULT FAILED e IS_ERROR possono determinare l'esito positivo o negativo complessivo di una funzione.  
  
 Se FAILED o IS_ERROR restituisce TRUE, il Driver OLE DB per il consumer di SQL Server ha la certezza che l'esecuzione della funzione membro non è riuscita. Se FAILED o IS_ERROR restituisce FALSE e il valore HRESULT non sia uguale a S_OK, il Driver OLE DB per SQL Server consumer è garantito la funzione ha esito positivo in un certo senso. Il consumer può recuperare informazioni dettagliate su questa restituzione "esito positivo con informazioni" dal Driver OLE DB per le interfacce di errore di SQL Server. Inoltre, nel caso in cui una funzione non riesce chiaramente (la macro FAILED restituisce TRUE), informazioni dettagliate sull'errore è disponibile nel Driver OLE DB per le interfacce di errore di SQL Server.  
  
 Il Driver OLE DB per i consumer di SQL Server verifica in genere il valore restituito HRESULT DB_S_ERRORSOCCURRED "esito positivo con informazioni". Le funzioni membro che restituiscono DB_S_ERRORSOCCURRED definiscono in genere uno o più parametri che forniscono al consumer i valori di stato. Nessuna informazione di errore potrebbe essere disponibile per il consumer siano quelle restituite nei parametri con valori di stato, è necessario implementare la logica dell'applicazione per recuperare i valori di stato quando sono disponibili.  
  
 Il Driver OLE DB per le funzioni membro di SQL Server non restituiscono il codice di esito positivo S_FALSE. Tutti i Driver OLE DB per le funzioni membro di SQL Server restituiscono sempre S_OK per indicare l'esito positivo.  
  
## <a name="see-also"></a>Vedere anche  
 [errori](../../oledb/ole-db-errors/errors.md)  
  
  
