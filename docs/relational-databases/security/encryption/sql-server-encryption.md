---
title: Crittografia di SQL Server | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 05/03/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption [SQL Server], about encryption
- security [SQL Server], encryption
- cryptography [SQL Server], about cryptography
ms.assetid: ead0150e-4943-4ad5-84c8-36f85c7278f4
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 441968f81086a875ee526d31dcaf753c1e103868
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-encryption"></a>Crittografia di SQL Server
  La crittografia è il processo che consiste nell'offuscare i dati tramite l'utilizzo di una chiave o di una password. È in grado di rendere i dati inutilizzabili se non si dispone della chiave di decrittografia o password corrispondente. La crittografia non risolve i problemi relativi al controllo di accesso, ma migliora la sicurezza limitando la perdita di dati anche se il controllo di accesso viene eluso. Se, ad esempio, il computer host del database è configurato scorrettamente e un pirata informatico ottiene dati riservati, le informazioni sottratte potrebbero essere inutilizzabili se crittografate.  
  
 È possibile utilizzare la crittografia in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per connessioni, dati e stored procedure. Nella tabella seguente sono disponibili ulteriori informazioni sulla crittografia in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Sebbene la crittografia sia un strumento prezioso per garantire la sicurezza, se ne sconsiglia l'utilizzo per tutti i dati o le connessioni. Per decidere se implementare la crittografia oppure no, considerare le modalità di accesso ai dati utilizzate dagli utenti. Se per accedere gli utenti utilizzano una rete pubblica, la crittografia dei dati potrebbe essere necessaria per aumentare il livello di sicurezza. Tuttavia, se tutti accedono attraverso una configurazione di Intranet sicura, la crittografia potrebbe non essere necessaria. L'utilizzo della crittografia comporta anche l'adozione di una strategia di manutenzione per password, chiavi e certificati.  
  
> [!NOTE]  
>  Le informazioni più recenti sulla sicurezza a livello di trasporto (TSL1.2) sono disponibili nell'articolo [Supporto di TLS 1.2 per Microsoft SQL Server](https://support.microsoft.com/kb/3135244).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Gerarchia di crittografia](../../../relational-databases/security/encryption/encryption-hierarchy.md)  
 Informazioni sulla gerarchia di crittografia in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Scelta di un algoritmo di crittografia](../../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
 Informazioni sulla selezione di un algoritmo di crittografia efficace.  
  
 [Transparent Data Encryption &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption-tde.md)  
 Informazioni generali sulla crittografia trasparente dei dati.  
  
 [Chiavi di crittografia del database e di SQL Server &#40;Motore di database&#41;](../../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le chiavi di crittografia sono costituite da una combinazione di chiavi pubbliche, private e simmetriche utilizzate per proteggere dati riservati. In questa sezione vengono illustrate l'implementazione e la gestione delle chiavi di crittografia.  
  
 [Always Encrypted &#40;Motore di database&#41;](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
 Garantisce che gli amministratori del database locale, gli operatori di database cloud o altri utenti con privilegi elevati, ma non autorizzati, non possano accedere ai dati crittografati.  
  
 [Mascheramento dati dinamici](../../../relational-databases/security/dynamic-data-masking.md)  
 Limita l'esposizione dei dati sensibili nascondendoli agli utenti senza privilegi.  
  
 [Certificati SQL Server e chiavi simmetriche](../../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)  
 Informazioni sull'uso della crittografia a chiave pubblica.  
  
## <a name="related-content"></a>Contenuto correlato  
 [Sicurezza di SQL Server](../../../relational-databases/security/securing-sql-server.md)  
 Panoramica della sicurezza della piattaforma [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e del funzionamento con gli utenti e gli oggetti a protezione diretta.  
  
 [Funzioni di crittografia &#40;Transact-SQL&#41;](../../../t-sql/functions/cryptographic-functions-transact-sql.md)  
 Informazioni sull'implementazione delle funzioni di crittografia.  
  
 [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](../../../t-sql/functions/encryptbypassphrase-transact-sql.md)  
 Informazioni sull'utilizzo di una password per la crittografia dei dati.  
  
 [ENCRYPTBYKEY &#40;Transact-SQL&#41;](../../../t-sql/functions/encryptbykey-transact-sql.md)  
 Informazioni sull'utilizzo di una chiave simmetrica per la crittografia dei dati.  
  
 [ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;](../../../t-sql/functions/encryptbyasymkey-transact-sql.md)  
 Informazioni sull'utilizzo di una chiave simmetrica per la crittografia dei dati.  
  
 [ENCRYPTBYCERT &#40;Transact-SQL&#41;](../../../t-sql/functions/encryptbycert-transact-sql.md)  
 Informazioni sull'utilizzo di un certificato per la crittografia dei dati.  
  
## <a name="external-resources"></a>Risorse esterne  
 [Microsoft TechNet: SQL Server TechCenter: Sicurezza e protezione di SQL Server 2005](https://msdn.microsoft.com/sqlserver/bb895847.aspx)  
 Informazioni aggiornate sulla sicurezza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [sys.key_encryptions &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-key-encryptions-transact-sql.md)   
 [Chiavi di crittografia del database e di SQL Server &#40;Motore di database&#41;](../../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [Eseguire il backup e il ripristino delle chiavi di crittografia di Reporting Services](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
  
  

