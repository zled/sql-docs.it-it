---
title: Set di righe dello Schema OLE DB | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- schema rowsets [OLE DB]
- schema rowsets [Analysis Services], OLE DB
- OLE DB schema rowsets
- rowsets [Analysis Services], OLE DB
ms.assetid: ca2ee87a-ba04-4501-9125-33934c58ab31
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6467a1e54dba2ad8a4e88f1d892dfa2f3cd64381
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="ole-db-schema-rowsets"></a>Set di righe dello schema OLE DB
  I set di righe dello schema OLE DB seguenti sono supportati dal provider di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA). Utilizzare il **DISCOVER_ENUMERATORS** set di righe con la [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo per verificare se un provider dell'origine dati supporta un set di righe.  
  
 Per ottenere informazioni dettagliate su questi set di righe, è inoltre possibile cercare l'argomento "Set di righe dello schema" nella parte relativa alla OLE DB Programmer's Reference in MSDN® Library nel sito Web [!INCLUDE[msCoName](../../../includes/msconame-md.md)].  
  
 Nella tabella seguente viene descritto questo set di righe dello schema.  
  
|Set di righe|Description|  
|------------|-----------------|  
|**DBSCHEMA_ASSERTIONS**|Identifica le asserzioni definite nel catalogo e di proprietà di un determinato utente.|  
|[Set di righe DBSCHEMA_CATALOGS](../../../analysis-services/schema-rowsets/ole-db/dbschema-catalogs-rowset.md) <sup>1</sup>|Identifica gli attributi fisici associati a cataloghi accessibili dal sistema di gestione di database (DBMS). Per alcuni sistemi, ad esempio [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Access, è possibile che sia presente un solo catalogo. Per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], questo set di righe enumera tutti i cataloghi (database) definiti nel database di sistema.|  
|**DBSCHEMA_CHARACTER_SETS**|Identifica i set di caratteri definiti nel catalogo e accessibili a un determinato utente.|  
|**DBSCHEMA_CHECK_CONSTRAINTS**|Identifica i vincoli CHECK definiti nel catalogo e di proprietà di un determinato utente.|  
|**DBSCHEMA_CHECK_CONSTRAINTS_BY_TABLE**|Identifica i vincoli CHECK per una tabella specifica, definiti in un catalogo di proprietà di un determinato utente.|  
|**DBSCHEMA_COLLATIONS**|Identifica le regole di confronto tra i caratteri definite nel catalogo e accessibili a un determinato utente.|  
|**DBSCHEMA_COLUMN_DOMAIN_USAGE**|Identifica le colonne definite nel catalogo che dipendono da un dominio definito nel catalogo e di proprietà di un determinato utente.|  
|**DBSCHEMA_COLUMN_PRIVILEGES**|Identifica i privilegi sulle colonne di tabelle definiti nel catalogo e disponibili per un determinato utente o concessi da un determinato utente.|  
|[Set di righe DBSCHEMA_COLUMNS](../../../analysis-services/schema-rowsets/ole-db/dbschema-columns-rowset.md) <sup>1</sup>|Fornisce informazioni di colonna per tutte le colonne che soddisfano i criteri di restrizione specificati.|  
|**DBSCHEMA_CONSTRAINT_COLUMN_USAGE**|Identifica le colonne utilizzate da vincoli referenziali, vincoli UNIQUE e vincoli CHECK, nonché le asserzioni definite nel catalogo e di proprietà di un determinato utente.|  
|**DBSCHEMA_CONSTRAINT_TABLE_USAGE**|Identifica le tabelle utilizzate da vincoli referenziali, vincoli UNIQUE e vincoli CHECK, nonché le asserzioni definite nel catalogo e di proprietà di un determinato utente.|  
|**DBSCHEMA_FOREIGN_KEYS**|Identifica le colonne chiave esterne definite nel catalogo da un determinato utente. Per maggiore praticità dei programmatori non SQL, questo set di righe dello schema si basa su diverse viste degli schemi ISO. Se supportato, questo set di righe dello schema deve essere sincronizzato con le viste ISO correlate (**REFERENTIAL_CONSTRAINTS** e **CONSTRAINT_COLUMN_USAGE**).|  
|**DBSCHEMA_INDEXES**|Identifica gli indici definiti nel catalogo e di proprietà di un determinato utente.|  
|**DBSCHEMA_KEY_COLUMN_USAGE**|Identifica le colonne definite nel catalogo e vincolate come chiavi da un determinato utente.|  
|**DBSCHEMA_PRIMARY_KEYS**|Identifica le colonne chiave primaria definite nel catalogo da un determinato utente. Per maggiore praticità dei programmatori non SQL, questo set di righe dello schema si basa su una vista dello schema ISO. Se supportato, questo set di righe dello schema deve essere sincronizzata con la vista ISO correlata (**CONSTRAINT_COLUMN_USAGE**).|  
|**DBSCHEMA_PROCEDURE_COLUMNS**|Restituisce informazioni sulle colonne di set di righe restituite da procedure.|  
|**DBSCHEMA_PROCEDURE_PARAMETERS**|Restituisce informazioni sui parametri e i codici restituiti da procedure.|  
|**DBSCHEMA_PROCEDURES**|Identifica le procedure definite nel catalogo e di proprietà di un determinato utente. Questa è un'estensione OLE DB.|  
|[Set di righe DBSCHEMA_PROVIDER_TYPES](../../../analysis-services/schema-rowsets/ole-db/dbschema-provider-types-rowset.md) <sup>1</sup>|Identifica i tipi di dati (di base) supportati dal provider di dati.|  
|**DBSCHEMA_REFERENTIAL_CONSTRAINTS**|Identifica i vincoli referenziali definiti nel catalogo e di proprietà di un determinato utente.|  
|**DBSCHEMA_SCHEMATA**|Identifica gli schemi di proprietà di un determinato utente.|  
|**DBSCHEMA_SQL_LANGUAGES**|Identifica i livelli di conformità, le opzioni e i sottolinguaggi supportati dai dati di elaborazione dell'implementazione SQL definiti nel catalogo.|  
|**DBSCHEMA_STATISTICS**|Identifica le statistiche definite nel catalogo e di proprietà di un determinato utente.<br /><br /> Questa tabella non è correlata la **TABLE_STATISTICS** set di righe.|  
|**DBSCHEMA_TABLE_CONSTRAINTS**|Identifica i vincoli di tabella definiti nel catalogo e di proprietà di un determinato utente.|  
|**DBSCHEMA_TABLE_PRIVILEGES**|Identifica i privilegi sulle tabelle definiti nel catalogo e disponibili per un determinato utente o concessi da un determinato utente.|  
|**DBSCHEMA_TABLE_STATISTICS**|Descrive i set di statistiche disponibili relativi alle tabelle nel provider.<br /><br /> Questo set di righe non è correlato il **statistiche** set di righe.|  
|[Set di righe DBSCHEMA_TABLES](../../../analysis-services/schema-rowsets/ole-db/dbschema-tables-rowset.md) <sup>1</sup>|Identifica i gruppi di misure e le dimensioni esposte come tabelle all'interno di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|**DBSCHEMA_TABLES_INFO** <sup>1</sup>|Identifica le tabelle, incluse le viste, definite nel catalogo e accessibili a un determinato utente.|  
|**DBSCHEMA_TRANSLATIONS**|Identifica le traduzioni dei caratteri definite nel catalogo e accessibili a un determinato utente.|  
|**DBSCHEMA_TRUSTEE**|Enumera le terze parti trusted per un'origine dati.|  
|**DBSCHEMA_USAGE_PRIVILEGES**|Identifica la **utilizzo** privilegi per gli oggetti che sono definiti nel catalogo e sono disponibili a o concessi da un determinato utente.|  
|**DBSCHEMA_VIEW_COLUMN_USAGE**|Identifica le viste definite nel catalogo e accessibili a un determinato utente.|  
|**DBSCHEMA_VIEW_TABLE_USAGE**|Identifica le tabelle da cui dipendono le tabelle visualizzate, definite nel catalogo e di proprietà di un determinato utente.|  
|**DBSCHEMA_VIEWS**|Identifica le viste definite nel catalogo e accessibili a un determinato utente.|  
  
 <sup>1</sup> indica di righe dello schema supportati dal provider dell'origine dati MSOLAP per il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] provider XMLA.  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe DISCOVER_ENUMERATORS](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)   
 [Set di righe dello Schema di Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  

