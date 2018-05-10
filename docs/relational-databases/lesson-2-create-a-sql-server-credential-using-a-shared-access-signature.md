---
title: 'Lezione 2: Creare credenziali di SQL Server usando una firma di accesso condiviso | Microsoft Docs'
ms.custom: ''
ms.date: 02/25/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
caps.latest.revision: 17
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a88a95ea4ad99373c5f8a1994599a2dbea961669
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-2-create-a-sql-server-credential-using-a-shared-access-signature"></a>Lezione 2: Creare credenziali di SQL Server usando una firma di accesso condiviso
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In questa lezione verranno create credenziali per archiviare le informazioni sulla sicurezza che saranno poi usate da SQL Server per scrivere e leggere dal contenitore di Azure creato nella [Lezione 1: creare i criteri per il contenitore e generare una chiave di firma di accesso condivisa (SAS, Shared Access Signature)](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md).  
  
Una credenziale di SQL Server è un oggetto utilizzato per archiviare le informazioni di autenticazione necessarie per connettersi a una risorsa all'esterno di SQL Server. Nelle credenziali vengono archiviati il percorso URI del contenitore di archiviazione e i valori della firma di accesso condivisa per questo contenitore.  
  
> [!NOTE]  
> Se si vuole eseguire il backup di SQL Server 2012 SP1 CU2 o versione successiva o di un database di SQL Server 2014 nel contenitore di Azure, è possibile usare la [sintassi deprecata](https://technet.microsoft.com/en-US/library/dn435916(v=sql.120).aspx) illustrata qui per creare credenziali di SQL Server sulla base della chiave dell'account di archiviazione.  
  
## <a name="create-sql-server-credential"></a>Creare credenziali di SQL Server  
Per creare credenziali di SQL Server, seguire questa procedura:  
  
1.  Connettersi a SQL Server Management Studio.  
  
2.  Aprire una nuova finestra di query e connettersi all'istanza di SQL Server 2016 del motore di database nell'ambiente locale.  
  
3.  Nella nuova finestra query incollare l'istruzione CREATE CREDENTIAL con la firma di accesso condiviso illustrata nella Lezione 1 ed eseguire lo script.  
  
    Lo script sarà simile al codice seguente.  
  
    ```Transact-SQL  
  
    USE master  
    CREATE CREDENTIAL [https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>] -- this name must match the container path, start with https and must not contain a forward slash.  
       WITH IDENTITY='SHARED ACCESS SIGNATURE' -- this is a mandatory string and do not change it.   
       , SECRET = 'sharedaccesssignature' -- this is the shared access signature key that you obtained in Lesson 1.   
    GO  
  
    ```  
  
4.  Per visualizzare tutte le credenziali disponibili, è possibile eseguire l'istruzione seguente nella finestra di query collegata all'istanza:  
  
    ```Transact-SQL  
    SELECT * from sys.credentials  
    ```  
  
5.  Aprire una nuova finestra di query e connettersi all'istanza di SQL Server 2016 del motore di database nella macchina virtuale di Azure.  
  
6.  Nella nuova finestra query incollare l'istruzione CREATE CREDENTIAL con la firma di accesso condiviso illustrata nella Lezione 1 ed eseguire lo script.  
  
7.  Ripetere i passaggi 5 e 6 per tutte le istanze di SQL Server 2016 aggiuntive che devono avere accesso al contenitore di Azure.  
  
**Lezione successiva:**  
  
[Lezione 3: Backup del database su URL](../relational-databases/lesson-3-database-backup-to-url.md)  
  
## <a name="see-also"></a>Vedere anche  
[Credenziali &#40;motore di database&#41;](../relational-databases/security/authentication-access/credentials-database-engine.md)  
[CREATE CREDENTIAL &#40;Transact-SQL&#41;](../t-sql/statements/create-credential-transact-sql.md)  
[sys.credentials &#40;Transact-SQL&#41;](../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  

