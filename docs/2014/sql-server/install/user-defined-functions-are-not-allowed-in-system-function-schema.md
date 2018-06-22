---
title: In system_function_schema non sono consentite funzioni definite dall'utente | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- system functions [SQL Server]
- user-defined functions [SQL Server], system
ms.assetid: 3cb54053-ef65-4558-ae96-8686b6b22f4f
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 16c6cf618028d56a3b09cdad8da4cfd9eb9309f4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067514"
---
# <a name="user-defined-functions-are-not-allowed-in-systemfunctionschema"></a>In system_function_schema non sono consentite funzioni definite dall'utente
  Rilevate funzioni definite dall'utente che sono proprietà dell'utente non documentato **system_function_schema**. Non è possibile creare una funzione di sistema definita dall'utente specificando tale utente. Il **system_function_schema** nome utente non esiste, e l'ID utente che è associato con lo stesso nome (UID = 4) è riservato per il **sys** schema ed è limitato al solo uso interno.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Le operazioni di archiviazione e accesso agli oggetti di sistema sono state modificate nei modi seguenti:  
  
-   Gli oggetti di sistema sono archiviati in sola lettura **risorse** del database e indirizzare gli aggiornamenti di oggetto di sistema non sono consentiti.  
  
     Gli oggetti di sistema appaiono logicamente nel **sys** schema di ogni database. In questo modo è possibile richiamare le funzioni di sistema da qualsiasi database specificando un nome di funzione composto da una sola parte. Ad esempio, l'istruzione `SELECT * FROM fn_helpcollations()` può essere eseguita da qualsiasi database.  
  
-   L'utente non documentato **system_function_schema** è stato rimosso.  
  
-   L'ID utente associato **system_function_schema** (UID = 4) è riservato per il **sys** schema ed è limitato al solo uso interno.  
  
 Queste modifiche hanno l'effetto seguente sulle funzioni di sistema definite dall'utente:  
  
-   Istruzioni Data Definition Language (DDL) che fanno riferimento a **system_function_schema** avrà esito negativo. Ad esempio, l'istruzione `CREATE FUNCTION system`_`function` \_ `schema.fn` \_ `MySystemFunction` ... non verrà completata.  
  
-   Dopo l'aggiornamento a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], gli oggetti esistenti che appartengono allo **system_function_schema** sono contenuti solo nel **sys** dello schema del **master** database. Poiché gli oggetti di sistema non possono essere modificati, queste funzioni non possono essere modificate o eliminate dal **master** database. Inoltre, non possono essere richiamate da altri database specificando un nome di funzione composto da una sola parte.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Prima di eseguire l'aggiornamento, completare le attività seguenti:  
  
1.  Modificare la proprietà delle funzioni definite dall'utente esistenti a **dbo** usando la **sp_changeobjectowner** stored procedure di sistema.  
  
2.  Rinominare la funzione in modo da non utilizzare il prefisso 'fn_' per evitare potenziali conflitti di nome con le funzioni di sistema correnti o future.  
  
3.  Aggiungere una copia delle funzioni modificate in ogni database in cui vengono utilizzate.  
  
4.  Sostituire i riferimenti a **system_function_schema** con **dbo** in tutti gli script che contengono istruzioni DDL di funzioni definite dall'utente.  
  
5.  Modificare gli script che richiamano tali funzioni per l'utilizzo di entrambi il nome in due parti dbo **. * * * nome_funzione*, o il nome in tre parti *database_name ***.** dbo.* nome_funzione *.  
  
 Per ulteriori informazioni, vedere gli argomenti seguenti della documentazione online di SQL Server:  
  
-   "sp_changeobjectowner"  
  
-   "Separazione fra schema e utente"  
  
-   "Database Resource"  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)   
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Rimuovere le istruzioni che modificano oggetti di sistema](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md)   
 [Rimuovere le istruzioni che eliminano oggetti di sistema](../../../2014/sql-server/install/remove-statements-that-drop-system-objects.md)  
  
  
