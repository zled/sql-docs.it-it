---
title: Supporto per colonne di tipo sparse (ODBC) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 11ae959f-2fb6-4b85-ac5d-1476a82136d4
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2b294c0b1226722f98a14f1f49aeb077216a18d2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167580"
---
# <a name="sparse-columns-support-odbc"></a>Supporto per colonne di tipo sparse (ODBC)
  In questo argomento viene descritto il supporto ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client per le colonne di tipo sparse. Per un esempio che illustra il supporto ODBC per colonne di tipo sparse, vedere [chiamare SQLColumns in una tabella con colonne di tipo Sparse](../../native-client-odbc-how-to/call-sqlcolumns-on-a-table-with-sparse-columns.md). Per ulteriori informazioni sulle colonne di tipo sparse, vedere [supporto per colonne di tipo Sparse in SQL Server Native Client](../features/sparse-columns-support-in-sql-server-native-client.md).  
  
## <a name="statement-metadata"></a>Metadati di istruzione  
 Il campo di descrizione del parametro dell'applicazione (APD) e l'attributo dell'istruzione SQL_SOPT_SS_NAME_SCOPE accettano i valori aggiuntivi SQL_SS_NAME_SCOPE_EXTENDED e SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET. Questi valori specificano quali colonne sono incluse nel set di risultati restituito da [SQLColumns](../../native-client-odbc-api/sqlcolumns.md). Per ulteriori informazioni su SQL_SOPT_SS_NAME_SCOPE, vedere [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).  
  
 È possibile utilizzare un nuovo descrittore della riga di implementazione (IRD, Implementation Row Descriptor), un campo SQLSMALLINT di sola lettura denominato SQL_CA_SS_IS_COLUMN_SET, per determinare se una colonna è un valore XML di `column_set`. SQL_CA_SS_IS_COLUMN_SET accetta i valori SQL_TRUE e SQL_FALSE.  
  
## <a name="catalog-metadata"></a>Metadati del catalogo  
 Due [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] colonne specifiche (SS_IS_SPARSE e SS_IS_COLUMN_SET) sono stati aggiunti al set di risultati per [SQLColumns](../../native-client-odbc-api/sqlcolumns.md).  
  
## <a name="odbc-function-support-for-sparse-columns"></a>Supporto della funzione ODBC per colonne di tipo sparse  
 Sono state aggiornate le funzioni ODBC seguenti per supportare colonne di tipo sparse in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:  
  
-   [SQLColAttribute](../../native-client-odbc-api/sqlcolattribute.md)  
  
-   [SQLColumns](../../native-client-odbc-api/sqlcolumns.md)  
  
-   [SQLGetDescField](../../native-client-odbc-api/sqlgetdescfield.md)  
  
-   [SQLSetDescField](../../native-client-odbc-api/sqlsetdescfield.md)  
  
-   [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md)  
  
  