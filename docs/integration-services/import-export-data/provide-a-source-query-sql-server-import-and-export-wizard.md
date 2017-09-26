---
title: Specificare una Query di origine (Server importazione / esportazione guidata SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.providesourcequery.f1
ms.assetid: c8cbd07e-b9c3-422f-94b8-d6fc8cf31cf5
caps.latest.revision: 61
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 190c39de92d8fc1b559f43c90c95e446ccc87272
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="provide-a-source-query-sql-server-import-and-export-wizard"></a>Impostazione query di origine (Importazione/Esportazione guidata SQL Server)
Se è stato specificato che si vuole fornire una query per selezionare i dati da copiare, l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] visualizza **Impostazione query di origine**. In questa pagina è necessario scrivere e testare la query SQL che seleziona i dati da copiare dall'origine dati alla destinazione. È anche possibile incollare il testo di una query salvata o caricare il testo della query da un file.

## <a name="screen-shot-of-the-source-query-page"></a>Screenshot della pagina Query di origine  
La schermata seguente mostra la pagina **Impostazione query di origine** della procedura guidata.
 
In questo semplice esempio, l'utente ha immesso la query `SELECT * FROM Sales.Customer` per copiare tutte le righe e tutte le colonne di **Sales. Customer** tabella nel database di origine.
-   `SELECT *`significa copia tutte le colonne.
-   L'assenza di un `WHERE` clausola significa copiare tutte le righe.
  
 ![Pagina di query di origine dell'importazione / esportazione guidata](../../integration-services/import-export-data/media/source-query.png "pagina di query di origine dell'importazione / esportazione guidata")  

## <a name="provide-the-query-and-check-its-syntax"></a>Specificare la query e controllarne la sintassi
**Istruzione SQL**  
 Digitare una query SELECT per recuperare righe e colonne di dati dal database di origine. È anche possibile incollare il testo di una query salvata o caricare la query da un file facendo clic su **Sfoglia**. 
  
 Ad esempio, la query seguente recupera il **SalesPersonID**, **SalesQuota**, e **SalesYTD** dall'esempio di AdventureWorks database per i venditori la cui proprietà percentuale di Commissione è superiore all'1,5%.  
  
```sql
SELECT SalesPersonID, SalesQuota, SalesYTD  
FROM Sales.SalesPerson  
WHERE CommissionPct > 0.015  
```  

Per altri esempi di query SELECT, vedere [Esempi di istruzioni SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-examples-transact-sql.md) o eseguire una ricerca online.  

Se l'origine dati è Excel, vedere [Specificare una query di origine per Excel](#excelQueries) più avanti in questo argomento per informazioni su come specificare fogli di lavoro Excel e intervalli in una query.
  
 **Analizza**  
 Controlla la sintassi dell'istruzione SQL immessa nella casella di testo **Istruzione SQL** .  
  
> [!NOTE]
> Se il tempo necessario per controllare la sintassi dell'istruzione supera il valore di timeout di 30 secondi, l'analisi si arresta e genera un errore. Non sarà possibile andare oltre questa pagina della procedura guidata fino a quando l'analisi non riesce. Una soluzione per evitare il timeout consiste nel creare una vista di database basata sulla query che si vuole usare e quindi eseguire la query sulla vista dalla procedura guidata, invece di immettere direttamente il testo della query.  
  
 **Sfoglia**  
 Selezionare un file salvato che contiene il testo di una query SQL tramite il **aprire** la finestra di dialogo. La selezione di un file copia il testo dal file alla casella di testo **Istruzione SQL** .  
 
## <a name="excelQueries"></a> Specificare una query di origine per Excel
### <a name="specify-excel-objects-in-queries"></a>Specificare gli oggetti di Excel nelle query
Le query possono essere eseguite in tre tipi di oggetti Excel.
-   **Foglio di lavoro.** Per eseguire una query in un foglio di lavoro, aggiungere il carattere $ alla fine del nome del foglio e aggiungere delimitatori all'inizio e alla fine della stringa, ad esempio **[Foglio1$]**.

    ```
    SELECT * FROM [Sheet1$]
    ```

-   **Intervallo denominato.** Per eseguire una query in un intervallo denominato, è sufficiente usare il nome dell'intervallo, ad esempio **MioIntervalloDati**.
    
    ```
    SELECT * FROM MyDataRange
    ```

-   **Intervallo senza nome.** Per specificare un intervallo di celle a cui non è stato assegnato un nome, aggiungere il carattere $ alla fine del nome del foglio, aggiungere la specifica dell'intervallo e aggiungere delimitatori all'inizio e alla fine della stringa, ad esempio **[Foglio1$A1:B4]**.

    ```
    SELECT * FROM [Sheet1$A1:B4]
    ```

### <a name="prepare-the-excel-source-data"></a>Preparare i dati di origine Excel
Quando si specifica un foglio di lavoro o un intervallo come tabella di origine, il driver legge il blocco di celle *contigue* che inizia con la prima cella non vuota nell'angolo superiore sinistro del foglio di lavoro o dell'intervallo. Per questa ragione, i dati di origine non possono includere righe vuote. Ad esempio, non può essere presente una riga vuota tra le intestazioni di colonna e le righe di dati. Se è presente un titolo seguito da righe vuote nella parte superiore del foglio di lavoro sopra i dati, non è possibile eseguire query nel foglio di lavoro. In Excel è necessario assegnare un nome all'intervallo di dati ed eseguire una query nell'intervallo denominato anziché nel foglio di lavoro.

## <a name="whats-next"></a>Operazioni successive  
 Dopo aver scritto e testato la query SQL che seleziona i dati da copiare, la pagina successiva dipende dalla destinazione dei dati.  
  
-   Per la maggior parte delle destinazioni la pagina successiva è **Selezione tabelle e viste di origine**. In questa pagina è possibile esaminare la query specificata e, facoltativamente, scegliere le colonne da copiare e visualizzare un'anteprima dei dati di esempio. Per altre informazioni, vedere [Selezione tabelle e viste di origine](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md).  
  
-   Se la destinazione è un file flat, la pagina successiva è **Configurazione destinazione file flat**. In questa pagina è possibile specificare le opzioni di formattazione per il file flat di destinazione. Dopo aver configurato il file flat, la pagina successiva è **Selezione tabelle e viste di origine**. Per altre informazioni, vedere [Configurazione destinazione file flat](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md).  



