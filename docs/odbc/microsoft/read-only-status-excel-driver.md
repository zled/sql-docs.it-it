---
title: Stato di sola lettura (Driver per Excel) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read-only status for Excel driver [ODBC]
- Excel driver [ODBC], read-only status
ms.assetid: ef5d773b-4f8f-4005-b985-84b53d8e9f9b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 641c6b6324ccb0f12cb5b28bd25b06dc0fcc5029
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="read-only-status-excel-driver"></a>Stato di sola lettura (Driver per Excel)
Quando viene utilizzato il driver per Microsoft Excel, le tabelle di origine dati vengono aperti in sola lettura per impostazione predefinita e possono essere aperto da un solo utente alla volta. Anche se tabelle hanno lo stato di sola lettura, tuttavia, le applicazioni possono eseguire inserimenti e aggiornamenti per le tabelle di Microsoft Excel.  
  
 Quando un'applicazione esegue un comando Salva con nome dei dati di Microsoft Excel tramite il driver Microsoft Excel, l'applicazione deve creare una nuova tabella e inserire i dati da salvare nella nuova tabella. Inserimenti comportare un'aggiunta alla tabella. Altre operazioni non possono essere eseguite nella tabella fino a quando non viene chiuso e riaperto. Una volta chiusa, la tabella non insert successivo può essere eseguita perché la tabella è quindi una tabella di sola lettura.  
  
 È possibile aggiornare i valori quando si utilizza il driver per Microsoft Excel, ma non può essere eliminata una riga da una tabella basata su un foglio di calcolo di Microsoft Excel, pertanto gli aggiornamenti non sono ufficialmente supportati dal driver Microsoft Excel.

