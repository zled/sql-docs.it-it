---
title: http_endpoints (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.http_endpoints
- http_endpoints
- sys.http_endpoints_TSQL
- http_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.http_endpoints catalog view
ms.assetid: 16f59695-ecd9-457e-8874-055af63f8ea7
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 6b6c0182715a823a481224295839cc7b61fda210
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="syshttpendpoints-transact-sql"></a>sys.http_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni endpoint creato nel server, che utilizza il protocollo HTTP.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**< colonne ereditate >**||Eredita le colonne da [Endpoints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**Sito**|**nvarchar(128)**|Nome del computer host per il sito, come specificato nell'opzione SITE =.|  
|**url_path**|**nvarchar(4000)**|Parte del percorso dell'URL per l'endpoint HTTP, come specificato nell'opzione PATH=.|  
|**is_clear_port_enabled**|**bit**|1 = Porta non protetta abilitata con l'opzione PORT = CLEAR.|  
|**CLEAR_PORT**|**int**|Numero di porta specificato nell'opzione CLEAR PORT =.<br /><br /> NULL = Non specificata.|  
|**is_ssl_port_enabled**|**bit**|1 = Porta SSL abilitata con l'opzione PORT = SSL.|  
|**SSL_PORT**|**int**|Valore del numero di porta specificato nell'opzione SSL PORT =.<br /><br /> NULL = Non specificata.|  
|**is_anonymous_enabled**|**bit**|1 = Accesso anonimo abilitato con l'opzione AUTHENTICATION = ANONYMOUS.|  
|**is_basic_auth_enabled**|**bit**|1 = Autenticazione di base abilitata con l'opzione AUTHENTICATION = BASIC.|  
|**is_digest_auth_enabled**|**bit**|1 = Autenticazione digest abilitata con l'opzione AUTHENTICATION = DIGEST.|  
|**is_kerberos_auth_enabled**|**bit**|1 = Autenticazione integrata abilitata con l'opzione AUTHENTICATION = KERBEROS.|  
|**is_ntlm_auth_enabled**|**bit**|1 = Autenticazione integrata abilitata con l'opzione AUTHENTICATION = NTLM.|  
|**is_integrated_auth_enabled**|**bit**|1 = Autenticazione integrata abilitata con l'opzione AUTHENTICATION = INTEGRATED.|  
|**authorization_realm**|**nvarchar(128)**|Hint restituito al client nell'ambito della richiesta di autenticazione HTTP DIGEST. Valore dell'opzione AUTH REALM.<br /><br /> NULL se non specificato o se l'autenticazione DIGEST non è abilitata.|  
|**DEFAULT_LOGON_DOMAIN**|**nvarchar(128)**|Dominio di accesso predefinito se si abilita l'autenticazione BASIC. Valore dell'opzione DEFAULT LOGON DOMAIN.<br /><br /> NULL se non specificato o se l'autenticazione BASIC non è abilitata.|  
|**is_compression_enabled**|**bit**|1 = Opzione COMPRESSION = ENABLED impostata.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo degli endpoint &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  
