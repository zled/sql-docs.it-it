---
title: CREAZIONE di certificati (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CERTIFICATE
- CREATE_CERTIFICATE_TSQL
- sql13.swb.createcertificate.f1
- CERTIFICATE_TSQL
- CREATE CERTIFICATE
- sql13.swb.certificateproperties.f1
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], certificates
- certificates [SQL Server], adding
- certificates [SQL Server]
- adding certificates
- cryptography [SQL Server], certificates
- CREATE CERTIFICATE statement
ms.assetid: a4274b2b-4cb0-446a-a956-1c8e6587515d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b77ff590d36f866c8679bfbc16e605565d9d8d1d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="create-certificate-transact-sql"></a>CREATE CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Aggiunge un certificato a un database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Questa funzionalità non è compatibile con l'esportazione del database mediante Data Tier Application Framework (DACFx). Prima dell'esportazione, è necessario eliminare tutti i certificati.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
CREATE CERTIFICATE certificate_name [ AUTHORIZATION user_name ]   
    { FROM <existing_keys> | <generate_new_keys> }  
    [ ACTIVE FOR BEGIN_DIALOG =  { ON | OFF } ]  
  
<existing_keys> ::=   
    ASSEMBLY assembly_name  
    | {   
        [ EXECUTABLE ] FILE = 'path_to_file'  
        [ WITH PRIVATE KEY ( <private_key_options> ) ]   
      }  
    | {   
        BINARY = asn_encoded_certificate  
        [ WITH PRIVATE KEY ( <private_key_options> ) ]  
      }  
<generate_new_keys> ::=   
    [ ENCRYPTION BY PASSWORD = 'password' ]   
    WITH SUBJECT = 'certificate_subject_name'   
    [ , <date_options> [ ,...n ] ]   
  
<private_key_options> ::=  
      {   
        FILE = 'path_to_private_key'  
         [ , DECRYPTION BY PASSWORD = 'password' ]  
         [ , ENCRYPTION BY PASSWORD = 'password' ]    
      }  
    |  
      {   
        BINARY = private_key_bits  
         [ , DECRYPTION BY PASSWORD = 'password' ]  
         [ , ENCRYPTION BY PASSWORD = 'password' ]    
      }  
  
<date_options> ::=  
    START_DATE = 'datetime' | EXPIRY_DATE = 'datetime'  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
CREATE CERTIFICATE certificate_name   
    { <generate_new_keys> | FROM <existing_keys> }  
    [ ; ]  
  
<generate_new_keys> ::=   
    WITH SUBJECT ='certificate_subject_name'   
    [ , <date_options> [ ,...n ] ]   
  
<existing_keys> ::=   
    {   
      FILE ='path_to_file'  
      WITH PRIVATE KEY   
         (   
           FILE ='path_to_private_key'  
           , DECRYPTION BY PASSWORD ='password'   
         )  
    }  
  
<date_options> ::=  
    START_DATE ='datetime' | EXPIRY_DATE ='datetime'  
```  
  
## <a name="arguments"></a>Argomenti  
 *nome_certificato*  
 È il nome per il certificato nel database.  
  
 AUTORIZZAZIONE *nome_utente*  
 È il nome dell'utente che possiede il certificato.  
  
 ASSEMBLY *nome_assembly*  
 Specifica un assembly firmato già caricato nel database.  
  
 [ESEGUIBILE] FILE ='*path_to_file*'  
 Specifica il percorso completo, nome di file incluso, del file con codifica DER che contiene il certificato. Se viene utilizzata l'opzione EXECUTABLE, il file è una DLL firmata dal certificato. *path_to_file* può essere un percorso locale o un percorso UNC di un percorso di rete. Nel contesto di sicurezza di accesso al file il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account del servizio. L'account deve disporre delle necessarie autorizzazioni per il file system.  
  
 WITH PRIVATE KEY  
 Specifica che la chiave privata del certificato viene caricata in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa clausola è valida solo se il certificato viene creato da un file. Per caricare la chiave privata di un assembly, utilizzare [ALTER CERTIFICATE](../../t-sql/statements/alter-certificate-transact-sql.md).  
  
 FILE ='*path_to_private_key*'  
 Specifica il percorso completo, compreso il nome del file, per la chiave privata. *path_to_private_key* può essere un percorso locale o un percorso UNC di un percorso di rete. Nel contesto di sicurezza di accesso al file il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account del servizio. L'account deve disporre delle necessarie autorizzazioni per il file system.  
  
> [!NOTE]  
>  Questa opzione non è disponibile in un database indipendente.  
  
 asn_encoded_certificate  
 Bit di un certificato con codifica ASN specificati come costante binaria.  
  
 BINARIO =*private_key_bits*  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Bit della chiave privata specificati come costante binaria. Questi bit possono essere in formato crittografato. Se crittografati, l'utente deve fornire una password di decrittografia. I controlli dei criteri della password non vengono eseguiti su questa password. I bit della chiave privata devono essere in un formato di file PVK.  
  
 DECRYPTION BY PASSWORD ='*key_password*'  
 Specifica la password necessaria per decrittografare la chiave privata recuperata da un file. Questa clausola è facoltativa se la chiave privata è protetta con una password Null. Non è consigliabile salvare una chiave privata in un file senza proteggerla con una password. Se è necessaria una password senza non specifica alcuna password, l'istruzione ha esito negativo.  
  
 ENCRYPTION BY PASSWORD ='*password*'  
 Specifica la password utilizzata per crittografare la chiave privata. Utilizzare questa opzione solo se si desidera crittografare il certificato con una password. Se questa clausola viene omessa, la chiave privata è crittografata tramite la chiave master del database. *password* deve soddisfare i requisiti dei criteri password Windows del computer in cui è in esecuzione l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere [Password Policy](../../relational-databases/security/password-policy.md).  
  
 OGGETTO ='*certificate_subject_name*'  
 Il termine *soggetto* si riferisce a un campo nei metadati del certificato, come definito nello standard x. 509. L'oggetto deve essere lungo non più di 64 caratteri, e questo limite viene applicato per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Linux. Per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Windows, l'oggetto può essere fino a 128 caratteri. Oggetti che superano i 128 caratteri vengono troncati quando questi vengono archiviati nel catalogo, ma l'oggetto binario di grandi dimensioni (BLOB) che contiene il certificato viene mantenuto il nome di oggetto completo.  
  
 Start_date ='*datetime*'  
 Data di inizio validità del certificato. Se non specificato, START_DATE verrà impostata sulla data corrente. START_DATE è in ora UTC e si può specificare in un qualsiasi formato convertibile in una data e ora.  
  
 EXPIRY_DATE ='*datetime*'  
 Data di scadenza del certificato. Se non specificato, EXPIRY_DATE è impostato su una data un anno dopo START_DATE. EXPIRY_DATE è in ora UTC e si può specificare in un qualsiasi formato convertibile in una data e ora. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Service Broker viene controllata la data di scadenza. Tuttavia, scadenza non viene applicata quando il certificato viene utilizzato per la crittografia.  
  
 ACTIVE FOR BEGIN_DIALOG = { **ON** | OFF}  
 Rende il certificato disponibile per un initiator di una conversazione di dialogo di [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Il valore predefinito è ON.  
  
## <a name="remarks"></a>Osservazioni  
 Un certificato è un'entità a protezione diretta a livello di database conforme allo standard X.509 e che supporta i campi della specifica X.509 V1. L'istruzione CREATE CERTIFICATE consente di caricare un certificato da un file o un assembly e può inoltre essere utilizzata per generare una coppia di chiavi e creare un certificato autofirmato.  
  
 La chiave privata deve essere \<= 2500 byte in formato crittografato. Le chiavi private generate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono 1024 bit tempo tramite [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] e sono della lunghezza di 2048 bit a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Le chiavi private importate da un'origine esterna devono avere una lunghezza compresa tra 384 bit e 4,096 bit. La lunghezza di una chiave privata importata deve essere un valore intero multiplo di 64 bit. I certificati usati per TDE sono limitati a chiavi private con dimensioni di 3456 bit.  
  
 Il numero intero di serie del certificato viene archiviato, ma solo i primi 16 byte viene visualizzata nella vista del catalogo sys. Certificates.  
  
 L'intero campo emittente del certificato viene archiviato, ma solo i primi 884 byte di Sys. Certificates vista del catalogo.  
  
 La chiave privata deve corrispondere alla chiave pubblica specificata da *nome_certificato*.  
  
 Quando si crea un certificato da un contenitore, il caricamento della chiave privata è facoltativo. La chiave privata viene invece sempre creata quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un certificato autofirmato. Per impostazione predefinita, la chiave privata viene crittografata con la chiave master del database. Se la chiave master del database non esiste e non viene specificata, l'istruzione ha esito negativo.  
  
 L'opzione ENCRYPTION BY PASSWORD non è obbligatorio quando la chiave privata è crittografata con la chiave master del database. Utilizzare questa opzione solo quando la chiave privata è crittografata con una password. Se non si specifica la password, la chiave privata del certificato verrà crittografata con la chiave master del database. Se la chiave master del database non può essere aperto, si omette questa clausola causa un errore.  
  
 Non è necessario specificare una password di decrittografia quando la chiave privata è crittografata con la chiave master del database.  
  
> [!NOTE]  
>  Le funzioni predefinite per la crittografia e la firma non controllano le date di scadenza dei certificati. Gli utenti di queste funzioni dovranno decidere autonomamente quando eseguire il controllo delle scadenze dei certificati.  
  
 È possibile creare una descrizione binaria di un certificato utilizzando il [CERTENCODED &#40; Transact-SQL &#41; ](../../t-sql/functions/certencoded-transact-sql.md) e [CERTPRIVATEKEY &#40; Transact-SQL &#41; ](../../t-sql/functions/certprivatekey-transact-sql.md) funzioni. Per un esempio che utilizza **CERTPRIVATEKEY** e **CERTENCODED** per copiare un certificato a un altro database, vedere l'esempio B nell'argomento [CERTENCODED &#40; Transact-SQL &#41; ](../../t-sql/functions/certencoded-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CREATE CERTIFICATE per il database. Solo account di accesso Windows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gli account di accesso e i ruoli applicazione possono disporre di certificati. I gruppi e i ruoli non possono disporre di certificati.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-a-self-signed-certificate"></a>A. Creazione di un certificato autofirmato  
 Nell'esempio seguente viene creato un certificato denominato `Shipping04`. La chiave privata di questo certificato è protetta con una password.  
  
```  
CREATE CERTIFICATE Shipping04   
   ENCRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y'  
   WITH SUBJECT = 'Sammamish Shipping Records',   
   EXPIRY_DATE = '20201031';  
GO  
```  
  
### <a name="b-creating-a-certificate-from-a-file"></a>B. Creazione di un certificato da un file  
 Nell'esempio seguente viene creato un certificato nel database e la coppia di chiavi viene caricata da file.  
  
```  
CREATE CERTIFICATE Shipping11   
    FROM FILE = 'c:\Shipping\Certs\Shipping11.cer'   
    WITH PRIVATE KEY (FILE = 'c:\Shipping\Certs\Shipping11.pvk',   
    DECRYPTION BY PASSWORD = 'sldkflk34et6gs%53#v00');  
GO   
```  
  
### <a name="c-creating-a-certificate-from-a-signed-executable-file"></a>C. Creazione di un certificato da un file eseguibile firmato  
  
```  
CREATE CERTIFICATE Shipping19   
    FROM EXECUTABLE FILE = 'c:\Shipping\Certs\Shipping19.dll';  
GO  
```  
  
 In alternativa, è possibile creare un assembly dal file `dll` e quindi creare un certificato dall'assembly.  
  
```  
CREATE ASSEMBLY Shipping19   
    FROM ' c:\Shipping\Certs\Shipping19.dll'   
    WITH PERMISSION_SET = SAFE;  
GO  
CREATE CERTIFICATE Shipping19 FROM ASSEMBLY Shipping19;  
GO  
```  
  
### <a name="d-creating-a-self-signed-certificate"></a>D. Creazione di un certificato autofirmato  
 Nell'esempio seguente viene creato un certificato denominato `Shipping04` senza specificare una password di crittografia. Questo esempio può essere utilizzato con [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].
  
```  
CREATE CERTIFICATE Shipping04   
   WITH SUBJECT = 'Sammamish Shipping Records';  
GO  
```  
  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione ALTER CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [CERTENCODED &#40; Transact-SQL &#41;](../../t-sql/functions/certencoded-transact-sql.md)   
 [CERTPRIVATEKEY &#40; Transact-SQL &#41;](../../t-sql/functions/certprivatekey-transact-sql.md)  
  
  


