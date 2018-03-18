---
title: CERTPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d63968d8b07a37ea49662bd0727632a1675b3913
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="certproperty-transact-sql"></a>CERTPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
ID del certificato. *Cert_ID* è di tipo int.
  
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
  
Il tipo restituito dipende dalla proprietà specificata nella chiamata alla funzione. Tutti i valori restituiti vengono inclusi nel tipo restituito di **sql_variant**.
-   *Expiry_Date* e *Start_Date* restituiscono **datetime**.  
-   *Cert_Serial_Number*, *Issuer_Name*, *Subject* e *String_SID* restituiscono **nvarchar**.  
-   *SID* restituisce un valore **varbinary**.  
  
## <a name="remarks"></a>Remarks  
Le informazioni sui certificati sono visibili nella vista del catalogo [sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md).
  
## <a name="permissions"></a>Autorizzazioni  
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
[ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)  
[CERT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/cert-id-transact-sql.md)
[Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)
[sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)
[Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)
  
  
