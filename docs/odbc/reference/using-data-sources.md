---
title: Utilizzo di origini dati | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data sources [ODBC], about data sources
ms.assetid: d5550619-22b2-4b16-bd08-fbabb6554c40
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a9ef21a59be0b292912a6ca4b4fc75a67dc952fb
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="using-data-sources"></a>Utilizzo di origini dati
Origini dati vengono in genere create dall'utente finale o un tecnico con un programma chiamato il *Amministratore ODBC*. L'amministratore ODBC richiede all'utente per il driver da utilizzare e quindi chiama tale driver. Il driver consente di visualizzare una finestra di dialogo che richiede le informazioni che necessarie per la connessione all'origine dati. Dopo che l'utente immette le informazioni, il driver viene archiviato nel sistema.  
  
 In un secondo momento, l'applicazione chiama il responsabile di Driver e passa il nome di un'origine dati macchina o il percorso di un file contenente un'origine dati file. Quando viene passato un nome dell'origine dati macchina, Driver Manager cerca il sistema per individuare il driver utilizzato dall'origine dati. Quindi, il driver viene caricato e passa il nome dell'origine dati. Il driver utilizza il nome dell'origine dati per trovare le informazioni che necessarie per la connessione all'origine dati. Infine, si connette all'origine dati, in genere chiedere conferma all'utente per un ID utente e una password, che in genere non sono archiviati.  
  
 Quando viene passato a un'origine dati file, gestione Driver apre il file e carica il driver specificato. Se il file contiene inoltre una stringa di connessione, questo passa al driver. Utilizzando le informazioni nella stringa di connessione, il driver si connette all'origine dati. Se è stata passata alcuna stringa di connessione, il driver richiede in genere all'utente le informazioni necessarie.
