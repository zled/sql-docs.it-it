---
title: Problemi legati all'evoluzione del database (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- compatibility [SQL Server], multuser database changes
- database evolution [SQL Server]
ms.assetid: 1ed6ae10-d212-4ec2-8569-1b94ab1cba6d
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0ec32d850a2daa689fbd28a24e8609a362d9520a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062319"
---
# <a name="issues-of-database-evolution-visual-database-tools"></a>Problemi legati all'evoluzione del database (Visual Database Tools)
  Quando si modifica la struttura di un database distribuito, è necessario assicurarsi che tale modifica sia compatibile con i dati e la struttura del database esistenti. Le seguenti modifiche potrebbero richiedere l'esecuzione di operazioni specifiche:  
  
-   **Aggiunta di un vincolo** Se si aggiunge un vincolo, il database potrebbe già contenere dati che non lo rispettano. Quando si tenta di salvare il nuovo vincolo, nella casella di dialogo [Notifiche postsalvataggio &#40;Visual Database Tools&#41;](visual-database-tools.md) l'utente verrà avvertito che non è stato possibile creare il vincolo tramite il server del database. Per forzare l'accettazione del nuovo vincolo da parte del database, deselezionare la casella di controllo **Verifica dati esistenti durante la creazione**.  
  
-   **Aggiunta di una relazione** Se si aggiunge una relazione, il database potrebbe già contenere righe della tabella chiave esterna che non hanno righe corrispondenti nella tabella chiave primaria. I dati esistenti potrebbero pertanto non soddisfare l'integrità referenziale. Quando si tenta di salvare la nuova relazione, nella casella di dialogo [Notifiche postsalvataggio &#40;Visual Database Tools&#41;](visual-database-tools.md) l'utente verrà avvertito che non è stato possibile salvare la tabella chiave esterna modificata tramite il server del database. Per forzare l'accettazione della modifica da parte del database, deselezionare la casella di controllo **Verifica dati esistenti durante la creazione**.  
  
-   **Modifica di una tabella che contribuisce a una vista indicizzata** Se si modifica una tabella che contribuisce a una vista indicizzata di Microsoft SQL Server, gli indici della vista andranno persi. Per informazioni sulla creazione degli indici, vedere la documentazione online di SQL Server.  
  
-   **Eliminazione di un oggetto** Se si elimina un oggetto, ad esempio una colonna, una tabella o una vista, verificare prima che nessun altro oggetto del database vi faccia riferimento.  
  
 Indipendentemente dalla modalità in base a cui si modifica la progettazione del database, è consigliabile mantenere una cronologia delle modifiche. Una possibile soluzione consiste nel mantenere gli script SQL per tutte le modifiche apportate al database di produzione.  
  
## <a name="see-also"></a>Vedere anche  
 [I vincoli UNIQUE e vincoli Check](../../relational-databases/tables/unique-constraints-and-check-constraints.md)   
 [Ambienti multiutente &#40;Visual Database Tools&#41;](multiuser-environments-visual-database-tools.md)  
  
  