---
title: SQLGetTypeInfo | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
caps.latest.revision: 47
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e83a45cad86f882bfcb1c7cbb15f32736d694d55
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166381"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] report dei driver ODBC di Native Client imposta la colonna aggiuntiva USERTYPE nel risultato di `SQLGetTypeInfo`. USERTYPE riporta la definizione del tipo di dati DB-Library e risulta utile agli sviluppatori che trasferiscono applicazioni DB-Library esistenti a ODBC.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tratta l'identità come attributo, mentre ODBC la tratta come tipo di dati. Per risolvere questa mancata corrispondenza, `SQLGetTypeInfo` restituisce i tipi di dati: **intidentity**, **smallintidentity**, **tinyintidentity**, **decimalidentity** , e **numericidentity**. Il `SQLGetTypeInfo` colonna AUTO_UNIQUE_VALUE del set di risultati indica il valore TRUE per questi tipi di dati.  
  
 Per **varchar**, **nvarchar** e **varbinary**la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client continua a segnalare 8000, 4000 e 8000 rispettivamente per il valore di COLUMN_SIZE il valore, anche se è illimitato. Ciò consente di assicurare la compatibilità con le versioni precedenti.  
  
 Per il **xml** tipo di dati, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client riporta SQL_SS_LENGTH_UNLIMITED per COLUMN_SIZE indicare dimensioni illimitate.  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo e parametri con valori di tabella  
 Il tipo di tabella per i parametri con valori di tabella è sostanzialmente un metatipo, ovvero un tipo utilizzato per definire altri tipi. Pertanto, non dispone di essere esposti mediante SQLGetTypeInfo. Le applicazioni devono utilizzare SQLTables, anziché SQLGetTypeInfo, per recuperare i metadati per i tipi di tabella utilizzati con i parametri con valori di tabella.  
  
 Per ulteriori informazioni sul recupero di metadati per i parametri con valori di tabella, vedere [gli attributi delle istruzioni che per i parametri Affect Table-Valued](../native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md).  
  
 Per ulteriori informazioni sui parametri con valori di tabella, vedere [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>Supporto di SQLGetTypeInfo per le caratteristiche avanzate di data e ora  
 Per i valori restituiti per i tipi di data/ora, vedere [metadati del catalogo](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Per informazioni generali, vedere [data e ora miglioramenti &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>Supporto SQLGetTypeInfo per i tipi CLR definiti dall'utente di grandi dimensioni  
 `SQLGetTypeInfo` supporta i tipi CLR definiti dall'utente di grandi dimensioni. Per altre informazioni, vedere [Large CLR User-Defined tipi &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLGetTypeInfo](http://go.microsoft.com/fwlink/?LinkId=59356)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  