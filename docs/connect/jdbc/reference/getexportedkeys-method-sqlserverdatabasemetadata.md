---
title: Metodo getExportedKeys (SQLServerDatabaseMetaData) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getExportedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 26888e61-b243-4a1b-922c-c0a451dcff4d
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e24d6268d5c46bb67b0ea97f593de1ccf7ec3f3c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getexportedkeys-method-sqlserverdatabasemetadata"></a>Metodo getExportedKeys (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descrizione delle colonne di chiave esterna che fanno riferimento alle colonne di chiave primaria della tabella specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.ResultSet getExportedKeys(java.lang.String cat,  
                                          java.lang.String schema,  
                                          java.lang.String table)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Cat*  
  
 Oggetto **stringa** che contiene il nome del catalogo.  
  
 *schema*  
  
 Oggetto **stringa** che contiene il nome dello schema.  
  
 *table*  
  
 Oggetto **stringa** che contiene il nome della tabella.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getExportedKeys viene specificato dal metodo getExportedKeys nell'interfaccia DatabaseMetaData.  
  
 Il set di risultati restituito dal metodo getExportedKeys conterrà le informazioni seguenti:  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|PKTABLE_CAT|**String**|Nome del catalogo che contiene la tabella di chiave primaria.|  
|PKTABLE_SCHEM|**String**|Nome dello schema della tabella di chiave primaria.|  
|PKTABLE_NAME|**String**|Nome della tabella di chiave primaria.|  
|PKCOLUMN_NAME|**String**|Nome della colonna della chiave primaria.|  
|FKTABLE_CAT|**String**|Nome del catalogo che contiene la tabella di chiave esterna.|  
|FKTABLE_SCHEM|**String**|Nome dello schema della tabella di chiave esterna.|  
|FKTABLE_NAME|**String**|Nome della tabella di chiave esterna.|  
|FKCOLUMN_NAME|**String**|Nome della colonna della chiave esterna.|  
|KEY_SEQ|**breve**|Numero di sequenza della colonna in una chiave primaria a più colonne.|  
|UPDATE_RULE|**breve**|Azione applicata alla chiave esterna quando l'operazione SQL è un aggiornamento. Può essere uno dei valori seguenti:<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|DELETE_RULE|**breve**|Azione applicata alla chiave esterna quando l'operazione SQL è un'eliminazione. Può essere uno dei valori seguenti:<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|FK_NAME|**String**|Nome della chiave esterna.|  
|PK_NAME|**String**|Nome della chiave primaria.|  
|DEFERRABILITY|**breve**|Indica se la valutazione del vincolo di chiave esterna può essere posticipata fino a quando non viene eseguito un commit. Può essere uno dei valori seguenti:<br /><br /> importedKeyInitiallyDeferred (5)<br /><br /> importedKeyInitiallyImmediate (6)<br /><br /> importedKeyNotDeferrable (7)|  
  
> [!NOTE]  
>  Per ulteriori informazioni sui dati restituiti dal metodo getExportedKeys, vedere "sp_fkeys (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo getExportedKeys per restituire informazioni su tutte le chiavi esterne che fanno riferimento a chiavi primarie della tabella Person Contact il [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] database di esempio.  
  
```  
public static void executeGetExportedKeys(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getExportedKeys("AdventureWorks", "Person", "Contact");  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
