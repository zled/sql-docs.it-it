---
title: Metodo getFunctionColumns (SQLServerDatabaseMetaData) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2b0e0f7-717c-48e6-bcd2-a325d938a833
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1508d70610c47116a4aaf58063b0f4196459d3e4
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getfunctioncolumns-method-sqlserverdatabasemetadata"></a>Metodo getFunctionColumns (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descrizione dei parametri e del tipo restituito delle funzioni utente o di sistema del catalogo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public ResultSet getFunctionColumns(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern  
                       java.lang.String columnNamePattern)  
```  
  
#### <a name="parameters"></a>Parametri  
 *catalogo*  
  
 Oggetto **stringa** che contiene il nome del catalogo. Se è una stringa vuota (""), il risultato include le funzioni senza un catalogo. Se è **null**, il nome del catalogo non viene utilizzato per la ricerca.  
  
 *schemaPattern*  
  
 Oggetto **stringa** che contiene il modello di nome dello schema. Se è una stringa vuota (""), il risultato include le funzioni senza uno schema. Se è **null**, il nome dello schema non viene utilizzato per la ricerca.  
  
 *functionNamePattern*  
  
 Oggetto **stringa** che contiene il nome di una funzione.  
  
 *columnNamePattern*  
  
 Oggetto **stringa** che contiene il nome di un parametro.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getFunctionColumns viene specificato dal metodo getFunctionColumns nell'interfaccia DatabaseMetaData.  
  
 Restituisce solo le funzioni e i parametri corrispondenti allo schema, al nome della funzione e al nome del parametro specificati all'interno del catalogo specificato.  
  
 Ogni riga nel set di risultati include le colonne seguenti per una descrizione del parametro, una descrizione della colonna o un tipo restituito:  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**String**|Nome del database contenente la funzione.|  
|FUNCTION_SCHEM|**String**|Schema della funzione.|  
|FUNCTION_NAME|**String**|Nome della funzione.|  
|COLUMN_NAME|**String**|Nome di un parametro o di una colonna.|  
|COLUMN_TYPE|**breve**|**Il tipo della colonna. Può essere uno dei valori seguenti:**<br /><br /> functionColumnUnknown (0): tipo sconosciuto.<br /><br /> functionColumnIn (1): parametro di input.<br /><br /> functionColumnInOut (2): parametro di input/output.<br /><br /> functionColumnOut (3): parametro di output.<br /><br /> functionReturn (4): valore restituito della funzione.<br /><br /> functionColumnResult (5): un parametro o una colonna è una colonna del set di risultati.|  
|DATA_TYPE|**smallint**|Tipo di dati SQL valore Java.SQL.|  
|TYPE_NAME|**String**|Nome del tipo di dati.|  
|PRECISION|**int**|Numero totale di cifre significative.|  
|LENGTH|**int**|Lunghezza dei dati in byte.|  
|SCALE|**breve**|Numero di cifre a destra del separatore decimale.|  
|RADIX|**breve**|Base per i tipi numerici.|  
|NULLABLE|**breve**|Indica se il parametro o valore restituito può contenere un **null** valore.<br /><br /> **Può essere uno dei valori seguenti:**<br /><br /> functionNoNulls (0): il valore NULL non è consentito.<br /><br /> functionNullable (1): il valore NULL è consentito.<br /><br /> functionNullableUnknown (2): sconosciuto.|  
|REMARKS|**String**|Commenti su una colonna o un parametro.|  
|COLUMN_DEF|**String**|Valore predefinito della colonna.<br /><br /> **Nota:** queste informazioni sono disponibili con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] e JDBC specifiche del driver.|  
|SQL_DATA_TYPE|**smallint**|Questa colonna corrisponde alla **DATA_TYPE** colonna, tranne che per il **datetime** e ISO **intervallo** tipi di dati.<br /><br /> **Nota:** queste informazioni sono disponibili con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] e JDBC specifiche del driver.|  
|SQL_DATETIME_SUB|**smallint**|Il **datetime** ISO **intervallo** sottocodice se il valore di **SQL_DATA_TYPE** è **SQL_DATETIME** o **SQL_INTERVAL**. Per i dati di tipi diversi da **datetime** e ISO **intervallo**, questa colonna è NULL.<br /><br /> **Nota:**queste informazioni sono disponibili con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] e JDBC specifiche del driver.|  
|CHAR_OCTET_LENGTH|**int**|Lunghezza massima dei parametri o delle colonne di tipo carattere o binario. Per gli altri tipi di dati il valore è NULL.|  
|ORDINAL_POSITION|**int**|Per i parametri di input e di output, rappresenta la posizione a partire da 1.<br /><br /> Per le colonne del set di risultati, è la posizione della colonna nel set di risultati a partire da 1.<br /><br /> Per il valore restituito, è 0.|  
|IS_NULLABLE|**String**|Determina se un parametro o una colonna ammette i valori Null.<br /><br /> Può essere uno dei valori seguenti:<br /><br /> **Sì**: il parametro o una colonna può includere valori NULL.<br /><br /> **NON**: il parametro o una colonna non può includere valori NULL.<br /><br /> Stringa vuota (""): sconosciuto.|  
|SS_TYPE_CATALOG_NAME|**String**|Nome del catalogo contenente il tipo definito dall'utente (UDT).|  
|SS_TYPE_SCHEMA_NAME|**String**|Nome dello schema contenente il tipo definito dall'utente (UDT).|  
|SS_UDT_CATALOG_NAME|**String**|Tipo definito dall'utente (UDT) del nome completo.|  
|SS_UDT_SCHEMA_NAME|**String**|Nome del catalogo in cui viene definito il nome di una raccolta di XML Schema. Se non è possibile trovare il nome del catalogo, questa variabile contiene una stringa vuota.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**String**|Nome dello schema in cui viene definito il nome di una raccolta di XML Schema. Se non è possibile trovare il nome dello schema, viene visualizzata una stringa vuota.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**String**|Nome di una raccolta di XML Schema. Se non è possibile trovare il nome, viene visualizzata una stringa vuota.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**String**|Nome del catalogo contenente il tipo definito dall'utente (UDT).|  
|SS_XML_SCHEMACOLLECTION_NAME|**String**|Nome dello schema contenente il tipo definito dall'utente (UDT).|  
|SS_DATA_TYPE|**tinyint**|Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipo di dati utilizzato da stored procedure estese.<br /><br /> **Nota** per ulteriori informazioni sui tipi di dati restituito da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], vedere "Tipi di dati (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione in linea.|  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
