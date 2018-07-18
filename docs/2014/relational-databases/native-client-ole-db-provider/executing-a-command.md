---
title: L'esecuzione di un comando | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bddfd1c50163f6a74286043c2bc5e871ce366c1d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417690"
---
# <a name="executing-a-command"></a>Esecuzione di un comando
  Dopo aver stabilita la connessione a un'origine dati, il consumer chiama il **IDBCreateSession:: CreateSession** metodo per creare una sessione. La sessione funge da comando, set di righe o factory di transazioni.  
  
 Per utilizzare direttamente singoli indici o tabelle, il consumer richiede l'interfaccia `IOpenRowset`. Il metodo `IOpenRowset::OpenRowset` viene aperto e restituisce un set di righe che include tutte le righe di un singolo indice o tabella di base.  
  
 Per eseguire un comando (ad esempio SELECT \* FROM Authors), il consumer richiede il `IDBCreateCommand` interfaccia. Il consumer può eseguire il metodo `IDBCreateCommand::CreateCommand` per creare un oggetto comando e richiedere l'interfaccia `ICommandText`. Il metodo `ICommandText::SetCommandText` viene utilizzato per specificare il comando da eseguire.  
  
 Per eseguire il comando, viene utilizzato `Execute`. Il comando può essere qualsiasi nome di istruzione o di procedura SQL. Non tutti i comandi producono un oggetto set di risultati (set di righe). Comandi come SELECT * FROM Authors producono un set di risultati.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'applicazione del provider OLE DB di SQL Server Native Client](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
