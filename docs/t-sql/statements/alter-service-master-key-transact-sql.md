---
title: ALTER SERVICE MASTER KEY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SERVICE_MASTER_KEY_TSQL
- ALTER SERVICE MASTER KEY
dev_langs:
- TSQL
helpviewer_keywords:
- REGENERATE phrase
- FORCE option
- ALTER SERVICE MASTER KEY statement
- cryptography [SQL Server], Service Master Key
- modifying Service Master Key
- decryption [SQL Server], Service Master Key
- encryption [SQL Server], Service Master Key
- service master key [SQL Server], modifying
ms.assetid: a1e9be0e-4115-47d8-9d3a-3316d876a35e
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4ee9fd8a888ed796b4d01b007aec5f8217cce5d9
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-service-master-key-transact-sql"></a>ALTER SERVICE MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica la chiave master del servizio di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ALTER SERVICE MASTER KEY   
    [ { <regenerate_option> | <recover_option> } ] [;]  
  
<regenerate_option> ::=  
    [ FORCE ] REGENERATE  
  
<recover_option> ::=  
    { WITH OLD_ACCOUNT = 'account_name' , OLD_PASSWORD = 'password' }  
    |      
    { WITH NEW_ACCOUNT = 'account_name' , NEW_PASSWORD = 'password' }  
```  
  
## <a name="arguments"></a>Argomenti  
 FORCE  
 Indica che la chiave master del servizio deve essere rigenerata, anche a rischio di perdita dei dati. Per ulteriori informazioni, vedere [modifica l'Account del servizio SQL Server](#_changing) più avanti in questo argomento.  
  
 REGENERATE  
 Indica che la chiave master del servizio deve essere rigenerata.  
  
 OLD_ACCOUNT **='***account_name***'**  
 Specifica il nome dell'account del servizio Windows precedente.  
  
> [!WARNING]  
>  Questa opzione è obsoleta. Non usare. In alternativa, utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 OLD_PASSWORD **='***password***'**  
 Specifica la password dell'account del servizio Windows precedente.  
  
> [!WARNING]  
>  Questa opzione è obsoleta. Non usare. In alternativa, utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 NEW_ACCOUNT **='***account_name***'**  
 Specifica il nome del nuovo account del servizio Windows.  
  
> [!WARNING]  
>  Questa opzione è obsoleta. Non usare. In alternativa, utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 NEW_PASSWORD **='***password***'**  
 Specifica la password del nuovo account del servizio Windows.  
  
> [!WARNING]  
>  Questa opzione è obsoleta. Non usare. In alternativa, utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="remarks"></a>Osservazioni  
 La chiave master del servizio viene generata automaticamente la prima volta che risulta necessaria per crittografare la password di un server collegato, le credenziali o la chiave master del database. La chiave master del servizio viene crittografata mediante la chiave del computer locale o l'API Windows per la protezione dei dati (DAPI, Data Protection API). In questa API viene utilizzata una chiave derivata dalle credenziali di Windows dell'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] usa l'algoritmo di crittografia AES per proteggere la chiave master del servizio (SMK) e la chiave master del database (DMK). AES è un algoritmo di crittografia più recente rispetto a 3DES utilizzato nelle versioni precedenti. Dopo aver aggiornato un'istanza di [!INCLUDE[ssDE](../../includes/ssde-md.md)] a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] le chiavi SMK e DMK devono essere rigenerate per aggiornare le chiavi master ad AES. Per altre informazioni sulla rigenerazione della DMK, vedere [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md).  
  
##  <a name="_changing"></a>Modifica l'Account del servizio SQL Server  
 Per modificare l'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per gestire una modifica dell'account del servizio, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] archivia una copia ridondante della chiave master del servizio protetta dall'account del computer che ha le autorizzazioni necessarie per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gruppo del servizio. Se il computer viene ricompilato, lo stesso utente di dominio utilizzato in precedenza dall'account del servizio può recuperare la chiave master del servizio. Questo non funziona con gli account locali o di sistema locale, servizio locale o servizio di rete. Quando si stanno spostando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a un altro computer, eseguire la migrazione la chiave master del servizio tramite backup e ripristino.  
  
 L'istruzione REGENERATE consente di rigenerare la chiave master del servizio. In seguito alla rigenerazione della chiave master del servizio, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] decrittografa tutte le chiavi crittografate con tale chiave e quindi le crittografa con la nuova chiave master del servizio. Si tratta di un'operazione che utilizza molte risorse e pertanto dovrebbe essere pianificata in periodi di carico ridotto, a meno che la chiave non sia stata compromessa. In caso di esito negativo di una qualsiasi delle operazioni di decrittografia, l'intera istruzione avrà esito negativo.  
  
 L'opzione FORCE consente di continuare il processo di rigenerazione della chiave anche se non è possibile recuperare la chiave master corrente o decrittografare tutte le chiavi private crittografate con tale chiave master. Utilizzare l'opzione FORCE solo se la rigenerazione non riesce ed è possibile ripristinare la chiave master del servizio usando il [RESTORE SERVICE MASTER KEY](../../t-sql/statements/restore-service-master-key-transact-sql.md) istruzione.  
  
> [!CAUTION]  
>  La chiave master del servizio è l'elemento radice della gerarchia di crittografia di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Con la chiave master del servizio vengono protetti direttamente o indirettamente tutte le altre chiavi e tutti i segreti nell'albero. Se non è possibile decrittografare una chiave dipendente durante una rigenerazione forzata, i dati protetti dalla chiave andranno perduti.  
  
 Se si sposta SQL in un altro computer, è necessario utilizzare lo stesso account del servizio per decrittografare SMK. Tramite SQL Server verrà corretta automaticamente la crittografia dell'account del computer.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL SERVER per il server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rigenerata la chiave master del servizio.  
  
```  
ALTER SERVICE MASTER KEY REGENERATE;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [RIPRISTINARE la chiave MASTER del servizio &#40; Transact-SQL &#41;](../../t-sql/statements/restore-service-master-key-transact-sql.md)   
 [CHIAVE MASTER del servizio di BACKUP &#40; Transact-SQL &#41;](../../t-sql/statements/backup-service-master-key-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

