---
title: SQLSetConnectOption (Driver ODBC di Visual FoxPro) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLSetConnectOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5a35449e-4694-4ee5-9fa1-45d5a8fe7823
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3ad5d029263219c97cb6bffa7536a9c9f9f58a21
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetconnectoption-visual-foxpro-odbc-driver"></a>SQLSetConnectOption (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: parziale  
  
 Conformità di API ODBC: Livello 1  
  
 Imposta le opzioni che controllano gli aspetti di connessioni. Questa funzione è supportata parzialmente: il driver supporta tutti i valori per il *fOption* argomento ma non supporta alcune *vParam* valori per il *fOption* argomento SQL_TXN_ISOLATION.  
  
 Nella tabella seguente vengono descritti solo gli argomenti con il comportamento specifico per l'implementazione di Visual FoxPro il Driver ODBC di **SQLSetConnectOption**.  
  
|*fOption*|Osservazioni|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Se si sceglie SQL_AUTOCOMMIT_OFF, l'applicazione deve esplicitamente eseguire il commit o il rollback delle transazioni con [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); il Driver ODBC di Visual FoxPro non esegue automaticamente il commit un'istruzione transactable dopo il completamento. Se l'istruzione è transactable, il driver iniziare una transazione.|  
|SQL_CURRENT_QUALIFIER|Può essere un nome completo [database](../../odbc/microsoft/visual-foxpro-terminology.md) nome o il percorso completo alla directory contenente zero o più [libero tabelle](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|SQL_LOGINTIMEOUT|Restituisce l'errore "Driver non valido".|  
|SQL_CURSORS|Restituisce l'errore "Driver non valido".|  
|SQL_PACKET_SIZE|Restituisce l'errore "Driver non valido".|  
|SQL_TXN_ISOLATION|Il driver consente solo SQL_TXN_READ_COMMITTED.<br /><br /> Nell'esempio *vParam*s non sono supportati:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Per ulteriori informazioni, vedere [SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md) nel *riferimento per programmatori ODBC*.
