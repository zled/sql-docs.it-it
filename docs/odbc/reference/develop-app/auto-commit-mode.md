---
title: Modalità autocommit | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- auto-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: c8de5b60-d147-492d-b601-2eeae8511d00
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 87a5bababd2129ffb7e0aad36a2ceb3362d4acd9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792359"
---
# <a name="auto-commit-mode"></a>Modalità autocommit
*In modalità autocommit,* ogni operazione di database è una transazione che verrà eseguito il commit eseguito. Questa modalità è adatta per numero di transazioni reali costituiti da una singola istruzione SQL. Non è necessario delimitare oppure specificare il completamento di queste transazioni. Nel database senza supporto delle transazioni, la modalità autocommit è l'unica modalità supportata. In tali database, le istruzioni vengono eseguite quando vengono eseguite e non è possibile eseguire il rollback li; sono pertanto sempre in modalità autocommit.  
  
 Se il sistema DBMS sottostante non supporta le transazioni in modalità autocommit, il driver possibile emularli eseguendo manualmente il commit di ogni istruzione SQL eseguita.  
  
 Se un batch di istruzioni SQL viene eseguito in modalità autocommit, è specifico dell'origine dati quando le istruzioni nel batch vengono eseguito il commit. Possono essere eseguito il commit perché vengono eseguite o nel suo complesso dopo l'esecuzione dell'intero batch. Alcune origini dati supportino entrambi questi comportamenti e possono fornire un modo per la selezione di uno o altri utenti. In particolare, se si verifica un errore nel corso del batch, è specifico dell'origine dati se le istruzioni già eseguite sono stato eseguito il commit o rollback. Di conseguenza, le applicazioni interoperative che usano batch e richiedono loro di eseguire il commit o rollback nel suo complesso devono eseguire batch solo in modalità di commit manuale.
