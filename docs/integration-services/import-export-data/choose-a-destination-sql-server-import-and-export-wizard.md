---
title: Scegliere una destinazione (SQL Server importazione / esportazione guidata) | Documenti Microsoft
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
- sql13.dts.impexpwizard.chooseadestination.f1
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
caps.latest.revision: 104
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 4ff3c7c8413bd6b535e1c5f95e2a7b06b397c053
ms.contentlocale: it-it
ms.lasthandoff: 08/28/2017

---
# <a name="choose-a-destination-sql-server-import-and-export-wizard"></a>Scelta destinazione (Importazione/Esportazione guidata SQL Server)
 Dopo aver fornito informazioni sull'origine dei dati e su come connettersi a tale origine, nell'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene visualizzata l'opzione **Scegliere una destinazione**. In questa pagina è possibile specificare informazioni sulla destinazione per i dati e su come connettersi a tale destinazione.
  
Per informazioni sulle destinazioni di dati che è possibile usare, vedere [Quali origini e destinazioni di dati è possibile usare?](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources). 

## <a name="screen-shot-of-the-destination-page"></a>Screenshot della pagina Destinazione
Lo screenshot seguente mostra la prima parte della pagina **Scegliere una destinazione** della procedura guidata. Il resto della pagina presenta un numero variabile di opzioni che variano a seconda di destinazione che si sceglie di seguito.

![Scegli destinazione](../../integration-services/import-export-data/media/choose-destination.png)

## <a name="choose-a-destination"></a>Scegliere una destinazione
 **Destinazione**  
 Specificare la destinazione selezionando il provider di dati che può importare i dati nella destinazione.
 
-   **Il provider di dati che occorre è in genere deducibile dal nome**, perché il nome del provider contiene in genere il nome dell'oggetto di destinazione, ad esempio, *File Flat* destinazione, Microsoft *Excel*, Microsoft *accesso*, .net Framework Data Provider for *SqlServer*, .net Framework Data Provider for *Oracle*.

-   **Se si dispone di un driver ODBC per la destinazione**, selezionare .net Framework di Provider di dati per ODBC. Quindi immettere le informazioni specifiche del driver. Driver ODBC non sono elencati nell'elenco a discesa delle destinazioni. .Net Framework di Provider di dati per ODBC funge da wrapper per il driver ODBC. Per altre informazioni, vedere [connettersi a un'origine dati ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **Possono essere disponibili più provider per la destinazione.** In genere, è possibile selezionare qualsiasi provider che funziona con la destinazione. Ad esempio, per connettersi a Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile utilizzare il Provider di dati .NET Framework per SQL Server o il driver ODBC di SQL Server. (Altri provider sono ancora nell'elenco ma non sono più supportate). 

## <a name="my-destination-isnt-in-the-list"></a>La destinazione non è nell'elenco
-   **È possibile scaricare il provider di dati** da Microsoft o da terze parti. L'elenco dei provider di dati disponibili nel **destinazione** elenco include solo i provider installati nel computer. Per informazioni sulle destinazioni che è possibile utilizzare, vedere [quali origini dati e destinazioni è possibile usare?](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)

-   **È necessario un driver ODBC per la destinazione?** Driver ODBC non sono elencati nell'elenco a discesa delle destinazioni. Se si dispone di un driver ODBC per la destinazione, selezionare .net Framework di Provider di dati per ODBC. Quindi immettere le informazioni specifiche del driver. .Net Framework di Provider di dati per ODBC funge da wrapper per il driver ODBC. Per altre informazioni, vedere [connettersi a un'origine dati ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

-   **provider a 32 e 64 bit.** Se si sta eseguendo la procedura guidata a 64 bit, sarà possibile vedere le destinazioni per cui è installato un provider a 32 bit e viceversa.

> [!NOTE]
> Per utilizzare la versione a 64 bit di SQL Server di importazione / esportazione guidata, è necessario installare SQL Server. SQL Server Data Tools (SSDT) e SQL Server Management Studio (SSMS) sono applicazioni a 32 bit e installare solo i file a 32 bit, inclusa la versione a 32 bit della procedura guidata.

## <a name="after-you-choose-a-destination"></a>Dopo aver scelto una destinazione
Dopo aver scelto una destinazione, il resto del **scegliere una destinazione** pagina presenta un numero variabile di opzioni che dipendono dal provider di dati scelto.

Per connettersi a una destinazione di uso comune, vedere una delle seguenti pagine.
-   [Connettersi a SQL Server](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi a Oracle](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi ai file flat (file di testo)](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi a Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi a accesso](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi con ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [Connettersi all'archiviazione Blob di Azure](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [Connettersi a PostgreSQL](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [La connessione a MySQL](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)

Per informazioni su come connettersi a una destinazione che non è elencata, vedere [al riferimento di stringhe di connessione](https://www.connectionstrings.com/). In questo sito di terze parti sono stringhe di connessione di esempio e altre informazioni sui provider di dati e le informazioni di connessione che richiedono.

## <a name="whats-next"></a>Operazioni successive  
 Dopo aver fornito informazioni sulla destinazione dei dati e su come connettersi a tale destinazione, la pagina successiva è **Impostazione copia tabella o query**. In questa pagina è possibile specificare se si vuole copiare un'intera tabella o solo alcune righe. Per altre informazioni, vedere [Impostazione copia tabella o query](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md).  

## <a name="see-also"></a>Vedere anche
[Iniziare con questo semplice esempio dell'Importazione/Esportazione guidata](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)



