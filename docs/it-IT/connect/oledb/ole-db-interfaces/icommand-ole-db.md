---
title: ICommand (OLE DB) | Documenti Microsoft
description: Interfaccia ICommand (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ICommand [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 6aa64b140c1b7127237406818ef0af7c41c16f98
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="icommand-ole-db"></a>ICommand (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In questo articolo viene descritto il comportamento OLE DB specifico per il Driver OLE DB per SQL Server.  
  
## <a name="icommandexecute"></a>ICommand::Execute  
 L'inserimento di un numero di dati maggiori delle dimensioni di una colonna restituisce in genere un errore. Tuttavia, esistono casi in cui viene restituito S_OK, ma la *dwStatus* verrà impostato su DBSTATUS_S_TRUNCATED. In genere si verifica durante l'inserimento di dati con parametri, in cui la colonna non è sufficientemente grande da contenere i dati, e **ICommandWithParameters:: SetParameterInfo** non è ancora stato chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce & #40; OLE DB & #41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)
  
  
