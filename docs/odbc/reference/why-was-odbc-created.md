---
title: Perché è stato creato ODBC? | Microsoft Docs
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
- ODBC [ODBC], about ODBC
ms.assetid: ba6eb993-316b-4650-bab8-d76583c00e53
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 88b081ecb06f023154ab227aa57691a1ccee03e1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="why-was-odbc-created"></a>Perché è stato creato ODBC?
Società utilizzato in passato, un singolo DBMS. L'accesso al database è stato eseguito il front-end del sistema o mediante le applicazioni scritte per lavorare esclusivamente con tale sistema. Tuttavia, come l'utilizzo di computer aumento delle dimensioni e ulteriori componenti hardware e software è diventato disponibile, società avviato acquisire diversi DBMS. Sono molti i motivi: persone hanno acquistate animale più economico, qual era il più veloce, quali sono già informata, ciò che è stato più recente sul mercato, cosa ha funzionato ottimale per una singola applicazione. Per altri motivi erano riorganizzazioni e fusioni, in cui i reparti che in precedenza erano un singolo DBMS era diversi.  
  
 Il problema di dimensioni sono aumentate ancora più complesso con l'avvento del PC. Questi computer portati in una serie di strumenti per l'esecuzione di query, l'analisi e visualizzazione dei dati, insieme a un numero di database economici e facile da utilizzare. In poi, una singola società era spesso dati sparsi nell'intera innumerevoli desktop, server e minicomputer, archiviati in una vasta gamma di database incompatibili e accede a un elevato numero di strumenti diversi, alcuni dei quali è stato possibile ottenere tutti i dati.  
  
 La richiesta di verifica finale di origine con l'avvento del client/server di elaborazione, che si cerca di rendere l'uso più efficiente delle risorse del computer. Basso costo personal computer (client) si trovano sul desktop e fornire entrambi un front-end grafico per i dati e un numero di strumenti economici, ad esempio fogli di calcolo, grafici, programmi e autori di report. Minicomputer e computer mainframe (server) host DBMS, in cui utilizzano la potenza di elaborazione e la posizione centrale per fornire accesso ai dati rapido coordinato. Come si era il software front-end di essere connessi ai database back-end?  
  
 Un problema analogo riscontrate fornitori di software indipendenti (ISV). I fornitori di software del database per minicomputer e mainframe erano in genere costretti a scrivere una versione di un'applicazione per ogni sistema DBMS o scrivere codice specifico DBMS per ogni sistema DBMS che desidera accedere. I fornitori di software per PC era necessario scrivere routine di accesso ai dati per ogni vari DBMS con cui si intende utilizzare. In questo modo spesso una notevole quantità di risorse impiegati per la scrittura e la gestione di routine, piuttosto che le applicazioni di accesso ai dati e le applicazioni spesso sono state vendute in qualità, ma in se potrebbe accedono a dati in un sistema DBMS.  
  
 Cosa è necessario entrambi i gruppi di sviluppatori è un modo per accedere ai dati in diversi DBMS. Il gruppo di mainframe e minicomputer necessario un modo per unire i dati dai diversi DBMS in una singola applicazione, mentre il gruppo di computer di personal necessaria questa possibilità, nonché un modo per scrivere una singola applicazione che è indipendente da qualsiasi un DBMS. In breve, entrambi i gruppi necessitassero una modalità interoperativa per accedere ai dati; aprono necessaria la connettività del database.
