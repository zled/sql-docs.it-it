---
title: Creazione di programmi SMO | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Visual Basic [SMO]
- Visual C# [SMO]
- programming [SMO]
- SQL Server Management Objects, programming
- SMO [SQL Server], programming
ms.assetid: 7d2f0bcf-f1ae-45b8-bc3f-7aea4fae7e45
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2115b0e807e8308b802a2d0f104c71304ad40154
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066441"
---
# <a name="creating-smo-programs"></a>Creazione di programmi SMO
  La programmazione generale degli oggetti [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) include le aree comuni condivise da tutti gli oggetti, ad esempio l'esecuzione di metodi, l'impostazione di proprietà e la manipolazione di raccolte.  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Connessione a un'istanza di SQL Server](connecting-to-an-instance-of-sql-server.md)|Il programma SMO più semplice che stabilisce una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Vengono illustrate l'autenticazione di Windows e l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e vengono forniti esempi di connessione a un'istanza locale e a un'istanza remota di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Disconnessione da un'istanza di SQL Server](disconnecting-from-an-instance-of-sql-server.md)|Programma che illustra come eseguire la disconnessione dall'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Chiamata di metodi](calling-methods.md)|In questa sezione viene descritto l'approccio generale alla chiamata dei metodi. Viene illustrato l'utilizzo dei parametri e la gestione delle tabelle di dati restituite in un oggetto <xref:System.Data.DataTable>. Viene fornito inoltre un esempio di chiamata di un costruttore di oggetti e della chiamata del metodo `Clone`.|  
|[Impostazione delle proprietà](setting-properties-smo.md)|In questa sezione viene illustrato come impostare diversi tipi di proprietà, come impostare e ottenere le proprietà degli oggetti e, attraverso gli esempi forniti, come impostare le proprietà dell'oggetto al momento della creazione e come  scorrere tutte le proprietà di un oggetto.|  
|[Uso delle raccolte](using-collections.md)|Vari programma che illustrano le tecniche utilizzate con le raccolte di oggetti. Viene spiegato come fare riferimento a un oggetto tramite le raccolte e, attraverso gli esempi forniti, come scorrere i membri di una raccolta.|  
|[Gestione degli eventi SMO](handling-smo-events.md)|In questa sezione viene descritto come impostare e gestire eventi in SMO e viene fornito un esempio su come impostare un gestore eventi e una sottoscrizione di eventi.|  
|[Gestione delle eccezioni SMO](handling-smo-exceptions.md)|In questa sezione viene illustrato come intercettare le eccezioni in SMO attraverso esempi di intercettazioni e di visualizzazione di un'eccezione interna.|  
|[Uso dei tipi di dati](working-with-data-types.md)|In questa sezione viene illustrato come utilizzare i diversi tipi di dati di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], come costruire un oggetto datatype con la specifica nel costruttore di oggetti e viene fornito un esempio di creazione di un oggetto datatype tramite il costruttore predefinito.|  
|[Uso di transazioni](using-transactions.md)|In questa sezione viene illustrato come implementare l'elaborazione delle transazioni in un programma SMO e vengono forniti esempi di utilizzo delle transazioni in questo tipo di programmi.|  
|[Uso della modalità di acquisizione](using-capture-mode.md)|In questa sezione viene illustrato come registrare l'output del programma SMO. Nell'esempio il programma SMO viene registrato sotto forma di istruzioni [!INCLUDE[tsql](../../../includes/tsql-md.md)] inviate all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per un'esecuzione successiva.|  
  
  