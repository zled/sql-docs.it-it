---
title: CERTPROPERTY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CERTPROPERTY
- CERTPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], schema names
- schemas [SQL Server], names
- CERTPROPERTY function
ms.assetid: 966c09aa-bc4e-45b0-ba53-c8381871f638
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4b43b587688b574c6d6395b72c5b368b82e617fd
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="certproperty-transact-sql"></a>CERTPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce il valore di una proprietà del certificato specificata.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CertProperty ( Cert_ID , '<PropertyName>' )  
  
<PropertyName> ::=  
   Expiry_Date | Start_Date | Issuer_Name   
   | Cert_Serial_Number | Subject | SID | String_SID   
```  
  
## <a name="arguments"></a>Argomenti  
*Cert_ID*  
ID del certificato. *Cert_ID* è un tipo int.
  
*Expiry_Date*  
Data di scadenza del certificato.
  
*Start_Date*  
Data in cui il certificato è diventato valido.
  
*Issuer_Name*  
Nome dell'autorità che ha emesso il certificato.
  
*Cert_Serial_Number*  
Numero di serie del certificato.
  
*Oggetto*  
Oggetto del certificato.
  
 *SID*  
SID del certificato. Corrisponde anche al SID di qualsiasi account di accesso o utente sul quale è stato eseguito il mapping al certificato.
  
*String_SID*  
SID del certificato nel formato di stringa di caratteri. Corrisponde anche al SID di qualsiasi account di accesso o utente sul quale è stato eseguito il mapping al certificato.
  
## <a name="return-types"></a>Tipi restituiti
La specifica della proprietà deve essere racchiusa tra virgolette singole.
  
Il tipo restituito dipende dalla proprietà specificata nella chiamata alla funzione. Restituire tutte vengono inclusi nel tipo restituito di **sql_variant**.
-   *Expiry_Date* e *Start_Date* restituire **datetime**.  
-   *Cert_Serial_Number*, *Issuer_Name*, *soggetto*, e *String_SID* restituire **nvarchar**.  
-   *SID* restituisce **varbinary**.  
  
## <a name="remarks"></a>Osservazioni  
Informazioni sui certificati sono visibili nella [Sys. Certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md) vista del catalogo.
  
## <a name="permissions"></a>Permissions  
Sono richieste autorizzazioni per il certificato ed è necessario che al chiamante non sia stata negata l'autorizzazione VIEW DEFINITION per il certificato.
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene restituito l'oggetto del certificato.
  
```sql
-- First create a certificate.  
CREATE CERTIFICATE Marketing19 WITH   
    START_DATE = '04/04/2004' ,  
    EXPIRY_DATE = '07/07/2007' ,  
    SUBJECT = 'Marketing Print Division';  
GO  
  
-- Now use CertProperty to examine certificate  
-- Marketing19's properties.  
DECLARE @CertSubject sql_variant;  
set @CertSubject = CertProperty( Cert_ID('Marketing19'), 'Subject');  
PRINT CONVERT(nvarchar, @CertSubject);  
GO  
```  
  
## <a name="see-also"></a>Vedere anche
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
[Istruzione ALTER CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-certificate-transact-sql.md)  
[CERT_ID &#40; Transact-SQL &#41; ](../../t-sql/functions/cert-id-transact-sql.md) 
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)
[Sys. Certificates &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md) 
 [Viste del catalogo sicurezza &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)
  
  

