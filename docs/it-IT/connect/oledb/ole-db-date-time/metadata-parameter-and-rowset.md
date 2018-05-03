---
title: Metadati per parametri e set di righe | Documenti Microsoft
description: Metadati di parametro e set di righe
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- metadata [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 96960a9f74a872327512dac5dce43ea3db68d69a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="metadata---parameter-and-rowset"></a>Metadati - parametro e i set di righe
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Questo articolo fornisce informazioni sul tipo seguente e i membri dei tipi, correlati alle funzionalità avanzate di data e ora OLE DB.  
  
-   Struttura DBBINDING  
  
-   **ICommandWithParameters::GetParameterInfo**  
  
-   **ICommandWithParameters::SetParameterInfo**  
  
-   **IColumnsRowset::GetColumnsRowset**  
  
-   **IColumnsInfo::GetColumnInfo**  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 Le seguenti informazioni vengono restituite nella struttura DBPARAMINFO tramite *prgParamInfo*:  
  
|Tipo di parametro|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|-------------------|------------------|--------------|-----------------------------------------------------|  
|data|DBTYPE_DBDATE|6|10|0|Clear|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Impostare|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Clear|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Clear|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Impostare|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Impostare|  
  
 Tenere presente che in alcuni casi gli intervalli di valori non sono continui Ciò è dovuto all'aggiunta di un separatore decimale quando la precisione frazionaria è maggiore di zero.  
  
 DBPARAMFLAGS_SS_ISVARIABLESCALE è valido solo se connesso a un [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (o versione successiva) server. DBPARAMFLAGS_SS_ISVARIABLESCALE non viene mai impostata quando si è connessi al server di livello inferiore.  
  
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
  
 "DBPARAMFLAGS_SS_ISVARIABLESCALE" viene ignorato in caso di invio di dati al server. Le applicazioni possono forzare l'utilizzo di tipi legacy flusso di dati tabulare (TDS) utilizzando i nomi di tipo specifico del provider "**datetime**"e"**smalldatetime**". Quando si è connessi a [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (o versione successiva) Server, "**datetime2**"verrà utilizzato il formato e una conversione server implicita si verifica, se necessario, quando il nome di tipo"**datetime2**" o "DbType DBTIMESTAMP". *bScale* viene ignorata se i nomi di tipo specifico del provider "**datetime**"o"**smalldatetime**" vengono utilizzati. In caso contrario, è necessario assicurarsi che le applicazioni *bScale* sia impostata correttamente. Applicazioni aggiornate da MDAC e Driver OLE DB per SQL Server da [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] che utilizzano "DBTYPE_DBTIMESTAMP" avrà esito negativo se non viene impostato *bScale* correttamente. Quando si è connessi a istanze server precedenti a [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], *bScale* valore diverso da 0 o 3 con "DBTYPE_DBTIMESTAMP" è un errore e verrà restituito E_FAIL.  
  
 Quando non viene chiamato ICommandWithParameters:: SetParameterInfo, il provider implica il tipo di server dal tipo di associazione come specificato in IAccessor:: CreateAccessor come indicato di seguito:  
  
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
  
 DBCOLUMNFLAGS_SS_ISVARIABLESCALE è valido solo se connesso a un [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (o versione successiva) server. DBCOLUMNFLAGS_SS_ISVARIABLESCALE non è definito quando si è connessi a server legacy.  
  
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
 [Supporto dei tipi di dati per i miglioramenti relativi a data e ora OLE DB](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
  
  
