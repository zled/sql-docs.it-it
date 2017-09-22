---
title: Limitazioni di sicurezza per SQL Server in Linux | Documenti Microsoft
description: In questo argomento viene descritto SQL Server sulle restrizioni di Linux.
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 6823b8a9cd3f92781d0fd3518f50b8866ba12d48
ms.contentlocale: it-it
ms.lasthandoff: 09/21/2017

---
# <a name="security-limitations-for-sql-server-on-linux"></a>Limitazioni di sicurezza per SQL Server in Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

SQL Server in Linux attualmente presenta le limitazioni seguenti:

* Viene fornito un criterio password standard. MUST_CHANGE è l'unica opzione che è possibile configurare.  
* Extensible Key Management non è supportata. 
* Utilizzo di chiavi archiviate nell'insieme di credenziali chiave di Azure non è supportato.
* SQL Server genera il proprio certificato autofirmato per crittografia delle connessioni. Attualmente, SQL Server non può essere configurato per l'utilizzo di un utente fornito un certificato per SSL o TLS. 

Per ulteriori informazioni sulle funzionalità di sicurezza disponibili in SQL Server, vedere il [centro di sicurezza per il motore di Database di SQL Server e Database SQL di Azure](/sql-docs/docs/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database).

## <a name="next-steps"></a>Passaggi successivi

Per le attività di sicurezza comuni, vedere [iniziare con la funzionalità di sicurezza di SQL Server in Linux](sql-server-linux-security-get-started.md).   
Per uno script modificare il protocollo TCP numero di porta, le directory di SQL Server e configurare i flag di traccia o regole di confronto, vedere [configurare SQL Server in Linux con mssql conf](sql-server-linux-configure-mssql-conf.md).

