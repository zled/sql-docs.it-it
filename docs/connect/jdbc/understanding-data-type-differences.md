---
title: Dati di informazioni sulle differenze tra i tipi | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab8fa00f-cb16-47e2-94b8-3a76f56c2b84
caps.latest.revision: "33"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f9f24abd0bf39ebe61cf3715371c6c6c3d6f5663
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="understanding-data-type-differences"></a>Informazioni sulle differenze tra i tipi di dati
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Esistono alcune differenze tra i tipi di dati Java linguaggio di programmazione e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di dati. Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] consente di superare tali differenze tramite diversi tipi di conversioni.  
  
## <a name="character-types"></a>Tipi di caratteri  
 I tipi di dati stringa di caratteri JDBC sono **CHAR**, **VARCHAR**, e **LONGVARCHAR**. Il driver JDBC fornisce supporto per l'API di JDBC 4.0. In JDBC 4.0, i tipi di dati stringa di caratteri JDBC possono anche essere **NCHAR**, **NVARCHAR**, e **LONGNVARCHAR**. Questi nuovi tipi di stringhe di caratteri mantengono i tipi di caratteri nativi di Java in formato Unicode pertanto non richiedono più conversioni da ANSI a Unicode o viceversa.  
  
|Tipo|Description|  
|----------|-----------------|  
|A lunghezza fissa|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **char** e **nchar** tipi di dati sono mappati direttamente a Microsoft JDBC **CHAR** e **NCHAR** tipi. Si tratta di tipi a lunghezza fissa con spaziatura messi a disposizione dal server nel caso in cui la colonna presenti SET ANSI_PADDING ON. Riempimento è sempre attivato per **nchar**, ma per **char**, nel caso in cui le colonne char del server non sono possono essere riempite, il driver JDBC viene aggiunto il riempimento.|  
|A lunghezza variabile|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **varchar** e **nvarchar** tipi mappati direttamente a Microsoft JDBC **VARCHAR** e **NVARCHAR** tipi, rispettivamente.|  
|Long|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **testo** e **ntext** mapping tra tipi di JDBC **LONGVARCHAR** e **LONGNVARCHAR** digitare, rispettivamente. Si tratta di tipi deprecati a partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)], è necessario utilizzare i tipi di valori di grandi dimensioni, **varchar (max)** o **nvarchar (max)**, anziché.<br /><br /> Tramite l'aggiornamento\<tipo numerico > e [updateObject (int, lang)](../../connect/jdbc/reference/updateobject-method-int-java-lang-object.md) metodi avranno esito negativo su **testo** e **ntext** colonne del server. Se tuttavia si utilizza il [setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md) metodo con un tipo di conversione di caratteri specificato è supportato su **testo** e **ntext** colonne del server.|  
  
## <a name="binary-string-types"></a>Tipi di stringhe binarie  
 I tipi di stringa binaria JDBC sono **binario**, **VARBINARY**, e **LONGVARBINARY**.  
  
|Tipo|Description|  
|----------|-----------------|  
|A lunghezza fissa|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **binario** tipo è associato direttamente a Microsoft JDBC **binario** tipo. Si tratta di un tipo a lunghezza fissa con spaziatura messo a disposizione dal server nel caso in cui la colonna presenti SET ANSI_PADDING ON. La spaziatura viene aggiunta dal driver JDBC se mancante nelle colonne char del server.<br /><br /> Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **timestamp** è di tipo JDBC **binario** tipo con lunghezza fissa di 8 byte.|  
|A lunghezza variabile|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **varbinary** digitare esegue il mapping a JDBC **VARBINARY** tipo.<br /><br /> Il **udt** digitare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] esegue il mapping a JDBC come un **VARBINARY** tipo.|  
|Long|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **immagine** digitare esegue il mapping a JDBC **LONGVARBINARY** tipo. Questo tipo è deprecato a partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)], è necessario utilizzare un tipo di valori di grandi dimensioni, **varbinary (max)** invece.|  
  
## <a name="exact-numeric-types"></a>Tipi di valori numerici esatti  
 Ai tipi di valori numerici esatti di JDBC viene eseguito il mapping direttamente ai tipi corrispondenti di SQL Server.  
  
|Tipo|Description|  
|----------|-----------------|  
|BIT|Microsoft JDBC **BIT** tipo rappresenta un singolo bit che può essere 0 o 1. Esegue il mapping a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **bit** tipo.|  
|TINYINT|Microsoft JDBC **TINYINT** tipo rappresenta un singolo byte. Esegue il mapping a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **tinyint** tipo.|  
|SMALLINT|Microsoft JDBC **SMALLINT** tipo rappresenta un intero con segno a 16 bit. Esegue il mapping a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **smallint** tipo.|  
|INTEGER|Microsoft JDBC **intero** tipo rappresenta un intero con segno a 32 bit. Esegue il mapping a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **int** tipo.|  
|bigint|Microsoft JDBC **BIGINT** tipo rappresenta un intero con segno a 64 bit. Esegue il mapping a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **bigint** tipo.|  
|NUMERIC|Microsoft JDBC **numerico** tipo rappresenta un valore decimale a precisione fissa che contiene i valori di precisione identica. Il **numerico** esegue il mapping al tipo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **numerico** tipo.|  
|DECIMAL|Microsoft JDBC **decimale** tipo rappresenta un valore decimale a precisione fissa che include valori pari almeno alla precisione specificata. Il **decimale** esegue il mapping al tipo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **decimale** tipo.<br /><br /> Microsoft JDBC **decimale** tipo esegue il mapping al [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **money** e **smallmoney** tipi, che sono specifici tipi decimali a precisione fissa archiviati in 8 e 4 byte, rispettivamente.|  
  
## <a name="approximate-numeric-types"></a>Tipi di valori numerici approssimati  
 I tipi numerici approssimati di JDBC sono **reale**, **DOPPIE**, e **FLOAT**.  
  
|Tipo|Description|  
|----------|-----------------|  
|REAL|Microsoft JDBC **reale** tipo presenta sette cifre di precisione (precisione singola) e viene eseguito il mapping direttamente il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **reale** tipo.|  
|DOUBLE|Microsoft JDBC **DOPPIE** tipo presenta 15 cifre di precisione (precisione doppia) e viene eseguito il mapping per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **float** tipo. Microsoft JDBC **FLOAT** tipo è un sinonimo di **DOUBLE**. Poiché può esserci confusione tra **FLOAT** e **DOPPIE**, **DOPPIE** preferito.|  
  
## <a name="datetime-types"></a>Tipi datetime  
 Microsoft JDBC **TIMESTAMP** esegue il mapping al tipo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **datetime** e **smalldatetime** tipi. Il **datetime** tipo viene archiviato in due valori interi a 4 byte. Il **smalldatetime** tipo include le stesse informazioni (data e ora), ma con una minore precisione, in due valori interi piccoli a 2 byte.  
  
> [!NOTE]  
>  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **timestamp** tipo è un tipo di stringa binaria di lunghezza fissa. Non è mappato a uno dei tipi di fase JDBC: **data**, **ora**, o **TIMESTAMP**.  
  
## <a name="custom-type-mapping"></a>Mapping personalizzato dei tipi  
 La funzionalità di mapping del tipo personalizzato di JDBC, che utilizza le interfacce di dati SQL per JDBC avanzata tipi (UDT, Struct e così via). non è implementata nel driver JDBC.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sui tipi di dati del driver JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
