---
title: Istruzione ALTER CERTIFICATE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 04/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_CERTIFICATE_TSQL
- ALTER CERTIFICATE
dev_langs:
- TSQL
helpviewer_keywords:
- ENCRYPTION BY PASSWORD option
- encryption [SQL Server], certificates
- modifying certificates
- private keys [SQL Server]
- ALTER CERTIFICATE statement
- certificates [SQL Server], modifying
ms.assetid: da4dc25e-72e0-4036-87ce-22de83160836
caps.latest.revision: 46
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cb83f32e2187025c916ee7291e5b52725db5af2c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-certificate-transact-sql"></a>ALTER CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Modifica la chiave privata utilizzata per crittografare un certificato, oppure ne aggiunge una nel caso in cui non sia presente alcuna chiave. Modifica la disponibilità di un certificato per [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ALTER CERTIFICATE certificate_name   
      REMOVE PRIVATE KEY  
    | WITH PRIVATE KEY ( <private_key_spec> [ ,... ] )  
    | WITH ACTIVE FOR BEGIN_DIALOG = [ ON | OFF ]  
  
<private_key_spec> ::=   
      FILE = 'path_to_private_key'   
    | DECRYPTION BY PASSWORD = 'key_password'   
    | ENCRYPTION BY PASSWORD = 'password'   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER CERTIFICATE certificate_name   
{  
      REMOVE PRIVATE KEY  
    | WITH PRIVATE KEY (   
        FILE = '<path_to_private_key>',  
        DECRYPTION BY PASSWORD = '<key password>' )
}  
```  
  
## <a name="arguments"></a>Argomenti  
 *nome_certificato*  
 Nome univoco con il quale il certificato è noto nel database.  
  
 FILE **='***path_to_private_key***'**  
 Specifica il percorso completo, compreso il nome del file, per la chiave privata. Questo parametro può essere un percorso locale o un percorso UNC di rete. L'accesso al file verrà effettuato nel contesto di sicurezza dell'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Quando si utilizza questa opzione, occorre verificare che l'account del servizio abbia accesso al file specificato.  
  
 DECRYPTION BY PASSWORD **='***key_password***'**  
 Specifica la password necessaria per decrittografare la chiave privata.  
  
 ENCRYPTION BY PASSWORD **='***password***'**  
 Viene specificata la password utilizzata per crittografare la chiave privata del certificato nel database. *password* deve soddisfare i requisiti dei criteri password Windows del computer in cui è in esecuzione l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere [Password Policy](../../relational-databases/security/password-policy.md).  
  
 REMOVE PRIVATE KEY  
 Specifica che la chiave privata non deve più essere mantenuta all'interno del database.  
  
 ACTIVE FOR BEGIN_DIALOG  **=**  {ON | OFF}  
 Rende il certificato disponibile per un initiator di una conversazione di dialogo di [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
## <a name="remarks"></a>Osservazioni  
 La chiave privata deve corrispondere alla chiave pubblica specificata da *nome_certificato*.  
  
 La clausola DECRYPTION BY PASSWORD può essere omessa se la password nel file è protetta con un valore di password Null.  
  
 Quando la chiave privata di un certificato già esistente nel database viene importata da un file, la chiave privata sarà protetta automaticamente dalla chiave master del database. Per proteggere la chiave privata con una password, utilizzare la frase ENCRYPTION BY PASSWORD.  
  
 L'opzione REMOVE PRIVATE KEY eliminerà la chiave privata del certificato dal database. Impostare tale opzione nei casi in cui la verifica delle firme verrà eseguita tramite certificato, o negli scenari di [!INCLUDE[ssSB](../../includes/sssb-md.md)] in cui non è richiesta una chiave privata. Non rimuovere la chiave privata di un certificato che protegge una chiave simmetrica.  
  
 Non è necessario specificare una password di decrittografia quando la chiave privata è crittografata tramite la chiave master del database.  
  
> [!IMPORTANT]  
>  Eseguire sempre una copia di archivio della chiave privata prima di rimuoverla dal database. Per altre informazioni, vedere [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md).  
  
 L'opzione WITH PRIVATE KEY non è disponibile in un database indipendente.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER per il certificato.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-changing-the-password-of-a-certificate"></a>A. Modifica della password di un certificato  
  
```  
ALTER CERTIFICATE Shipping04   
    WITH PRIVATE KEY (DECRYPTION BY PASSWORD = 'pGF$5DGvbd2439587y',  
    ENCRYPTION BY PASSWORD = '4-329578thlkajdshglXCSgf');  
GO  
```  
  
### <a name="b-changing-the-password-that-is-used-to-encrypt-the-private-key"></a>B. Modifica della password utilizzata per crittografare la chiave privata  
  
```  
ALTER CERTIFICATE Shipping11   
    WITH PRIVATE KEY (ENCRYPTION BY PASSWORD = '34958tosdgfkh##38',  
    DECRYPTION BY PASSWORD = '95hkjdskghFDGGG4%');  
GO  
```  
  
### <a name="c-importing-a-private-key-for-a-certificate-that-is-already-present-in-the-database"></a>C. Importazione di una chiave privata per un certificato che è già presente nel database  
  
```  
ALTER CERTIFICATE Shipping13   
    WITH PRIVATE KEY (FILE = 'c:\\importedkeys\Shipping13',  
    DECRYPTION BY PASSWORD = 'GDFLKl8^^GGG4000%');  
GO  
```  
  
### <a name="d-changing-the-protection-of-the-private-key-from-a-password-to-the-database-master-key"></a>D. Modifica del tipo di protezione della chiave privata, da password a chiave master di database  
  
```  
ALTER CERTIFICATE Shipping15   
    WITH PRIVATE KEY (DECRYPTION BY PASSWORD = '95hk000eEnvjkjy#F%');  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-importing-a-private-key-for-a-certificate-that-is-already-present-in-the-database"></a>E. Importazione di una chiave privata per un certificato che è già presente nel database  
  
```  
ALTER CERTIFICATE Shipping13   
    WITH PRIVATE KEY (FILE = '\\ServerA7\importedkeys\Shipping13',  
    DECRYPTION BY PASSWORD = 'GDFLKl8^^GGG4000%');  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

