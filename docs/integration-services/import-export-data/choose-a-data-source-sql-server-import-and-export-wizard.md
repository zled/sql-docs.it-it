---
title: Scegliere un'origine dati (SQL Server importazione / esportazione guidata) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.chooseadatasource.f1
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
caps.latest.revision: 124
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 80d35cb294fd900611c73ca37bba2a66baef0767
ms.contentlocale: it-it
ms.lasthandoff: 08/28/2017

---
# <a name="choose-a-data-source-sql-server-import-and-export-wizard"></a>Scelta origine dati (Importazione/Esportazione guidata SQL Server)
  Dopo la pagina di benvenuto, l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mostra **Scelta origine dati**. In questa pagina è necessario fornire informazioni sull'origine dati e su come connettersi a tale origine.
  
Per informazioni sulle origini dati che è possibile usare, vedere [Quali origini dati e destinazioni è possibile usare](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)

## <a name="screen-shot-of-the-choose-a-data-source-page"></a>Screenshot della pagina Scegliere un'origine dati 
Lo screenshot seguente mostra la prima parte della pagina **Scegliere un'origine dati** della procedura guidata. Il resto della pagina presenta un numero variabile di opzioni che variano a seconda dell'origine dati che si sceglie di seguito.

![Scegliere l'origine](../../integration-services/import-export-data/media/choose-source.png)

## <a name="choose-a-data-source"></a>Scelta origine dati
 **Origine dati**  
Specificare l'origine dati selezionando un provider di dati che può connettersi all'origine.

-   **Il provider di dati che occorre è in genere deducibile dal nome**, perché il nome del provider contiene in genere il nome dell'origine dati - ad esempio, *File Flat* origine, Microsoft *Excel*, Microsoft *accesso*, .net Framework Data Provider for *SqlServer*, .net Framework Data Provider for *Oracle*.

-   **Se si dispone di un driver ODBC per l'origine dati**, selezionare .net Framework di Provider di dati per ODBC. Quindi immettere le informazioni specifiche del driver. Driver ODBC non sono elencati nell'elenco a discesa delle origini dati. .Net Framework di Provider di dati per ODBC funge da wrapper per il driver ODBC. Per altre informazioni, vedere [connettersi a un'origine dati ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **Potrebbero essere disponibili più provider per l'origine dati.** In genere è possibile selezionare qualsiasi provider che funziona con l'origine. Ad esempio, per connettersi a Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile utilizzare il Provider di dati .NET Framework per SQL Server o il driver ODBC di SQL Server. (Altri provider sono ancora nell'elenco ma non sono più supportate). 

## <a name="my-data-source-isnt-in-the-list"></a>Origine dati non è nell'elenco
-   **È possibile scaricare il provider di dati** da Microsoft o da terze parti. L'elenco dei provider di dati disponibili nel **origine dati** elenco include solo i provider installati nel computer. Per informazioni sulle origini dati che è possibile usare, vedere [Quali origini dati e destinazioni è possibile usare](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)

-   **È necessario un driver ODBC per l'origine dati?** Driver ODBC non sono elencati nell'elenco a discesa delle origini dati. Se si dispone di un driver ODBC per l'origine dati, selezionare .net Framework di Provider di dati per ODBC. Quindi immettere le informazioni specifiche del driver. .Net Framework di Provider di dati per ODBC funge da wrapper per il driver ODBC. Per altre informazioni, vedere [connettersi a un'origine dati ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **provider a 32 e 64 bit.** Se si sta eseguendo la procedura guidata a 64 bit, sarà possibile vedere origini dati per cui è installato un provider a 32 bit e viceversa.

> [!NOTE]
> Per utilizzare la versione a 64 bit di SQL Server di importazione / esportazione guidata, è necessario installare SQL Server. SQL Server Data Tools (SSDT) e SQL Server Management Studio (SSMS) sono applicazioni a 32 bit e installare solo i file a 32 bit, inclusa la versione a 32 bit della procedura guidata.

## <a name="after-you-choose-a-data-source"></a>Dopo aver scelto un'origine dati
Dopo aver scelto un'origine dati, il resto del **scegliere un'origine dati** pagina presenta un numero variabile di opzioni che dipendono dal provider di dati scelto.

Per connettersi a un'origine dati di uso comune, vedere una delle seguenti pagine.
-   [Connettersi a SQL Server](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi a Oracle](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi ai file flat (file di testo)](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi a Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi a accesso](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi con ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi all'archiviazione Blob di Azure](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [Connettersi a PostgreSQL](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [La connessione a MySQL](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)

Per informazioni su come connettersi a un'origine dati che non è elencata, vedere [al riferimento di stringhe di connessione](https://www.connectionstrings.com/). In questo sito di terze parti sono stringhe di connessione di esempio e altre informazioni sui provider di dati e le informazioni di connessione che richiedono.

## <a name="whats-next"></a>Operazioni successive  
 Dopo avere fornito informazioni sull'origine dei dati e su come connettersi a tale origine, la pagina successiva è **Scelta destinazione**. In questa pagina fornire informazioni sulla destinazione per i dati e su come connettersi a tale destinazione. Per altre informazioni, vedere [Scelta destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md).
 
## <a name="see-also"></a>Vedere anche
[Iniziare con questo semplice esempio dell'Importazione/Esportazione guidata](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)



