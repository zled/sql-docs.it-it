---
title: Configurazione server - regole di confronto | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- collation configuration, SQL Server
- collation configuration, Setup
- collation configuration
ms.assetid: e3986870-5be4-458b-b671-5ff12a27b022
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ee24c8f9234069526780db72457e178d50d5c824
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170516"
---
# <a name="server-configuration---collation"></a>Configurazione del server - Regole di confronto
  Nella pagina Configurazione del server - Regole di confronto dell'Istallazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è possibile modificare le impostazioni per le regole di confronto utilizzate dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] e da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per scopi di ordinamento. Scegliere l'opzione che corrisponde alle impostazioni per le regole di confronto di installazioni diverse di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]o di un altro computer.  
  
## <a name="options"></a>Opzioni  
 Personalizza per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono disponibili due gruppi di regole di confronto: le regole di confronto di Windows e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le regole di confronto. È possibile specificare impostazioni distinte per le regole di confronto per il [!INCLUDE[ssDE](../../includes/ssde-md.md)] e [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]oppure le stesse regole di confronto per entrambi i servizi.  
  
 Per impostazione predefinita, vengono selezionate regole di confronto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per le impostazioni locali di sistema della lingua inglese. Le regole di confronto predefinite per le versioni localizzate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono determinate dalle impostazioni locali di sistema di Windows per il computer in uso.  
  
 Modificare le impostazioni predefinite solo se l'impostazione delle regole di confronto per questa installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve corrispondere alle impostazioni delle regole di confronto utilizzate da un'altra istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]oppure alle impostazioni locali di sistema di Windows di un altro computer.  
  
 **Nota** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usa solo le regole di confronto di Windows. Se si intende installare [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], selezionare una regola di confronto di Windows durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per garantire risultati coerenti tra [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] e [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Per altre informazioni, vedere [Collation Settings in Setup](http://go.microsoft.com/fwlink/?LinkId=190977)(Impostazioni regole di confronto nell'installazione).  
  
## <a name="best-practices"></a>Procedure consigliate  
 Per altre informazioni su una tabella delle impostazioni locali di sistema Windows e sulle regole di confronto predefinite corrispondenti usate dal programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vedere [Collation Settings in Setup](http://go.microsoft.com/fwlink/?LinkId=190977)(Impostazioni regole di confronto nell'installazione).  
  
 Se possibile, utilizzare un'unica regola di confronto per l'organizzazione. In questo modo, non è necessario specificare esplicitamente la regola di confronto per ogni database, colonna, espressione o identificatore. In caso di utilizzo di più regole di confronto e impostazioni di tabelle codici, sarà necessario codificare le query in modo da considerare le regole di precedenza delle regole di confronto. Per altre informazioni, vedere l'argomento [Precedenza delle regole di confronto &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) nella documentazione online.  
  
 Quando si selezionano regole di confronto per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tenere presenti le indicazioni seguenti:  
  
-   Selezionare regole di confronto BINARY2 se l'ordinamento in base a punti di codice binario risulta accettabile.  
  
-   Selezionare una regola di confronto di Windows per garantire un confronto coerente tra tipi di dati.  
  
-   Per un supporto linguistico più efficace, utilizzare una nuova regola di confronto di livello 100. Per altre informazioni, vedere [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
-   Se si prevede di eseguire la migrazione di un database all'istanza aggiornata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], selezionare regole di confronto corrispondenti alle regole di confronto esistenti per il database.  
  
  
