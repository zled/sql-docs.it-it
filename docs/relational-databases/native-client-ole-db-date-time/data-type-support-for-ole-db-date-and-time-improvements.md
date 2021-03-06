---
title: Supporto dei tipi di dati per i miglioramenti relativi a data e ora OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB], data type support
- OLE DB, date/time improvements
ms.assetid: d40e3fd6-9057-4371-8236-95cef300603e
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5cce6109766d6eddff563287fa6a36adf187146d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47595899"
---
# <a name="data-type-support-for-ole-db-date-and-time-improvements"></a>Supporto dei tipi di dati per i miglioramenti relativi a data e ora OLE DB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  In questo argomento vengono fornite informazioni sui tipi OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) che supportano i tipi di dati di data/ora di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="data-type-mapping-in-rowsets-and-parameters"></a>Mapping dei tipi di dati in set di righe e parametri  
 OLE DB fornisce due nuovi tipi di dati per supportare i nuovi tipi di server: DBTYPE_DBTIME2 e DBTYPE_DBTIMESTAMPOFFSET. Nella tabella seguente viene illustrato il mapping completo per il tipo di server:  
  
|Tipo di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Tipo di dati OLE DB|valore|  
|-----------------------------------------|----------------------|-----------|  
|DATETIME|DBTYPE_DBTIMESTAMP|135 (oledb.h)|  
|smalldatetime|DBTYPE_DBTIMESTAMP|135 (oledb.h)|  
|Data|DBTYPE_DBDATE|133 (oledb.h)|  
|time|DBTYPE_DBTIME2|145 (sqlncli.h)|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|146 (sqlncli.h)|  
|datetime2|DBTYPE_DBTIMESTAMP|135 (oledb.h)|  
  
## <a name="data-formats-strings-and-literals"></a>Formati di dati: stringhe e valori letterali  
  
|Tipo di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Tipo di dati OLE DB|Formato stringa per le conversioni client|  
|-----------------------------------------|----------------------|------------------------------------------|  
|DATETIME|DBTYPE_DBTIMESTAMP|'yyyy-mm-dd hh:mm:ss[.999]'<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta fino a tre cifre per i secondi frazionari per datetime.|  
|smalldatetime|DBTYPE_DBTIMESTAMP|'yyyy-mm-dd hh:mm:ss'<br /><br /> Questo tipo di dati ha un'accuratezza di un minuto. Il componente dei secondi sarà zero nell'output mentre verrà arrotondato dal server nell'input.|  
|Data|DBTYPE_DBDATE|'yyyy-mm-dd'|  
|time|DBTYPE_DBTIME2|'hh:mm:ss[.9999999]'<br /><br /> I secondi frazionari possono essere specificati facoltativamente utilizzando fino a sette cifre.|  
|datetime2|DBTYPE_DBTIMESTAMP|'yyyy-mm-dd hh:mm:ss[.fffffff]'<br /><br /> I secondi frazionari possono essere specificati facoltativamente utilizzando fino a sette cifre.|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|'yyyy-mm-dd hh:mm:ss[.fffffff] +/-hh:mm'<br /><br /> I secondi frazionari possono essere specificati facoltativamente utilizzando fino a sette cifre.|  
  
 Non vi sono modifiche nelle sequenze di escape per i valori letterali di data/ora.  
  
 Per i secondi frazionari nei risultati viene utilizzato un punto (.) anziché i due punti (:).  
  
 I valori stringa restituiti alle applicazioni sono sempre della stessa lunghezza per una colonna specifica. Nei componenti per anno, mese, giorno, ora, minuti e secondi vengono aggiunti con zero iniziali per raggiungere la larghezza massima. Sarà presente esattamente uno spazio tra la data e l'ora ed esattamente uno spazio tra l'ora e la differenza di fuso orario. Una differenza di fuso orario sarà sempre preceduta da un segno. Il segno sarà un più (+) quando la differenza è zero. Non verrà aggiunto alcuno spazio vuoto tra il segno e il valore di differenza. Se necessario, nei secondi frazionari verranno aggiunti zero finali fino a raggiungere la precisione definita per la colonna, ma non oltre. Per le colonne di tipo datetime, verranno utilizzate tre cifre per i secondi frazionari. Per le colonne di tipo smalldatetime, non vi saranno cifre per i secondi frazionari e i secondi saranno sempre zero.  
  
 Le conversioni dai valori stringa forniti dall'applicazione saranno più flessibili e consentiranno la presenza di valori di componente minori della larghezza massima. Gli anni possono essere costituiti da una a quattro cifre. I mesi, i giorni, le ore, i minuti e i secondi possono essere costituiti da una o due cifre. Può essere presente uno spazio vuoto arbitrario tra le differenze data/ora e ora/fuso orario. Il segno utilizzato per una differenza con zero ore e zero minuti può essere un più o un meno. Gli zeri finali sono consentiti per i secondi frazionari fino a un massimo di 9 cifre. Un componente per le ore può terminare con un separatore decimale e senza cifre per i secondi frazionari.  
  
 Una stringa vuota non è un valore letterale di data/ora valido e non rappresenta un valore NULL. Un tentativo di convertire una stringa vuota in un valore di data/ora genererà errori con SQLState 22018 e il messaggio "Carattere non valido per la specifica del cast".  
  
## <a name="data-formats-data-structures"></a>Formati di dati: strutture di dati  
 Nelle strutture specifiche di OLE DB descritte di seguito a OLE DB si applicano gli stessi vincoli di ODBC. Tali vincoli dipendono dal calendario gregoriano:  
  
-   L'intervallo per i mesi è compreso tra 1 e 12.  
  
-   L'intervallo per il campo del giorno è compreso tra 1 e il numero di giorni nel mese e deve essere coerente con i campi dell'anno e del mese, considerando gli anni bisestili.  
  
-   L'intervallo delle ore è compreso tra 0 e 23.  
  
-   L'intervallo dei minuti è compreso tra 0 e 59.  
  
-   L'intervallo dei secondi è compreso tra 0 e 59, consentendo fino a due secondi di compensazione per mantenere la sincronizzazione con l'ora siderale.  
  
 Sono state modificate le implementazioni per le strutture OLE esistenti seguenti in modo da supportare i nuovi tipi di data e ora di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le definizioni, tuttavia, non sono state modificate.  
  
-   DBTYPE_DATE. Si tratta di un tipo DATE di automazione. Viene rappresentato internamente come **double**. La parte intera corrisponde al numero di giorni a partire dal 30 dicembre 1899, mentre la parte frazionaria rappresenta una frazione del giorno. Poiché questo tipo ha un'accuratezza di 1 secondo, dispone di una scala effettiva pari a 0.  
  
-   DBTYPE_DBDATE  
  
-   DBTYPE_DBTIME  
  
-   DBTYPE_DBTIMESTAMP. Il campo della frazione è definito da OLE DB come numero di miliardesimi di secondo (nanosecondi) ed è incluso nell'intervallo compreso tra 0 e 999.999.999.  
  
-   DBTYPE_FILETIME  
  
### <a name="dbtypedbtime2"></a>DBTYPE_DBTIME2  
 In questa struttura è possibile aggiungere fino a 12 byte nei sistemi operativi a 32 bit e a 64 bit.  
  
```  
typedef struct tagDBTIME2 {  
    USHORT hour;  
    USHORT minute;  
    USHORT second;  
    ULONG fraction;  
    } DBTIME2;  
```  
  
### <a name="dbtype-dbtimestampoffset"></a>DBTYPE_DBTIMESTAMPOFFSET  
  
```  
typedef struct tagDBTIMESTAMPOFFSET {  
    SHORT year;  
    USHORT month;  
    USHORT day;  
    USHORT hour;  
    USHORT minute;  
    USHORT second;  
    ULONG fraction;  
    SHORT timezone_hour;  
    SHORT timezone_minute;  
    } DBTIMESTAMPOFFSET;  
```  
  
 Se `timezone_hour` è negativo, `timezone_minute` deve essere negativo o uguale a zero. Se `timezone_hour` è positivo, `timezone minute` deve essere positivo o uguale a zero. Se `timezone_hour` è zero, `timezone minute` può contenere un valore compreso tra -59 e +59.  
  
### <a name="ssvariant"></a>SSVARIANT  
 Questa struttura include ora le nuove strutture DBTYPE_DBTIME2 e DBTYPE_DBTIMESTAMPOFFSET e viene aggiunta una scala di frazioni di secondo per i tipi appropriati.  
  
```  
struct SSVARIANT {  
   SSVARTYPE vt;  
   DWORD dwReserved1;  
   DWORD dwReserved2;  
   union {  
// ...  
      DBTIMESTAMP tsDateTimeVal;  
      DBDATE dDateVal;  
      struct _Time2Val {  
         DBTIME2 tTime2Val;  
         BYTE bScale;  
      } Time2Val;  
      struct _DateTimeVal {  
         DBTIMESTAMP tsDateTimeVal;  
         BYTE bScale;  
      } DateTimeVal;  
      struct _DateTimeOffsetVal {   
         DBTIMESTAMPOFFSET tsoDateTimeOffsetVal;  
         BYTE bScale;  
      } DateTimeOffsetVal;  
// ...  
   };  
};  
```  
  
 L'enumerazione associata alla codifica dei tipi SSVARIANT che determina il tipo dell'enumerazione, inoltre, verrà estesa nel modo seguente:  
  
```  
enum SQLVARENUM {  
// ...  
   // Datetime  
   VT_SS_DATETIME      = DBTYPE_DBTIMESTAMP,  
   VT_SS_SMALLDATETIME = 206,  
  
   VT_SS_DATE = DBTYPE_DBDATE,  
   VT_SS_TIME2 = DBTYPE_DBTIME2,  
   VT_SS_DATETIME2 = 212  
   VT_SS_DATETIMEOFFSET = DBTYPE_DBTIMESTAMPOFFSET  
};  
```  
  
 Eseguire la migrazione di applicazioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client che usano **sql_variant** e si basano sulla precisione limitata di **datetime** dovranno essere aggiornate se lo schema sottostante è aggiornato per usare **datetime2** invece **datetime**.  
  
 Le macro di accesso per SSVARIANT sono state estese anche con l'aggiunta degli elementi seguenti:  
  
```  
#define V_SS_DATETIME2(X)       V_SS_UNION(X, DateTimeVal)  
#define V_SS_TIME2(X)           V_SS_UNION(X, Time2Val)  
#define V_SS_DATE(X)            V_SS_UNION(X, dDateVal)  
#define V_SS_DATETIMEOFFSET(X)  V_SS_UNION(X, DateTimeOffsetVal)  
```  
  
## <a name="data-type-mapping-in-itabledefinitioncreatetable"></a>Mapping dei tipi di dati in ITableDefinition::CreateTable  
 Con strutture DBCOLUMNDESC utilizzate da itabledefinition:: CreateTable viene usato il mapping dei tipi seguenti:  
  
|Tipo di dati OLE DB (*wType*)|Tipo di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Note|  
|----------------------------------|-----------------------------------------|-----------|  
|DBTYPE_DBDATE|Data||  
|DBTYPE_DBTIMESTAMP|**datetime2**(p)|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client controlla il DBCOLUMDESC *bScale* membro per determinare la precisione frazionaria dei secondi.|  
|DBTYPE_DBTIME2|**time**(p)|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client controlla il DBCOLUMDESC *bScale* membro per determinare la precisione frazionaria dei secondi.|  
|DBTYPE_DBTIMESTAMPOFFSET|**datetimeoffset**(p)|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client controlla il DBCOLUMDESC *bScale* membro per determinare la precisione frazionaria dei secondi.|  
  
 Quando un'applicazione specifica DBTYPE_DBTIMESTAMP in *wType*, è possibile eseguire l'override del mapping al **datetime2** specificando un nome di tipo nella *pwszTypeName*. Se **data/ora** omette *bScale* deve essere 3. Se **smalldatetime** omette *bScale* deve essere 0. Se *bScale* non è coerente con *wType* e *pwszTypeName*, viene restituito DB_E_BADSCALE.  
  
## <a name="see-also"></a>Vedere anche  
 [Miglioramenti relativi a data e ora &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
