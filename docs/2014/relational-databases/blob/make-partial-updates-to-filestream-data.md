---
title: Eseguire aggiornamenti parziali di dati FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: filestream
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
- FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
ms.assetid: d6f7661e-6c14-4d31-9541-4520ca0f82b2
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: de844f92f9ae7a35327defd4abcff3da9821ba66
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209191"
---
# <a name="make-partial-updates-to-filestream-data"></a>Esecuzione di aggiornamenti parziali di dati FILESTREAM
  Un'applicazione utilizza FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT per eseguire aggiornamenti parziali dei dati BLOB FILESTREAM. La funzione [DeviceIoControl](http://go.microsoft.com/fwlink/?LinkId=105527) passa il valore e l'handle restituito da [OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md) al driver FILESTREAM. Tramite il driver viene forzata una copia lato server dei dati FILESTREAM correnti nel file a cui fa riferimento l'handle. Se l'applicazione rilascia il valore FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT dopo la scrittura nell'handle, l'ultima operazione di scrittura viene resa persistente, mentre quelle precedenti eseguite nell'handle vanno perse.  
  
> [!NOTE]  
>  Per l'accesso remoto, FILESTREAM è basato sul [protocollo SMB](http://go.microsoft.com/fwlink/?LinkId=112454) .  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il valore `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` per eseguire un aggiornamento parziale di dati BLOB FILESTREAM inseriti.  
  
> [!NOTE]  
>  Questo esempio richiede il database e la tabella abilitati per FILESTREAM creati in [Creare un database abilitato per FILESTREAM](create-a-filestream-enabled-database.md) e [Creare una tabella per archiviare dati FILESTREAM](create-a-table-for-storing-filestream-data.md).  
  
 [!code-cpp[FILESTREAM#FS_CPP_FSCTL](../../snippets/tsql/SQL15/tsql/filestream/cpp/filestream.cpp#fs_cpp_fsctl)]  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso ai dati FILESTREAM con OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md)   
 [Creazione di applicazioni client per dati FILESTREAM](create-client-applications-for-filestream-data.md)  
  
  
