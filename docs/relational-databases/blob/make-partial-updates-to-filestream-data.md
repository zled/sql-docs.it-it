---
title: Eseguire aggiornamenti parziali di dati FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: filestream
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
- FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
ms.assetid: d6f7661e-6c14-4d31-9541-4520ca0f82b2
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 23bd3b82da83b466a137eaba15da2e1998df4ca3
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36833809"
---
# <a name="make-partial-updates-to-filestream-data"></a>Esecuzione di aggiornamenti parziali di dati FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Un'applicazione utilizza FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT per eseguire aggiornamenti parziali dei dati BLOB FILESTREAM. La funzione [DeviceIoControl](http://go.microsoft.com/fwlink/?LinkId=105527) passa il valore e l'handle restituito da [OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) al driver FILESTREAM. Tramite il driver viene forzata una copia lato server dei dati FILESTREAM correnti nel file a cui fa riferimento l'handle. Se l'applicazione rilascia il valore FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT dopo la scrittura nell'handle, l'ultima operazione di scrittura viene resa persistente, mentre quelle precedenti eseguite nell'handle vanno perse.  
  
> [!NOTE]  
>  Per l'accesso remoto, FILESTREAM è basato sul [protocollo SMB](http://go.microsoft.com/fwlink/?LinkId=112454) .  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il valore `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` per eseguire un aggiornamento parziale di dati BLOB FILESTREAM inseriti.  
  
> [!NOTE]  
>  Questo esempio richiede il database e la tabella abilitati per FILESTREAM creati in [Creare un database abilitato per FILESTREAM](../../relational-databases/blob/create-a-filestream-enabled-database.md) e [Creare una tabella per archiviare dati FILESTREAM](../../relational-databases/blob/create-a-table-for-storing-filestream-data.md).  
  
 [!code-cpp[FILESTREAM#FS_CPP_FSCTL](../../relational-databases/blob/codesnippet/cpp/make-partial-updates-to-_1.cpp)]  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso ai dati FILESTREAM con OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)   
 [Creazione di applicazioni client per dati FILESTREAM](../../relational-databases/blob/create-client-applications-for-filestream-data.md)  
  
  
