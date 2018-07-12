---
title: Data e ora miglioramenti (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 034c0957d4214b24fd9903b7b5ebb4e4a700bb4e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413421"
---
# <a name="date-and-time-improvements-odbc"></a>Data e ora miglioramenti (ODBC)
  In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] sono stati introdotti nuovi tipi di dati di data e ora. Questa sezione viene descritto come questi nuovi tipi vengono esposti come estensioni in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Per una panoramica delle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporto di Native Client per i nuovi tipi data e ora dei dati, vedere [data e ora miglioramenti](../native-client/features/date-and-time-improvements.md). Per un esempio che illustra il supporto per data/ora ODBC, vedere [Usa tipi di data e ora](../native-client-odbc-how-to/use-date-and-time-types.md).  
  
 Per informazioni più generali sui tipi di dati di data e ora, vedere [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Supporto dei tipi di dati per i miglioramenti relativi a data e ora ODBC](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 Vengono fornite informazioni sui tipi ODBC che supportano i tipi di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di data e ora.  
  
 [Metadati &#40;ODBC&#41;](../../database-engine/dev-guide/metadata-odbc.md)  
 Vengono descritte le informazioni restituite nei campi di descrizione del parametro di implementazione (IPD, Implementation Parameter Descriptor) e di descrizione della riga di implementazione (IRD, Implementation Row Descriptor) nonché i metadati della colonna restituiti da `SQLColumns` e `SQLProcedureColumns`. Vengono inoltre descritti i metadati del tipo di dati restituiti da `SQLGetTypeInfo`.  
  
 [Conversioni di tipo di dati DateTime &#40;ODBC&#41;](datetime-data-type-conversions-odbc.md)  
 Viene descritto come eseguire la conversione tra i valori datetime e datetimeoffset.  
  
 [Supporto sql_variant per i tipi di data e ora](sql-variant-support-for-date-and-time-types.md)  
 Viene descritto il supporto della funzione SQL_VARIANT per la funzionalità avanzata di data e ora.  
  
 [Modifiche apportate alla copia di massa per i tipi avanzati di data e ora &#40;OLE DB e ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Vengono descritti i miglioramenti apportati ai tipi di data/ora per supportare le operazioni di copia bulk.  
  
 [Comportamento con versioni precedenti di SQL Server il tipo avanzate di data e ora &#40;ODBC&#41;](enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 Viene descritto il comportamento previsto quando un'applicazione client che utilizza le caratteristiche avanzate di data e ora comunica con una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e quando un client compilato con una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client invia comandi a un server che supporta le caratteristiche avanzate di data e ora.  
  
 [Supporto delle API ODBC per le funzionalità avanzate di data e ora](odbc-api-support-for-enhanced-date-and-time-features.md)  
 Vengono elencate le funzioni ODBC che supportano la funzionalità avanzata di data e ora.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
