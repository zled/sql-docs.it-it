---
title: Metadati per parametri e set di righe | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-date-time
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: metadata [OLE DB]
ms.assetid: 31b318a4-20e7-4db0-b367-eb9938859029
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d45c0eafa873e0697c791d478eeffada7cfd91a0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="metadata---parameter-and-rowset"></a>Metadati - parametro e i set di righe
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  In questo argomento vengono fornite informazioni sul tipo e sui membri di tipo seguenti, relativi ai miglioramenti apportati alle funzionalità di data e ora OLE DB.  
  
-   Struttura DBBINDING  
  
-   **ICommandWithParameters:: GetParameterInfo**  
  
-   **ICommandWithParameters:: SetParameterInfo**  
  
-   **IColumnsRowset::**  
  
-   **IColumnsInfo:: GetColumnInfo**  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 Le seguenti informazioni vengono restituite nella struttura DBPARAMINFO tramite *prgParamInfo*:  
  
|Tipo di parametro|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|-------------------|------------------|--------------|-----------------------------------------------------|  
|data|DBTYPE_DBDATE|6|10|0|Clear|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Impostare|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Clear|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Clear|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19,21..27|0..7|Impostare|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26,28..34|0..7|Impostare|  
  
 Tenere presente che in alcuni casi gli intervalli di valori non sono continui Ciò è dovuto all'aggiunta di un separatore decimale quando la precisione frazionaria è maggiore di zero.  
  
 DBPARAMFLAGS_SS_ISVARIABLESCALE è valido solo se connesso a un [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (o versione successiva) server. DBPARAMFLAGS_SS_ISVARIABLESCALE non viene mai impostata quando si è connessi al server di livello inferiore.  
  
## <a name="icommandwithparameterssetparameterinfo-and-implied-parameter-types"></a>ICommandWithParameters::SetParameterInfo e tipi di parametri impliciti  
 Le informazioni specificate nella struttura DBPARAMBINDINFO devono essere conformi agli elementi seguenti:  
  
|*pwszDataSourceType*<br /><br /> (specifico del provider)|*pwszDataSourceType*<br /><br /> (generico di OLE DB)|*ulParamSize*|*bScale*|  
|----------------------------------------------------|-------------------------------------------------|-------------------|--------------|  
||DBTYPE_DATE|6|Ignorato|  
|data|DBTYPE_DBDATE|6|Ignorato|  
||DBTYPE_DBTIME|10|Ignorato|  
|time|DBTYPE_DBTIME2|10|0..7|  
|smalldatetime||16|Ignorato|  
|datetime||16|Ignorato|  
|datetime2 o DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|16|0..7|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|0..7|  
  
 Il *bPrecision* parametro viene ignorato.  
  
 "DBPARAMFLAGS_SS_ISVARIABLESCALE" viene ignorato in caso di invio di dati al server. Le applicazioni possono forzare l'utilizzo di tipi legacy flusso di dati tabulare (TDS) utilizzando i nomi di tipo specifico del provider "**datetime**"e"**smalldatetime**". Quando si è connessi a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (o versione successiva) Server, "**datetime2**"verrà utilizzato il formato e una conversione server implicita si verifica, se necessario, quando il nome di tipo"**datetime2**" o "DbType DBTIMESTAMP". *bScale* viene ignorata se i nomi di tipo specifico del provider "**datetime**"o"**smalldatetime**" vengono utilizzati. In caso contrario, è necessario assicurarsi che *bScale* sia impostata correttamente. Applicazioni aggiornate da MDAC e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] che utilizzano "DBTYPE_DBTIMESTAMP" avrà esito negativo se non viene impostato *bScale* correttamente. Quando si è connessi a istanze server precedenti a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], *bScale* valore diverso da 0 o 3 con "DBTYPE_DBTIMESTAMP" è un errore e verrà restituito E_FAIL.  
  
 Quando non viene chiamato ICommandWithParameters:: SetParameterInfo, il provider Ricava il server di tipo dal tipo di associazione come specificato in IAccessor:: CreateAccessor come indicato di seguito:  
  
|Tipo di associazione|*pwszDataSourceType*<br /><br /> (specifico del provider)|  
|------------------|----------------------------------------------------|  
|DBTYPE_DATE|datetime2(0)|  
|DBTYPE_DBDATE|data|  
|DBTYPE_DBTIME|time(0)|  
|DBTYPE_DBTIME2|time(7)|  
|DBTYPE_DBTIMESTAMP|datetime2(7)|  
|DBTYPE_DBTIMESTAMPOFFSET|datetimeoffset(7)|  
  
## <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 **IColumnsRowset::** restituisce le colonne seguenti:  
  
|Tipo di colonna|DBCOLUMN_TYPE|DBCOLUM_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE, DBCOLUMN_DATETIMEPRECISION|DBCOLUMN_FLAGS, DBCOLUMNFLAGS_SS_ISVARIABLESCALE|  
|-----------------|--------------------|-------------------------|-------------------------|--------------------------------------------------|---------------------------------------------------------|  
|data|DBTYPE_DBDATE|6|10|0|Clear|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Impostare|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Clear|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Clear|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Impostare|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Impostare|  
  
 In DBCOLUMN_FLAGS il valore di DBCOLUMNFLAGS_ISFIXEDLENGTH è sempre true per i tipi date/time e il valore dei flag seguenti è sempre false:  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER  
  
-   DBCOLUMNFLAGS_MAYDEFER  
  
 I flag restanti (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE e DBCOLUMNFLAGS_WRITEUNKNOWN) possono essere impostati in base alla modalità di definizione della colonna e alla query effettiva.  
  
 In DBCOLUMN_FLAGS è disponibile un nuovo flag DBCOLUMNFLAGS_SS_ISVARIABLESCALE che consente di determinare il tipo di server delle colonne nelle applicazioni, dove DBCOLUMN_TYPE è DBTYPE_DBTIMESTAMP. Per identificare il tipo di server è necessario utilizzare anche DBCOLUMN_SCALE o DBCOLUMN_DATETIMEPRECISION.  
  
 DBCOLUMNFLAGS_SS_ISVARIABLESCALE è valido solo se connesso a un [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (o versione successiva) server. DBCOLUMNFLAGS_SS_ISVARIABLESCALE non è definito quando si è connessi a server legacy.  
  
## <a name="icolumnsinfogetcolumninfo"></a>IColumnsInfo::GetColumnInfo  
 La struttura DBCOLUMNINFO restituisce le informazioni seguenti:  
  
|Tipo di parametro|*wType*|*ulColumnSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|--------------------|------------------|--------------|-----------------------------------------------------|  
|data|DBTYPE_DBDATE|6|10|0|Clear|  
|time(1..7)|DBTYPE_DBTIME2|10|8, 10..16|0..7|Impostare|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Clear|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Clear|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Impostare|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Impostare|  
  
 In *dwFlags*, DBCOLUMNFLAGS_ISFIXEDLENGTH è sempre true per tipi di data/ora e i flag seguenti sono sempre false:  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER, MAYDEFER  
  
 I flag restanti (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE e DBCOLUMNFLAGS_WRITEUNKNOWN) possono essere impostati.  
  
 Un nuovo flag DBCOLUMNFLAGS_SS_ISVARIABLESCALE viene fornito in *dwFlags* per consentire a un'applicazione determinare il tipo di server delle colonne, in cui *wType* è DBTYPE_DBTIMESTAMP. *bScale* deve inoltre essere utilizzato per identificare il tipo di server.  
  
## <a name="see-also"></a>Vedere anche  
 [I metadati &#40; OLE DB &#41;](http://msdn.microsoft.com/library/605e3be5-aeea-4573-9847-b866ed3c8bff)  
  
  
