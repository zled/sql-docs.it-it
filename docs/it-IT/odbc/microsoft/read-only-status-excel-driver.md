---
title: Stato di sola lettura (Driver per Excel) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- read-only status for Excel driver [ODBC]
- Excel driver [ODBC], read-only status
ms.assetid: ef5d773b-4f8f-4005-b985-84b53d8e9f9b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d0cdfec3129dbe01e5b25f0c8595b8bd4e528ba8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="read-only-status-excel-driver"></a>Stato di sola lettura (Driver per Excel)
Quando viene utilizzato il driver per Microsoft Excel, le tabelle di origine dati vengono aperti in sola lettura per impostazione predefinita e possono essere aperto da un solo utente alla volta. Anche se tabelle hanno lo stato di sola lettura, tuttavia, le applicazioni possono eseguire inserimenti e aggiornamenti per le tabelle di Microsoft Excel.  
  
 Quando un'applicazione esegue un comando Salva con nome dei dati di Microsoft Excel tramite il driver Microsoft Excel, l'applicazione deve creare una nuova tabella e inserire i dati da salvare nella nuova tabella. Inserimenti comportare un'aggiunta alla tabella. Altre operazioni non possono essere eseguite nella tabella fino a quando non viene chiuso e riaperto. Una volta chiusa, la tabella non insert successivo può essere eseguita perché la tabella è quindi una tabella di sola lettura.  
  
 È possibile aggiornare i valori quando si utilizza il driver per Microsoft Excel, ma non può essere eliminata una riga da una tabella basata su un foglio di calcolo di Microsoft Excel, pertanto gli aggiornamenti non sono ufficialmente supportati dal driver Microsoft Excel.
