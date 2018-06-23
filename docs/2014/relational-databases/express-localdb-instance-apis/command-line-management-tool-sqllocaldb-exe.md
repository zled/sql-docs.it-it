---
title: 'Strumento di gestione della riga di comando: SqlLocalDB.exe | Documenti Microsoft'
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
api_location:
- sqluserinstance.dll
ms.assetid: dd0882b1-a8a9-447a-8bdf-0f9d7f36d336
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 41fccfdd76df1b56f2a1b4f54851a80effa19f76
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169419"
---
# <a name="command-line-management-tool-sqllocaldbexe"></a>Strumento di gestione della riga di comando: SqlLocalDB.exe
  SqlLocalDB.exe è uno strumento semplice che consente all'utente di gestire facilmente le istanze del database locale dalla riga di comando. Viene implementato come un semplice wrapper dell'API dell'istanza del database locale. Come in molti strumenti SQL Server simili, ad esempio SQLCMD, i parametri vengono passati a SqlLocalDB come argomenti della riga di comando e l'output viene inviato alla console.  
  
 SqlLocalDB consente agli sviluppatori di utilizzare il database locale senza la necessità di scrivere codice per chiamare l'API o dipendere da altri strumenti per effettuare tale operazione.  
  
## <a name="sqllocaldb-options"></a>Opzioni di SqlLocalDB  
 SqlLocalDB supporta le opzioni seguenti.  
  
|Opzione|Funzione|  
|------------|------------------|  
|`-?`|Viene stampato il testo della Guida.|  
|`create&#124;c "instance name" [version-number] [-s]`|Viene creata una nuova istanza del database locale con una versione e un nome specificati.<br /><br /> Se il parametro [version-number] viene omesso, il valore predefinito è la versione della build di SqlLocalDB.<br /><br /> Tramite il parametro -s viene avviata la nuova istanza del database locale dopo la relativa creazione.|  
|`delete&#124;d “instance name”`|Viene eliminata l'istanza del database locale con il nome specificato.|  
|`start&#124;s "instance name"`|Viene avviata l'istanza del database locale con il nome specificato.|  
|`stop&#124;p "instance name" [-i&#124;-k]`|Viene arrestata l'istanza del database locale con il nome specificato, al termine dell'esecuzione delle query correnti.<br /><br /> Tramite il parametro -i viene richiesto l'arresto dell'istanza del database locale con l'opzione NOWAIT.<br /><br /> Tramite il parametro -k viene terminato il processo dell'istanza del database locale senza contattare quest'ultimo.|  
|`share&#124;h ["owner SID or account"] "private name" "shared name"`|Viene condivisa l'istanza privata specificata tramite il nome condiviso indicato. Se viene omesso il SID dell'utente o il nome dell'account, il valore predefinito è l'utente corrente.|  
|`unshare&#124;u “shared name”`|Viene rimossa la condivisione dell'istanza del database locale condivisa specificata.|  
|`info&#124;i`|Vengono elencate tutte le istanze del database locale esistenti di proprietà dell'utente corrente nonché tutte le istanze del database locale condivise.|  
|`info&#124;i “instance name”`|Vengono stampate le informazioni sull'istanza specificata del database locale.|  
|`versions&#124;v`|Vengono elencate tutte le versioni del database locale installate nel computer.|  
|||  
|`trace&#124;t on&#124;off`|Viene abilitata o disabilitata la traccia.|  
  
 Gli spazi in SqlLocalDB vengono considerati come delimitatori. È necessario racchiudere tra virgolette i nomi delle istanze contenenti spazi e caratteri speciali. Esempio:  
  
 `SqlLocalDB create "My instance name with spaces"`  
  
  