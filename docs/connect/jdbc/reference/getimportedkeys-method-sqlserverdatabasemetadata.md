---
title: Metodo getImportedKeys (SQLServerDatabaseMetaData) | Documenti Microsoft
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
apiname: SQLServerDatabaseMetaData.getImportedKeys
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: dc8c1a5e-700e-4059-a5ed-5013bbb87fb6
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8dc8dfc6d37fcd6ffb3c77105962e6d45b4be313
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="getimportedkeys-method-sqlserverdatabasemetadata"></a>Metodo getImportedKeys (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descrizione delle colonne di chiave primaria cui fanno riferimento le colonne di chiave esterna in una tabella.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.ResultSet getImportedKeys(java.lang.String cat,  
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
 Questo metodo getImportedKeys viene specificato dal metodo getImportedKeys nell'interfaccia DatabaseMetaData.  
  
 Il set di risultati restituito dal metodo getImportedKeys conterrà le informazioni seguenti:  
  
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
>  Per ulteriori informazioni sui dati restituiti dal metodo getImportedKeys, vedere "sp_fkeys (Transact-SQL)" in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo getImportedKeys per restituire informazioni su tutte le chiavi primarie che fanno riferimento chiavi esterne della tabella Person. Address di [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] database di esempio.  
  
```  
public static void executeGetImportedKeys(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getImportedKeys("AdventureWorks", "Person", "Address");  
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
  
  
