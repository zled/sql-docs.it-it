---
title: Panoramica ODBC | Documenti Microsoft
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
- ODBC [ODBC]
- ODBC [ODBC], about ODBC
ms.assetid: 233315bd-2b7f-4b20-9978-e920e1ea9a07
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 39ab7586ebc1cd63d028caab0d3c2f09b82c7172
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32916076"
---
# <a name="odbc-overview"></a>Panoramica ODBC
Open Database Connectivity (ODBC) è una diffuso API application programming interface () per l'accesso al database. È basato sulle specifiche di interfaccia a livello di chiamata (CLI) da Open Group e ISO/IEC per API di database e si utilizza Structured Query Language (SQL) poiché la lingua di accesso del database.  
  
 ODBC è progettato per il numero massimo *interoperabilità* -, ovvero la possibilità di una singola applicazione di accedere a sistemi di gestione di diversi database (DBMS) con lo stesso codice di origine. Applicazioni di database chiamano le funzioni nell'interfaccia di ODBC, che vengono implementate nei moduli specifici del database denominati *driver*. L'utilizzo di driver di isola le applicazioni da chiamate specifico del database nello stesso modo che i driver della stampante isolare elaboratori di comandi specifico della stampante. Poiché i driver sono stati caricati in fase di esecuzione, un utente ha solo per aggiungere un nuovo driver per accedere a un nuovo sistema DBMS; non è necessario ricompilare o ricollegare l'applicazione.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Perché è stato creato ODBC?](../../odbc/reference/why-was-odbc-created.md)  
  
-   [Che cos'è ODBC?](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC e l'interfaccia della riga di comando standard](../../odbc/reference/odbc-and-the-standard-cli.md)
