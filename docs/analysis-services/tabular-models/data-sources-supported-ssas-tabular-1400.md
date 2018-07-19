---
title: Origini dati supportate nei modelli 1400 tabulari di SQL Server Analysis Services | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 856e15e7365128bc79d119afe267334fb8470832
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38041659"
---
# <a name="data-sources-supported-in-sql-server-analysis-services-tabular-1400-models"></a>Origini dati supportate in SQL Server Analysis Services i modelli tabulari 1400

[!INCLUDE[ssas-appliesto-sql2017](../../includes/ssas-appliesto-sql2017.md)]

Questo articolo descrive i tipi di origini dati che possono essere utilizzate con i modelli tabulari di SQL Server Analysis Services (SSAS) a livello di compatibilità 1400. 

Per modelli tabulari di SSAS a livello di compatibilità 1200 e versioni precedenti, vedere [origini dati supportate nei modelli 1200 tabulari di SQL Server Analysis Services](data-sources-supported-ssas-tabular.md).

Per Azure Analysis Services, vedere [origini dati supportate in Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource).


## <a name="cloud-data-sources"></a>Origini dati cloud

|Origine dati di Azure  |In memoria  |DirectQuery  |
|---------|---------|---------|
|Database SQL di Azure     |   Sì      |    Sì      |
|Azure SQL Data Warehouse     |   Sì      |   Sì       |
|Archiviazione BLOB Azure     |   Sì       |    no      |
|Archiviazione tabelle di Azure    |   Sì       |    no      |
|Azure Cosmos DB      |  Sì        |  no        |
|Azure Data Lake Store     |   Sì       |    no      |
|Azure HDInsight HDFS     |     Sì     |   no       |
|Azure HDInsight Spark (Beta)     |   Sì       |   no       |
||||

**Provider**   
In memoria e i modelli DirectQuery, la connessione a origini dati di Azure usano Provider di dati .NET Framework per SQL Server.

## <a name="on-premises-data-sources"></a>Origini dati locali

### <a name="supported-by-in-memory-and-directquery-models"></a>Supportato in memoria e i modelli DirectQuery

|Origine dati | Provider in memoria | Provider DirectQuery |
|  --- | --- | --- |
| SQL Server |SQL Server Native Client 11.0, Provider Microsoft OLE DB per SQL Server, Provider di dati .NET Framework per SQL Server | Provider di dati .NET Framework per SQL Server |
| SQL Server Data Warehouse |SQL Server Native Client 11.0, Provider Microsoft OLE DB per SQL Server, Provider di dati .NET Framework per SQL Server | Provider di dati .NET Framework per SQL Server |
| Oracle |Provider Microsoft OLE DB per Oracle, Provider di dati Oracle per .NET |Provider di dati Oracle per .NET | |
| Teradata |Provider OLE DB per Teradata, Provider di dati Teradata per .NET |Provider di dati Teradata per .NET | |
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
|Righe dal file binario     | 
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
|Forum di Exhange Online     |
|Oggetti Salesforce    | 
|Report di Salesforce     |
|Elenchi SharePoint Online     |
|||

|Altro  |  
|---------|---------|
|Active Directory      | 
|Forum di Exhange     |  
|Feed OData     | 
|Query ODBC     | 
|OLE DB  | 
|Elenco di SharePoint | 
|||

## <a name="see-also"></a>Vedere anche

[Origini dati supportate in SQL Server Analysis Services i modelli tabulari 1200](data-sources-supported-ssas-tabular.md)

[Origini dati supportate in Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)   
