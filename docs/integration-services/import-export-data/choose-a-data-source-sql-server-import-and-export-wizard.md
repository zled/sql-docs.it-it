---
title: Scelta origine dati (Importazione/Esportazione guidata SQL Server) | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.chooseadatasource.f1
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7fe6c34e33f62bf5205763b2f2cf22f868ff418e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="choose-a-data-source-sql-server-import-and-export-wizard"></a>Scelta origine dati (Importazione/Esportazione guidata SQL Server)
  Dopo la pagina di benvenuto, l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mostra **Scelta origine dati**. In questa pagina è necessario fornire informazioni sull'origine dati e su come connettersi a tale origine.
  
Per informazioni sulle origini dati che è possibile usare, vedere [Quali origini dati e destinazioni è possibile usare](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)

## <a name="screen-shot-of-the-choose-a-data-source-page"></a>Screenshot della pagina Scegliere un'origine dati 
Lo screenshot seguente mostra la prima parte della pagina **Scegliere un'origine dati** della procedura guidata. Il resto della pagina presenta un numero variabile di opzioni a seconda dell'origine dati scelta.

![Scegliere l'origine](../../integration-services/import-export-data/media/choose-source.png)

## <a name="choose-a-data-source"></a>Scelta origine dati
 **Origine dati**  
Specificare l'origine dati selezionando un provider di dati che può connettersi all'origine.

-   **Il provider di dati necessario risulta in genere chiaro dal nome**, perché il nome del provider contiene di solito il nome dell'origine dati, ad esempio *Origine file flat*, Microsoft *Excel*, Microsoft *Access*, Provider di dati .NET Framework per *SQL Server*, Provider di dati .NET Framework per *Oracle*.

-   **Se si ha un driver ODBC per l'origine dati**, selezionare Provider di dati .NET Framework per ODBC, quindi immettere le informazioni specifiche del driver. I driver ODBC non sono presenti nell'elenco a discesa delle origini dati. Il provider di dati .Net Framework per ODBC funge da wrapper per il driver ODBC. Per altre informazioni, vedere [Connettersi a un'origine dati ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **Potrebbero essere disponibili più provider per l'origine dati.** In genere è possibile selezionare qualsiasi provider che funziona con l'origine. Ad esempio, per connettersi a Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è possibile usare il provider di dati .NET Framework per SQL Server o il driver ODBC di SQL Server. Nell'elenco sono presenti anche altri provider che però non sono più supportati. 

## <a name="my-data-source-isnt-in-the-list"></a>L'origine dati necessaria non è nell'elenco
-   **Può essere necessario scaricare il provider di dati** da Microsoft o da terze parti. L'elenco dei provider di dati disponibili nell'elenco **Origine dati** include solo i provider installati nel computer. Per informazioni sulle origini dati che è possibile usare, vedere [Quali origini dati e destinazioni è possibile usare](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)

-   **È disponibile un driver ODBC per l'origine dati?** I driver ODBC non sono presenti nell'elenco a discesa delle origini dati. Se si ha un driver ODBC per l'origine dati, selezionare Provider di dati .NET Framework per ODBC, quindi immettere le informazioni specifiche del driver. Il provider di dati .Net Framework per ODBC funge da wrapper per il driver ODBC. Per altre informazioni, vedere [Connettersi a un'origine dati ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **Provider a 32 bit e a 64 bit.** Se è in esecuzione la procedura guidata a 64 bit, non vengono visualizzate le origini dati per cui è installato solo un provider a 32 bit e viceversa.

> [!NOTE]
> Per usare la versione a 64 bit dell'Importazione/Esportazione guidata SQL Server, è necessario installare SQL Server. SQL Server Data Tools (SSDT) e SQL Server Management Studio (SSMS) sono applicazioni a 32 bit e installano solo i file a 32 bit, inclusa la versione a 32 bit della procedura guidata.

## <a name="after-you-choose-a-data-source"></a>Dopo aver scelto un'origine dati
Dopo aver scelto un'origine dati, il resto della pagina **Scelta origine dati** ha un numero variabile di opzioni a seconda del provider di dati scelto.

Per connettersi a un'origine dati di uso comune, vedere una delle pagine seguenti.
-   [Connettersi a SQL Server](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi a Oracle](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi a file flat (file di testo)](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi a Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi ad Access](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi con ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi ad Archiviazione BLOB di Azure](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [Connettersi a PostgreSQL](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi a MySQL](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)

Per informazioni su come connettersi a un'origine dati non elencata qui, vedere [The Connection Strings Reference](https://www.connectionstrings.com/). Questo sito di terze parti contiene stringhe di connessione di esempio e altre informazioni sui provider di dati e sulle informazioni di connessione richieste dai provider.

## <a name="whats-next"></a>Quali sono le operazioni successive?  
 Dopo avere fornito informazioni sull'origine dei dati e su come connettersi a tale origine, la pagina successiva è **Scelta destinazione**. In questa pagina fornire informazioni sulla destinazione per i dati e su come connettersi a tale destinazione. Per altre informazioni, vedere [Scelta destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md).
 
## <a name="see-also"></a>Vedere anche
[Iniziare con questo semplice esempio dell'Importazione/Esportazione guidata](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)


