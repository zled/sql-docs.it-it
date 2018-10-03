---
title: L'esecuzione di un comando | Microsoft Docs
description: Esecuzione di un comando
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- commands [OLE DB Driver for SQL Server]
- OLE DB, executing commands
- sessions [OLE DB Driver for SQL Server]
- OLE DB extensions for XML
- OLE DB Driver for SQL Server, command execution
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 9f163f1518b5dc89b6fe7e8e670f5b840aded8b7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47656359"
---
# <a name="executing-a-command"></a>Esecuzione di un comando
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Dopo aver stabilita la connessione a un'origine dati, il consumer chiama il **IDBCreateSession:: CreateSession** metodo per creare una sessione. La sessione funge da comando, set di righe o factory di transazioni.  
  
 Per lavorare direttamente con singoli indici o tabelle, il consumer richiede l'interfaccia **IOpenRowset**. Il metodo **IOpenRowset::OpenRowset** apre e restituisce un set di righe che include tutte le righe di un singolo indice o tabella di base.  
  
 Per eseguire un comando, ad esempio SELECT \* FROM Authors, il consumer richiede l'interfaccia **IDBCreateCommand**. Il consumer può eseguire la **IDBCreateCommand** per creare un oggetto command e richiesta per il **ICommandText** interfaccia. Il **ICommandText:: SetCommandText** metodo viene utilizzato per specificare il comando che deve essere eseguito.  
  
 Per eseguire il comando viene usato il comando **Esegui**. Il comando può essere qualsiasi nome di istruzione o di procedura SQL. Non tutti i comandi producono un oggetto set di risultati (set di righe). Comandi come SELECT * FROM Authors producono un set di risultati.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un driver OLE DB per applicazione SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
