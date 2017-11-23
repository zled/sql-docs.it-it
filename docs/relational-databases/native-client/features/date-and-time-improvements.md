---
title: Data e ora miglioramenti | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|features
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9b1d0d9d-1f6e-4399-8f61-e23f9a486a7a
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 843ce549dbd36f8fcbde8c61ade8cee2bc7163ca
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="date-and-time-improvements"></a>Data e ora miglioramenti
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  In questo argomento viene descritto il supporto [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client per i tipi di dati di data e ora aggiunti in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  
 Per ulteriori informazioni sui miglioramenti di data/ora, vedere [OLE DB data e ora miglioramenti &#40; &#41;](../../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md) e [data e ora miglioramenti &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
 Per informazioni sulle applicazioni di esempio che illustrano questa funzionalità, vedere [esempi di programmazione dati di SQL Server](http://msftdpprodsamples.codeplex.com/).  
  
## <a name="usage"></a>Utilizzo  
 Nelle sezioni seguenti vengono descritte le diverse modalità di utilizzo dei nuovi tipi di data e ora.  
  
### <a name="use-date-as-a-distinct-data-type"></a>Utilizzare il tipo date come tipo di dati distinto  
 A partire da [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], il supporto migliorato per i tipi di data/ora consente un utilizzo più efficiente del tipo SQL_TYPE_DATE ODBC (SQL_DATE per le applicazioni ODBC 2.0) e del tipo DBTYPE_DBDATE OLE DB.  
  
### <a name="use-time-as-a-distinct-data-type"></a>Utilizzare il tipo time come tipo di dati distinto  
 OLE DB include già un tipo di dati che contiene solo l'ora, ovvero DBTYPE_DBTIME, che garantisce precisione pari a 1 secondo. Il tipo equivalente in ODBC è SQL_TYPE_TIME (SQL_TIME per le applicazioni ODBC 2.0).  
  
 Il nuovo [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ora il tipo di dati ha frazionaria dei secondi precisione di 100 nanosecondi. Questa operazione richiede nuovi tipi in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client: DBTYPE_DBTIME2 (OLE DB) e SQL_SS_TIME2 (ODBC). Le applicazioni esistenti scritte per utilizzare le ore senza secondi frazionari possono utilizzare colonne time(0). I tipi OLE DB DBTYPE_TIME e ODBC SQL_TYPE_TIME esistenti e le strutture corrispondenti funzioneranno correttamente, a meno che le applicazioni non si basino sul tipo restituito nei metadati.  
  
### <a name="use-time-as-a-distinct-data-type-with-extended-fractional-seconds-precision"></a>Utilizzare il tipo time come tipo di dati distinto con precisione frazionaria dei secondi estesa  
 Alcune applicazioni, ad esempio le applicazioni di controllo dei processi e di produzione, richiedono la possibilità di gestire i dati di tipo time con una precisione pari a fino 100 nanosecondi. I nuovi tipi a tale scopo sono DBTYPE_DBTIME2 (OLE DB) e SQL_SS_TIME2 (ODBC).  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision"></a>Utilizzare il tipo datetime con precisione frazionaria dei secondi estesa  
 OLE DB definisce già un tipo con una precisione pari fino a 1 nanosecondo. Questo tipo, tuttavia, è già utilizzato dalle applicazioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] esistenti, che garantiscono una probabile precisione pari solo a 1/300 di secondo. Il nuovo **datetime2(3)** tipo non è direttamente compatibile con il tipo datetime esistente. Se vi è un rischio che tale tipo di dati influisca negativamente sul comportamento dell'applicazione, le applicazioni devono utilizzare un nuovo flag DBCOLUMN per determinare il tipo di server effettivo.  
  
 Anche ODBC definisce già un tipo con una precisione pari fino a 1 nanosecondo. Questo tipo, tuttavia, è già utilizzato dalle applicazioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] esistenti, che garantiscono una probabile precisione pari solo a 3 millisecondi. Il nuovo **datetime2(3)** tipo non è direttamente compatibile con esistente **datetime** tipo. **datetime2(3)** ha una precisione di un millisecondo e **datetime** ha una precisione di 1/300 di secondo. In ODBC le applicazioni possono determinare il tipo di server in uso tramite il campo di descrizione SQL_DESC_TYPE_NAME. Il tipo SQL_TYPE_TIMESTAMP (SQL_TIMESTAMP per le applicazioni ODBC 2.0) esistente può essere utilizzato per entrambi i tipi.  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision-and-timezone"></a>Utilizzare il tipo datetime con precisione frazionaria dei secondi estesa e fuso orario  
 Alcune applicazioni richiedono valori datetime con informazioni sul fuso orario. Questo requisito è supportato dai nuovi tipi DBTYPE_DBTIMESTAMPOFFSET (OLE DB) e SQL_SS_TIMESTAMPOFFSET (ODBC).  
  
### <a name="use-datetimedatetimedatetimeoffset-data-with-client-side-conversions-consistent-with-existing-conversions"></a>Utilizzare dati di tipo date/time/datetime/datetimeoffset con conversioni sul lato client coerenti con le conversioni esistenti  
 Lo standard ODBC descrive il funzionamento delle conversioni tra tipi di data, ora e timestamp. Tali tipi sono estesi in modo coerente per includere conversioni tra tutti i tipi di data e ora introdotti in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità di SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
