---
title: Origini dati supportate nei modelli di SQL Server Analysis Services tabulari 1400 | Documenti Microsoft
ms.date: 03/26/2018
ms.prod: analysis-services
ms.suite: pro-bi
ms.topic: article
ms.assetid: ''
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d153a2ca638c2ab70e147d22d5755e70ab5aba06
ms.sourcegitcommit: 7246ef88fdec262fa0d34bf0e232f089e03a6911
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2018
---
# <a name="data-sources-supported-in-sql-server-analysis-services-tabular-1400-models"></a>Origini dati supportate in SQL Server Analysis Services i modelli tabulari 1400

[!INCLUDE[ssas-appliesto-sql2017](../../includes/ssas-appliesto-sql2017.md)]

In questo articolo descrive i tipi di origini dati che possono essere utilizzate con i modelli tabulari di SQL Server Analysis Services (SSAS) a livello di compatibilità 1400. 

Per i modelli tabulari di SSAS a livello di compatibilità 1200 e inferiore, vedere [origini dati supportate nei modelli di SQL Server Analysis Services tabulari 1200](data-sources-supported-ssas-tabular.md).

Per Azure Analysis Services, vedere [origini dati supportate in Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource).


## <a name="cloud-data-sources"></a>Origini dati cloud

|Origine dati di Azure  |In memoria  |DirectQuery  |
|---------|---------|---------|
|Azure SQL Database     |   Sì      |    Sì      |
|Azure SQL Data Warehouse     |   Sì      |   Sì       |
|Archiviazione BLOB Azure     |   Sì       |    no      |
|Archiviazione tabelle di Azure    |   Sì       |    no      |
|DB Cosmos Azure      |  Sì        |  no        |
|Archivio Azure Data Lake     |   Sì       |    no      |
|Azure HDInsight HDFS     |     Sì     |   no       |
|Spark in Azure HDInsight (Beta)     |   Sì       |   no       |
||||

**Provider**   
In memoria e i modelli DirectQuery, la connessione a origini dati di Azure è possibile utilizzare il Provider di dati di .NET Framework per SQL Server.

## <a name="on-premises-data-sources"></a>Origini dati locali

### <a name="supported-by-in-memory-and-directquery-models"></a>Supportato in memoria e i modelli DirectQuery

|Datasource | Provider in memoria | Provider di DirectQuery |
|  --- | --- | --- |
| SQL Server |SQL Server Native Client 11.0, Provider Microsoft OLE DB per SQL Server, il Provider di dati .NET Framework per SQL Server | Provider di dati .NET Framework per SQL Server |
| SQL Server Data Warehouse |SQL Server Native Client 11.0, Provider Microsoft OLE DB per SQL Server, il Provider di dati .NET Framework per SQL Server | Provider di dati .NET Framework per SQL Server |
| Oracle |Provider Microsoft OLE DB per Oracle, il Provider di dati Oracle per .NET |Provider di dati Oracle per .NET | |
| Teradata |Provider OLE DB per Teradata, il Provider di dati Teradata per .NET |Provider di dati Teradata per .NET | |
| | | |

> [!NOTE]
> Per i modelli in memoria, i provider OLE DB possono fornire prestazioni migliori per i dati su larga scala. Quando si sceglie tra provider diversi per la stessa origine dati, provare innanzitutto il provider OLE DB.  

### <a name="supported-by-in-memory-models-only"></a>Supportato da solo modelli in memoria

|Database  |
|---------|---------|---------|
|Database di Access     | 
|SQL Server Analysis Services     | 
|IBM Informix (beta) | 
|Documento JSON     | 
|Righe dai dati binari     | 
|Database MySQL     | 
|Database PostgreSQL    | Sì | no
|SAP HANA   | Sì | no
|SAP Business Warehouse    | Sì | no
|Database di Sybase     | Sì | no
|||

|File  |  
|---------|---------|
|Cartella di lavoro di Excel     |
|Cartella     | 
|JSON | 
|Testo/CSV    | 
|Tabella XML    | 
|||

|Servizi online  |  
|---------|---------|
|Dynamics 365      |
|Exchange Online     |
|Oggetti Saleforce    | 
|Report di Salesforce     |
|Elenco di SharePoint Online     |
|||

|Altro  |  
|---------|---------|
|Active Directory      | 
|Exchange     |  
|Feed OData     | 
|Query ODBC     | 
|OLE DB  | 
|Elenco SharePoint | 
|||

## <a name="see-also"></a>Vedere anche

[Origini dati supportate in SQL Server Analysis Services i modelli tabulari 1200](data-sources-supported-ssas-tabular.md)

[Origini dati supportate in Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)   