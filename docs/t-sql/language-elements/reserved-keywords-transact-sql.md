---
title: Parole chiave (Transact-SQL) riservate | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- ODBC function calls
- keywords [SQL Server], reserved
- reserved words [SQL Server]
- keywords [SQL Server]
ms.assetid: ed8b3e27-6796-40f0-aef3-0cac5e0e2418
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 65ef776b119b40bbeb4bbdddcfe0a4a99379a833
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="reserved-keywords-transact-sql"></a>Parole chiave riservate (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizza parole chiave riservate per la definizione, la modifica e l'accesso ai database. Le parole chiave riservate fanno parte della grammatica del linguaggio [!INCLUDE[tsql](../../includes/tsql-md.md)] utilizzata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per analizzare e interpretare istruzioni e batch [!INCLUDE[tsql](../../includes/tsql-md.md)]. Nonostante da un punto di vista sintattico sia possibile utilizzare le parole chiave riservate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come identificatori e nomi di oggetto all'interno di script [!INCLUDE[tsql](../../includes/tsql-md.md)], in tal caso è necessario utilizzare identificatori delimitati.  
  
 Nella tabella seguente vengono elencate le parole chiave riservate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
||||  
|-|-|-|  
|ADD|EXTERNAL|PROCEDURE|  
|ALL|FETCH|PUBLIC|  
|ALTER|FILE|RAISERROR|  
|AND|FILLFACTOR|READ|  
|ANY|FOR|READTEXT|  
|AS|FOREIGN|RECONFIGURE|  
|ASC|FREETEXT|REFERENCES|  
|AUTHORIZATION|FREETEXTTABLE|REPLICATION|  
|BACKUP|FROM|RESTORE|  
|BEGIN|FULL|RESTRICT|  
|BETWEEN|FUNCTION|RETURN|  
|BREAK|GOTO|REVERT|  
|BROWSE|GRANT|REVOKE|  
|BULK|GROUP|RIGHT|  
|BY|HAVING|ROLLBACK|  
|CASCADE|HOLDLOCK|ROWCOUNT|  
|CASE|IDENTITY|ROWGUIDCOL|  
|CHECK|IDENTITY_INSERT|RULE|  
|CHECKPOINT|IDENTITYCOL|SAVE|  
|CLOSE|IF|SCHEMA|  
|CLUSTERED|IN|SECURITYAUDIT|  
|COALESCE|INDEX|SELECT|  
|COLLATE|INNER|SEMANTICKEYPHRASETABLE|  
|COLUMN|INSERT|SEMANTICSIMILARITYDETAILSTABLE|  
|COMMIT|INTERSECT|SEMANTICSIMILARITYTABLE|  
|COMPUTE|INTO|SESSION_USER|  
|CONSTRAINT|IS|SET|  
|CONTAINS|JOIN|SETUSER|  
|CONTAINSTABLE|KEY|SHUTDOWN|  
|CONTINUE|KILL|SOME|  
|CONVERT|LEFT|STATISTICS|  
|CREATE|LIKE|SYSTEM_USER|  
|CROSS|LINENO|TABLE|  
|CURRENT|LOAD|TABLESAMPLE|  
|CURRENT_DATE|MERGE|TEXTSIZE|  
|CURRENT_TIME|NATIONAL|THEN|  
|CURRENT_TIMESTAMP|NOCHECK|TO|  
|CURRENT_USER|NONCLUSTERED|Torna all'inizio|  
|CURSOR|NOT|TRAN|  
|DATABASE|NULL|TRANSACTION|  
|DBCC|NULLIF|TRIGGER|  
|DEALLOCATE|OF|TRUNCATE|  
|DECLARE|OFF|TRY_CONVERT|  
|DEFAULT|OFFSETS|TSEQUAL|  
|DELETE|ON|UNION|  
|DENY|OPEN|UNIQUE|  
|DESC|OPENDATASOURCE|UNPIVOT|  
|DISK|OPENQUERY|UPDATE|  
|DISTINCT|OPENROWSET|UPDATETEXT|  
|DISTRIBUTED|OPENXML|USE|  
|DOUBLE|OPTION|Utente|  
|DROP|OPPURE|VALUES|  
|DUMP|ORDER|VARYING|  
|ELSE|OUTER|VIEW|  
|END|OVER|WAITFOR|  
|ERRLVL|PERCENT|WHEN|  
|ESCAPE|PIVOT|WHERE|  
|EXCEPT|PLAN|WHILE|  
|EXEC|PRECISION|con|  
|EXECUTE|PRIMARY|WITHIN GROUP|  
|EXISTS|PRINT|WRITETEXT|  
|EXIT|PROC||  
  
 Lo standard ISO definisce inoltre un elenco di parole chiave riservate. Non utilizzare le parole chiave riservate di ISO per i nomi di oggetto e gli identificatori. Le parole chiave riservate di ODBC, elencate nella tabella seguente, corrispondono a quelle di ISO.  
  
> [!NOTE]  
>  L'elenco delle parole chiave riservate degli standard ISO può essere più o meno restrittivo rispetto a quello di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ad esempio, l'elenco di parole chiave riservate di ISO contiene **INT**. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tale valore non deve essere distinto come parola chiave riservata.  
  
 È possibile utilizzare le parole chiave riservate [!INCLUDE[tsql](../../includes/tsql-md.md)] come identificatori o nomi di database o di oggetti di database, ad esempio tabelle, colonne, viste e così via. A tale scopo, utilizzare identificatori tra virgolette o delimitati. È inoltre possibile utilizzare le parole chiave riservate come nomi di variabili e parametri di stored procedure.  
  
## <a name="odbc-reserved-keywords"></a>Parole chiave riservate di ODBC  
 Le parole elencate di seguito sono riservate per l'utilizzo in chiamate di funzioni di ODBC. Queste parole non limitano la grammatica SQL minima. Tuttavia, per garantire la compatibilità con driver che supportano la grammatica SQL di base, è consigliabile evitare l'utilizzo di queste parole riservate nelle applicazioni.  
  
 Di seguito è riportato l'elenco corrente delle parole chiave riservate di ODBC.  
  
||||  
|-|-|-|  
|**ABSOLUTE**|**EXEC**|**SI SOVRAPPONE**|  
|**AZIONE**|**EXECUTE**|**PAD**|  
|**ADA**|**EXISTS**|**PARZIALE**|  
|**ADD**|**EXTERNAL**|**PASCAL**|  
|**ALL**|**EXTRACT**|**POSIZIONE**|  
|**ALLOCARE**|**FALSE**|**PRECISIONE**|  
|**ALTER**|**FETCH**|**PREPARARE**|  
|**AND**|**FIRST**|**MANTENERE**|  
|**ANY**|**FLOAT**|**PRIMARY**|  
|**SONO**|**PER**|**PRIMA**|  
|**Analysis Services**|**ESTERNA**|**PRIVILEGI**|  
|**ASC**|**FORTRAN**|**PROCEDURE**|  
|**ASSERZIONE**|**TROVATO**|**PUBLIC**|  
|**AT**|**FROM**|**READ**|  
|**AUTHORIZATION**|**FULL**|**REAL**|  
|**AVG**|**GET**|**RIFERIMENTI**|  
|**BEGIN**|**GLOBALE**|**RELATIVO**|  
|**BETWEEN**|**GO**|**RESTRICT**|  
|**BIT**|**GOTO**|**REVOKE**|  
|**BIT_LENGTH**|**GRANT**|**RIGHT**|  
|**ENTRAMBI**|**GRUPPO**|**ROLLBACK**|  
|**BY**|**CON**|**ROWS**|  
|**CASCADE**|**ORA**|**SCHEMA**|  
|**CASCADED**|**IDENTITÀ**|**SCORRIMENTO**|  
|**CASE**|**CONTROLLO IMMEDIATO**|**SECONDO**|  
|**CAST**|**IN**|**SEZIONE**|  
|**CATALOG**|**INCLUDE**|**SELECT**|  
|**CHAR**|**INDEX**|**SESSIONE**|  
|**CHAR_LENGTH**|**INDICATORE**|**SESSION_USER**|  
|**CARATTERE**|**INIZIALMENTE**|**SET**|  
|**CHARACTER_LENGTH**|**INTERNA**|**DIMENSIONI**|  
|**CHECK**|**INPUT**|**SMALLINT**|  
|**CLOSE**|**DISTINZIONE**|**ALCUNI**|  
|**COALESCE**|**INSERT**|**SPACE**|  
|**COLLATE**|**INT**|**SQL**|  
|**REGOLE DI CONFRONTO**|**VALORE INTEGER**|**SQLCA**|  
|**COLONNA**|**INTERSECT**|**SQLCODE**|  
|**COMMIT**|**INTERVALLO**|**SQLERROR**|  
|**CONNECT**|**IN**|**SQLSTATE**|  
|**CONNESSIONE**|**È**|**SQLWARNING**|  
|**CONSTRAINT**|**ISOLAMENTO**|**SUBSTRING**|  
|**VINCOLI**|**CREARE UN JOIN**|**SUM**|  
|**CONTINUE**|**KEY**|**SYSTEM_USER**|  
|**CONVERTI**|**LANGUAGE**|**TABLE**|  
|**CORRISPONDENTE**|**LAST**|**TEMPORANEO**|  
|**COUNT**|**INIZIALI**|**QUINDI**|  
|**CREARE**|**LEFT**|**ORA**|  
|**CROSS**|**LEVEL**|**TIMESTAMP**|  
|**CORRENTE**|**LIKE**|**TIMEZONE_HOUR**|  
|**CURRENT_DATE**|**LOCAL**|**TIMEZONE_MINUTE**|  
|**CURRENT_TIME**|**LOWER**|**TO**|  
|**CURRENT_TIMESTAMP**|**MATCH**|**FINALI**|  
|**CURRENT_USER**|**MAX**|**TRANSAZIONE**|  
|**CURSORE**|**MIN**|**TRANSLATE**|  
|**DATA**|**MINUTO**|**TRANSLATION**|  
|**DAY**|**MODULO**|**TRIM**|  
|**DEALLOCATE**|**MONTH**|**TRUE**|  
|**DEC**|**NOMI**|**UNIONE**|  
|**DECIMALE**|**NAZIONALE**|**UNIVOCO**|  
|**DICHIARARE**|**NATURALE**|**UNKNOWN**|  
|**DEFAULT**|**NCHAR**|**UPDATE**|  
|**PUÒ ESSERE RINVIATO**|**NEXT**|**UPPER**|  
|**POSTICIPATA**|**NO**|**USAGE**|  
|**DELETE**|**NONE**|**USER**|  
|**DESC**|**NOT**|**UTILIZZO**|  
|**DESCRIBE**|**NULL**|**VALUE**|  
|**DESCRITTORE**|**NULLIF**|**VALORI**|  
|**DIAGNOSTICA**|**NUMERIC**|**VARCHAR**|  
|**DISCONNECT**|**OCTET_LENGTH**|**VARIABILE**|  
|**DISTINCT**|**OF**|**VIEW**|  
|**DOMINIO**|**ON**|**QUANDO**|  
|**DOPPIA**|**ONLY**|**OGNI VOLTA CHE**|  
|**DROP**|**OPEN**|**WHERE**|  
|**ELSE**|**OPZIONE**|**WITH**|  
|**END**|**OPPURE**|**LAVORO**|  
|**END-EXEC**|**ORDINE**|**SCRITTURA**|  
|**ESCAPE**|**ESTERNO**|**YEAR**|  
|**EXCEPT**|**OUTPUT**|**ZONE**|  
|**ECCEZIONE**|||  
  
## <a name="future-keywords"></a>Parole chiave di versioni future  
 Nelle versioni future di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le parole chiave elencate di seguito potrebbero diventare riservate in seguito all'implementazione di nuove funzionalità. È consigliabile evitare l'utilizzo di queste parole come identificatori.  
  
||||  
|-|-|-|  
|ABSOLUTE|HOST|RELATIVE|  
|ACTION|HOUR|RELEASE|  
|ADMIN|IGNORE|RESULT|  
|AFTER|IMMEDIATE|RETURNS|  
|AGGREGATE|INDICATOR|ROLE|  
|ALIAS|INITIALIZE|ROLLUP|  
|ALLOCATE|INITIALLY|ROUTINE|  
|ARE|INOUT|ROW|  
|ARRAY|INPUT|ROWS|  
|ASENSITIVE|INT|SAVEPOINT|  
|ASSERTION|INTEGER|SCROLL|  
|ASYMMETRIC|INTERSECTION|SCOPE|  
|AT|INTERVAL|SEARCH|  
|ATOMIC|ISOLATION|SECOND|  
|BEFORE|ITERATE|SECTION|  
|BINARY|LANGUAGE|SENSITIVE|  
|BIT|LARGE|SEQUENCE|  
|BLOB|LAST|SESSION|  
|BOOLEAN|LATERAL|SETS|  
|BOTH|LEADING|SIMILAR|  
|BREADTH|LESS|SIZE|  
|CALL|LEVEL|SMALLINT|  
|CALLED|LIKE_REGEX|SPACE|  
|CARDINALITY|LIMIT|SPECIFIC|  
|CASCADED|LN|SPECIFICTYPE|  
|CAST|LOCAL|SQL|  
|CATALOG|LOCALTIME|SQLEXCEPTION|  
|CHAR|LOCALTIMESTAMP|SQLSTATE|  
|CHARACTER|LOCATOR|SQLWARNING|  
|CLASS|MAP|START|  
|CLOB|MATCH|STATE|  
|COLLATION|MEMBER|STATEMENT|  
|COLLECT|METHOD|STATIC|  
|COMPLETION|MINUTE|STDDEV_POP|  
|CONDITION|MOD|STDDEV_SAMP|  
|CONNECT|MODIFIES|STRUCTURE|  
|CONNECTION|MODIFY|SUBMULTISET|  
|CONSTRAINTS|MODULE|SUBSTRING_REGEX|  
|CONSTRUCTOR|MONTH|SYMMETRIC|  
|CORR|MULTISET|SYSTEM|  
|CORRESPONDING|NAMES|TEMPORARY|  
|COVAR_POP|NATURAL|TERMINATE|  
|COVAR_SAMP|NCHAR|THAN|  
|CUBE|NCLOB|TIME|  
|CUME_DIST|NEW|TIMESTAMP|  
|CURRENT_CATALOG|NEXT|TIMEZONE_HOUR|  
|CURRENT_DEFAULT_TRANSFORM_GROUP|No|TIMEZONE_MINUTE|  
|CURRENT_PATH|Nessuno|TRAILING|  
|CURRENT_ROLE|NORMALIZE|TRANSLATE_REGEX|  
|CURRENT_SCHEMA|NUMERIC|TRANSLATION|  
|CURRENT_TRANSFORM_GROUP_FOR_TYPE|OBJECT|TREAT|  
|CYCLE|OCCURRENCES_REGEX|TRUE|  
|DATA|OLD|UESCAPE|  
|DATE|ONLY|UNDER|  
|DAY|OPERATION|UNKNOWN|  
|DEC|ORDINALITY|UNNEST|  
|DECIMAL|OUT|USAGE|  
|DEFERRABLE|OVERLAY|USING|  
|DEFERRED|OUTPUT|VALUE|  
|DEPTH|PAD|VAR_POP|  
|DEREF|Parametro|VAR_SAMP|  
|DESCRIBE|PARAMETERS|VARCHAR|  
|DESCRIPTOR|PARTIAL|VARIABLE|  
|DESTROY|PARTITION|WHENEVER|  
|DESTRUCTOR|PATH|WIDTH_BUCKET|  
|DETERMINISTIC|POSTFIX|WITHOUT|  
|DICTIONARY|PREFIX|WINDOW|  
|DIAGNOSTICS|PREORDER|WITHIN|  
|DISCONNECT|PREPARE|WORK|  
|DOMAIN|PERCENT_RANK|WRITE|  
|DYNAMIC|PERCENTILE_CONT|XMLAGG|  
|EACH|PERCENTILE_DISC|XMLATTRIBUTES|  
|ELEMENT|POSITION_REGEX|XMLBINARY|  
|END-EXEC|PRESERVE|XMLCAST|  
|EQUALS|PRIOR|XMLCOMMENT|  
|EVERY|PRIVILEGES|XMLCONCAT|  
|EXCEPTION|RANGE|XMLDOCUMENT|  
|FALSE|READS|XMLELEMENT|  
|FILTER|REAL|XMLEXISTS|  
|FIRST|RECURSIVE|XMLFOREST|  
|FLOAT|REF|XMLITERATE|  
|FOUND|REFERENCING|XMLNAMESPACES|  
|FREE|REGR_AVGX|XMLPARSE|  
|FULLTEXTTABLE|REGR_AVGY|XMLPI|  
|FUSION|REGR_COUNT|XMLQUERY|  
|GENERAL|REGR_INTERCEPT|XMLSERIALIZE|  
|GET|REGR_R2|XMLTABLE|  
|GLOBAL|REGR_SLOPE|XMLTEXT|  
|GO|REGR_SXX|XMLVALIDATE|  
|GROUPING|REGR_SXY|YEAR|  
|HOLD|REGR_SYY|ZONE|  
  
## <a name="see-also"></a>Vedere anche  
 [SET QUOTED_IDENTIFIER &#40; Transact-SQL &#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)   
 [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  
