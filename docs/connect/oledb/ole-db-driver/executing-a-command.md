---
title: Esegue un comando | Documenti Microsoft
description: Esegue un comando
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- commands [OLE DB Driver for SQL Server]
- OLE DB, executing commands
- sessions [OLE DB Driver for SQL Server]
- OLE DB extensions for XML
- OLE DB Driver for SQL Server, command execution
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8ac58c67053284ba6b60aebd9a47307f97c34886
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="executing-a-command"></a>Esecuzione di un comando
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Dopo aver stabilita la connessione a un'origine dati, il consumer chiama il **IDBCreateSession::CreateSession** metodo per creare una sessione. La sessione funge da comando, set di righe o factory di transazioni.  
  
 Per lavorare direttamente con le singole tabelle o indici, il consumer richiede il **IOpenRowset** interfaccia. Il **IOpenRowset::OPENROWSET** metodo apre e restituisce un set di righe che include tutte le righe da una singola tabella di base o un indice.  
  
 Per eseguire un comando (ad esempio SELECT \* FROM Authors), il consumer richiede il **IDBCreateCommand** interfaccia. Il consumer può eseguire il **IDBCreateCommand::CreateCommand** metodo per creare un oggetto comando e richiedere il **ICommandText** interfaccia. Il **ICommandText::SetCommandText** consente di specificare il comando che deve essere eseguito.  
  
 Il **Execute** comando viene utilizzato per eseguire il comando. Il comando può essere qualsiasi nome di istruzione o di procedura SQL. Non tutti i comandi producono un oggetto set di risultati (set di righe). Comandi come SELECT * FROM Authors producono un set di risultati.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un Driver OLE DB per SQL Server applicazione](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
