---
title: Sys. fulltext_semantic_languages (Transact-SQL) | Documenti Microsoft
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
- fulltext_semantic_languages
- fulltext_semantic_languages_TSQL
- sys.fulltext_semantic_languages
- sys.fulltext_semantic_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_semantic_languages catalog view
ms.assetid: b42a85e6-1db9-4a22-8a70-014574c95198
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9527c410457a94f82eca6b8e7250823e3bc0c7b9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysfulltextsemanticlanguages-transact-sql"></a>sys.fulltext_semantic_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni lingua il cui modello delle statistiche è registrato con l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Quando un modello di lingua è registrato, la lingua è abilitata per l'indicizzazione semantica.  
  
 Questa vista del catalogo è simile a [Sys. fulltext_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md).  
    
||||  
|-|-|-|  
|**Nome colonna**|**Tipo**|**Description**|  
|lcid|int|ID delle impostazioni locali (LCID) di Microsoft Windows per la lingua.|  
|name|sysname|È il valore dell'alias in [Sys. syslanguages &#40;Transact-SQL&#41; ](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) corrispondente al valore di **lcid**, o la rappresentazione di stringa del LCID numerico.|  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Per altre informazioni, vedere [Installazione e configurazione della ricerca semantica](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
## <a name="metadata"></a>Metadati  
 Per ulteriori informazioni sul database di statistiche lingua semantica installato per supportare l'indicizzazione semantica, eseguire una query sulla vista del catalogo [Sys. fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 La visibilità dei metadati nelle viste del catalogo è limitata alle entità a protezione diretta di cui l'utente è proprietario o per le quali dispone di autorizzazioni.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente viene illustrato come eseguire una query **Sys. fulltext_semantic_languages** per ottenere informazioni su tutti i modelli di lingua registrati per l'indicizzazione nell'istanza corrente di semantica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT * FROM sys.fulltext_semantic_languages;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione e configurazione della ricerca semantica](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
