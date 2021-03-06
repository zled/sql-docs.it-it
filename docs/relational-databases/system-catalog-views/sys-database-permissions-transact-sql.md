---
title: Sys. database_permissions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_permissions
- sys.database_permissions_TSQL
- database_permissions_TSQL
- sys.database_permissions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_permissions catalog view
ms.assetid: c1e261f8-6cb0-4759-b5f1-5ec233602655
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 04d86251149708aa521166018d643fe8735d3ec6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837530"
---
# <a name="sysdatabasepermissions-transact-sql"></a>sys.database_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una riga per ogni autorizzazione o per ogni autorizzazione per le eccezioni di colonna nel database. Per le colonne, esiste una riga per ogni autorizzazione che è diversa dall'autorizzazione corrispondente a livello di oggetto. Se l'autorizzazione per la colonna è lo stesso come autorizzazione per l'oggetto corrispondente, nessuna riga per tale e l'autorizzazione applicato è quello dell'oggetto.  
  
> [!IMPORTANT]  
>  Le autorizzazioni a livello di colonna hanno la precedenza sulle autorizzazioni a livello di oggetto per la stessa entità.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**class**|**tinyint**|Identifica la classe per la quale esiste l'autorizzazione.<br /><br /> 0 = Database<br />1 = Oggetto o colonna<br />3 = Schema<br />4 = Entità di database<br />5 = assembly - **si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br />6 = Tipo<br />10 = raccolta di XML Schema: <br />                      **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br />15 = tipo di messaggio - **si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br />16 = contratto di servizio - **si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br />17 = Service - **si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br />18 = associazione al servizio remoto - **si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br />19 = route - **si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br />23 = catalogo full-Text - **si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br />24 = chiave simmetrica - **si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br />25 = - certificate **si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br />26 = chiave asimmetrica - **si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**class_desc**|**nvarchar(60)**|Descrizione della classe per cui esiste l'autorizzazione.<br /><br /> DATABASE<br /><br /> OBJECT_OR_COLUMN<br /><br /> SCHEMA<br /><br /> DATABASE_PRINCIPAL<br /><br /> ASSEMBLY<br /><br /> TYPE<br /><br /> XML_SCHEMA_COLLECTION<br /><br /> MESSAGE_TYPE<br /><br /> SERVICE_CONTRACT<br /><br /> SERVICE<br /><br /> REMOTE_SERVICE_BINDING<br /><br /> ROUTE<br /><br /> FULLTEXT_CATALOG<br /><br /> SYMMETRIC_KEYS<br /><br /> CERTIFICATE<br /><br /> ASYMMETRIC_KEY|  
|**major_id**|**int**|ID dell'elemento per cui esiste l'autorizzazione, interpretato in base alla classe di appartenenza. In genere, il **major_id** tratta semplicemente dell'ID che si applica a ciò che rappresenta la classe. <br /><br /> 0 = il database stesso <br /><br /> > 0 = l'ID oggetto per gli oggetti utente <br /><br /> \<0 = l'ID oggetto per gli oggetti di sistema |  
|**minor_id**|**int**|ID secondario dell'elemento per cui esiste l'autorizzazione, interpretato in base alla classe di appartenenza. Spesso, il **minor_id** è zero, perché non è disponibile per la classe dell'oggetto non subcategory. In caso contrario, è l'ID colonna di una tabella.|  
|**grantee_principal_id**|**int**|ID dell'entità di database alla quale vengono concesse le autorizzazioni.|  
|**grantor_principal_id**|**int**|ID dell'entità di database dell'utente che concede queste autorizzazioni.|  
|**type**|**Char(4)**|Tipo di autorizzazione per il database Per un elenco dei tipi di autorizzazioni, vedere la tabella seguente.|  
|**permission_name**|**nvarchar(128)**|Nome dell'autorizzazione.|  
|**state**|**char(1)**|Stato dell'autorizzazione:<br /><br /> D = Deny<br /><br /> R = Revoke<br /><br /> G = Grant<br /><br /> W = Grant With Grant Option|  
|**state_desc**|**nvarchar(60)**|Descrizione dello stato dell'autorizzazione:<br /><br /> DENY<br /><br /> REVOKE<br /><br /> GRANT<br /><br /> GRANT_WITH_GRANT_OPTION|  

## <a name="database-permissions"></a>Autorizzazioni per il database   
I tipi di autorizzazioni seguenti sono possibili.
  
|Tipo di autorizzazione|Nome dell'autorizzazione|Entità a protezione diretta a cui si applica|  
|---------------------|---------------------|--------------------------|  
|AADS |ALTER ANY DATABASE EVENT SESSION |DATABASE |  
|AAMK |ALTER ANY MASK |DATABASE |  
|AEDS |ALTER ANY EXTERNAL DATA SOURCE |DATABASE |  
|AEFF |ALTER ANY EXTERNAL FILE FORMAT |DATABASE |  
|AL|ALTER|APPLICATION ROLE, ASSEMBLY, ASYMMETRIC KEY, CERTIFICATE, CONTRACT, DATABASE, FULLTEXT CATALOG, MESSAGE TYPE, OBJECT, REMOTE SERVICE BINDING, ROLE, ROUTE, SCHEMA, SERVICE, SYMMETRIC KEY, USER, XML SCHEMA COLLECTION|  
|ALAK|ALTER ANY ASYMMETRIC KEY|DATABASE|  
|ALAR|ALTER ANY APPLICATION ROLE|DATABASE|  
|ALAS|ALTER ANY ASSEMBLY|DATABASE|  
|ALCF|ALTER ANY CERTIFICATE|DATABASE|  
|ALDS|ALTER ANY DATASPACE|DATABASE|  
|ALED|ALTER ANY DATABASE EVENT NOTIFICATION|DATABASE|  
|ALFT|ALTER ANY FULLTEXT CATALOG|DATABASE|  
|ALMT|ALTER ANY MESSAGE TYPE|DATABASE|  
|ALRL|ALTER ANY ROLE|DATABASE|  
|ALRT|ALTER ANY ROUTE|DATABASE|  
|ALSB|ALTER ANY REMOTE SERVICE BINDING|DATABASE|  
|ALSC|ALTER ANY CONTRACT|DATABASE|  
|ALSK|ALTER ANY SYMMETRIC KEY|DATABASE|  
|ALSM|ALTER ANY SCHEMA|DATABASE|  
|ALSV|ALTER ANY SERVICE|DATABASE|  
|ALTG|ALTER ANY DATABASE DDL TRIGGER|DATABASE|  
|ALUS|ALTER ANY USER|DATABASE|  
|AUTH|AUTHENTICATE|DATABASE|  
|BADB|BACKUP DATABASE|DATABASE|  
|BALO|BACKUP LOG|DATABASE|  
|CL|CONTROL|APPLICATION ROLE, ASSEMBLY, ASYMMETRIC KEY, CERTIFICATE, CONTRACT, DATABASE, FULLTEXT CATALOG, MESSAGE TYPE, OBJECT, REMOTE SERVICE BINDING, ROLE, ROUTE, SCHEMA, SERVICE, SYMMETRIC KEY, TYPE, USER, XML SCHEMA COLLECTION|  
|CO|CONNECT|DATABASE|  
|CORP|CONNECT REPLICATION|DATABASE|  
|CP|CHECKPOINT|DATABASE|  
|CRAG|CREATE AGGREGATE|DATABASE|  
|CRAK|CREATE ASYMMETRIC KEY|DATABASE|  
|CRAS|CREATE ASSEMBLY|DATABASE|  
|CRCF|CREATE CERTIFICATE|DATABASE|  
|CRDB|CREATE DATABASE|DATABASE|  
|CRDF|CREATE DEFAULT|DATABASE|  
|CRED|CREATE DATABASE DDL EVENT NOTIFICATION|DATABASE|  
|CRFN|CREATE FUNCTION|DATABASE|  
|CRFT|CREATE FULLTEXT CATALOG|DATABASE|  
|CRMT|CREATE MESSAGE TYPE|DATABASE|  
|CRPR|CREATE PROCEDURE|DATABASE|  
|CRQU|CREATE QUEUE|DATABASE|  
|CRRL|CREATE ROLE|DATABASE|  
|CRRT|CREATE ROUTE|DATABASE|  
|CRRU|CREATE RULE|DATABASE|  
|CRSB|CREATE REMOTE SERVICE BINDING|DATABASE|  
|CRSC|CREATE CONTRACT|DATABASE|  
|CRSK|CREATE SYMMETRIC KEY|DATABASE|  
|CRSM|CREATE SCHEMA|DATABASE|  
|CRSN|CREATE SYNONYM|DATABASE|  
|CRSO|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> CREATE SEQUENCE|DATABASE|  
|CRSV|CREATE SERVICE|DATABASE|  
|CRTB|CREATE TABLE|DATABASE|  
|CRTY|CREATE TYPE|DATABASE|  
|CRVW|CREATE VIEW|DATABASE|  
|CRXS|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> CREATE XML SCHEMA COLLECTION|DATABASE|  
|DABO |ADMINISTER DATABASE BULK OPERATIONS | DATABASE |
|DL|Elimina|DATABASE, OBJECT, SCHEMA|  
|EAES |EXECUTE ANY EXTERNAL SCRIPT |DATABASE |
|EX|EXECUTE|ASSEMBLY, DATABASE, OBJECT, SCHEMA, TYPE, XML SCHEMA COLLECTION|  
|IM|IMPERSONATE|Utente|  
|IN|INSERT|DATABASE, OBJECT, SCHEMA|  
|RC|RECEIVE|OBJECT|  
|RF|REFERENCES|ASSEMBLY, ASYMMETRIC KEY, CERTIFICATE, CONTRACT, DATABASE, FULLTEXT CATALOG, MESSAGE TYPE, OBJECT, SCHEMA, SYMMETRIC KEY, TYPE, XML SCHEMA COLLECTION|  
|SL|SELECT|DATABASE, OBJECT, SCHEMA|  
|SN|SEND|SERVICE|  
|SPLN|SHOWPLAN|DATABASE|  
|SUQN|SUBSCRIBE QUERY NOTIFICATIONS|DATABASE|  
|TO|TAKE OWNERSHIP|ASSEMBLY, ASYMMETRIC KEY, CERTIFICATE, CONTRACT, DATABASE, FULLTEXT CATALOG, MESSAGE TYPE, OBJECT, REMOTE SERVICE BINDING, ROLE, ROUTE, SCHEMA, SERVICE, SYMMETRIC KEY, TYPE, XML SCHEMA COLLECTION|  
|UP|UPDATE|DATABASE, OBJECT, SCHEMA|  
|VW|VIEW DEFINITION|APPLICATION ROLE, ASSEMBLY, ASYMMETRIC KEY, CERTIFICATE, CONTRACT, DATABASE, FULLTEXT CATALOG, MESSAGE TYPE, OBJECT, REMOTE SERVICE BINDING, ROLE, ROUTE, SCHEMA, SERVICE, SYMMETRIC KEY, TYPE, USER, XML SCHEMA COLLECTION|  
|VWCK |VIEW ANY COLUMN ENCRYPTION KEY DEFINITION|DATABASE |  
|VWCM |VIEW ANY COLUMN MASTER KEY DEFINITION|DATABASE |  
|VWCT|VIEW CHANGE TRACKING|TABLE, SCHEMA|  
|VWDS|VIEW DATABASE STATE|DATABASE|  
  
## <a name="permissions"></a>Permissions  
 Qualsiasi utente può visualizzare le proprie autorizzazioni. Per visualizzare le autorizzazioni di altri utenti, è richiesta VIEW DEFINITION, ALTER ANY USER o qualsiasi autorizzazione per un utente. Per visualizzare i ruoli definiti dall'utente, è richiesta l'autorizzazione ALTER ANY ROLE o l'appartenenza al ruolo (ad esempio pubblico).  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-listing-all-the-permissions-of-database-principals"></a>A: elenco di tutte le autorizzazioni delle entità di database  
 Nella query seguente vengono elencate le autorizzazioni concesse o negate in modo esplicito alle entità di database.  
  
> [!IMPORTANT]  
>  Le autorizzazioni dei ruoli predefiniti del database non sono incluse in sys.database_permissions. Pertanto, le entità di database potrebbero contenere ulteriori autorizzazioni non presenti in questo elenco.  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc, pe.permission_name  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
### <a name="b-listing-permissions-on-schema-objects-within-a-database"></a>B: elenco di autorizzazioni per gli oggetti dello schema all'interno di un database  
 Nella query seguente viene creato un join di sys.database_principals e sys.database_permissions con sys.objects e sys.schemas per elencare le autorizzazioni concesse o negate agli oggetti di uno schema specifico.  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc,   
    pe.permission_name, s.name + '.' + o.name AS ObjectName  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id  
JOIN sys.objects AS o  
    ON pe.major_id = o.object_id  
JOIN sys.schemas AS s  
    ON o.schema_id = s.schema_id;  
```  
    
  
## <a name="see-also"></a>Vedere anche  
 [Securables](../../relational-databases/security/securables.md)   
 [Gerarchia delle autorizzazioni &#40;Motore di database&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  


