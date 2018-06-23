---
title: Creazione di un'applicazione del Provider SQL Server Native Client OLE DB | Documenti Microsoft
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
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f0912b99394b8317c78c134a3324dd9d30a04bd8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171417"
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a>Creazione di un'applicazione del provider OLE DB di SQL Server Native Client
  Creazione di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applicazione del provider OLE DB Native Client implica questi passaggi:  
  
1.  Avvio di una connessione a un'origine dati.  
  
2.  Esecuzione di un comando.  
  
3.  Elaborazione dei risultati.  
  
> [!NOTE]  
>  Se possibile, usare l'autenticazione di Windows. Se non è disponibile, agli utenti verrà richiesto di immettere le credenziali in fase di esecuzione. Evitare di archiviare le credenziali in un file. Se è necessario rendere persistenti le credenziali, è consigliabile crittografarle utilizzando [cryptoAPI Win32](http://go.microsoft.com/fwlink/?LinkId=9504).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Avvio di una connessione a un'origine dati](establishing-a-connection-to-a-data-source.md)  
  
-   [Esecuzione di un comando](executing-a-command.md)  
  
-   [Elaborazione dei risultati](processing-results.md)  
  
-   [Informazioni sulle proprietà OLE DB](about-ole-db-properties.md)  
  
-   [Uso della clausola OUTPUT con OLE DB in SQL Server Native Client](using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  