---
title: I mapping delle colonne (Server importazione / esportazione guidata SQL) | Documenti Microsoft
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
- sql13.dts.impexpwizard.columnmapandtransform.f1
ms.assetid: eadc54a6-f936-4ffc-91d7-fbfd2bdcab93
caps.latest.revision: 69
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b1ed879f21396c3c8d588307eaf087daea8c44c3
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="column-mappings-sql-server-import-and-export-wizard"></a>Mapping colonne (Importazione/Esportazione guidata SQL Server)
  Dopo aver selezionato le tabelle e le viste esistenti per copiare o rivedere la query fornita, fare clic su **Modifica mapping**per consentire a Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di visualizzare la finestra di dialogo **Mapping colonne** . In questa pagina specificare e configurare le colonne di destinazione per ricevere i dati copiati da colonne di origine. Spesso non è necessario modificare qualsiasi elemento in questa pagina.
  
Se non si desidera copiare tutte le colonne della tabella che è selezionata, una cosa che è possibile eseguire in questa pagina è escludere le colonne che non desiderate. Selezionare **ignorare** nel **destinazione** colonna il **mapping** elenco per le colonne che non si desidera copiare.
 
## <a name="screen-shot-of-the-column-mappings-page"></a>Screenshot della pagina Mapping colonne 
 La schermata seguente mostra un esempio del **i mapping delle colonne** la finestra di dialogo della procedura guidata. 
 
 In questo esempio, notare come la procedura guidata creerà una nuova tabella di destinazione perché è stato selezionato **Crea tabella di destinazione** . Per impostazione predefinita, la procedura guidata assegna ogni colonna della nuova tabella di destinazione lo stesso nome, tipo di dati e le proprietà della colonna di origine corrispondente. 
  
 ![Pagina mapping di colonna dell'importazione / esportazione guidata](../../integration-services/import-export-data/media/column-mappings.png "pagina mapping di colonna dell'importazione / esportazione guidata")  
  
## <a name="review-the-source-and-destination"></a>Esaminare l'origine e destinazione 
![Sezione di pagina, origine e destinazione mapping colonne](../../integration-services/import-export-data/media/column-mappings-page-source-and-destination-section.png)

 **Origine**  
 La tabella di origine selezionato, vista o query.  
  
 **Destinazione**  
 La vista o tabella di destinazione selezionata.  

## <a name="optionally-create-a-new-destination-table"></a>Facoltativamente, creare una nuova tabella di destinazione
![Pagina mapping di colonna, nuova sezione di tabella](../../integration-services/import-export-data/media/column-mappings-page-new-table-section.png)

 **Crea tabella di destinazione/file**  
 Se non esiste già, creare la tabella di destinazione.    
  
 **Modifica codice SQL**  
Fare clic su **Modifica SQL** per aprire la finestra di dialogo **Istruzione SQL CREATE TABLE** . Utilizzare l'istruzione CREATE TABLE generata automaticamente o modificarla in base alle esigenze. Se si modifica questa istruzione manualmente, è necessario assicurarsi che l'elenco dei mapping delle colonne riconosca le modifiche. Per altre informazioni, vedere [Istruzione SQL CREATE TABLE](../../integration-services/import-export-data/create-table-sql-statement-sql-server-import-and-export-wizard.md).  

### <a name="sometimes-these-options-are-disabled"></a>A volte queste opzioni sono disabilitate
Il **creare una tabella di destinazione** opzione e **modifica SQL** pulsante vengono automaticamente abilitato o disabilitato automaticamente.

-   **Abilitata.** Se è stato specificato un **nuova** tabella di destinazione nel **Selezione origine tabelle e viste** pagina il **Crea tabella di destinazione** viene selezionata automaticamente e il  **Modifica codice SQL** pulsante è abilitato.

-   **Disabilitato.** Se si seleziona un **esistente** tabella di destinazione nel **Selezione origine tabelle e viste** pagina il **Crea tabella di destinazione** opzione e **Modifica codice SQL**  pulsante sono disabilitati. Se si desidera creare una nuova tabella di destinazione, tornare alla schermata di **Selezione origine tabelle e viste** pagina e immettere il nome di un **nuova** tabella il **destinazione** colonna.  

## <a name="what-about-existing-data-in-the-destination"></a>Per quanto riguarda i dati esistenti nella destinazione?
![Pagina mapping di colonna, sezione Opzioni](../../integration-services/import-export-data/media/column-mappings-page-options-section.png)

 **Elimina righe nella tabella di destinazione/file**  
 Consente di specificare se cancellare i dati da una tabella esistente prima di caricare nuovi dati.  
  
 **Aggiungi righe alla tabella di destinazione/file**  
 Consente di specificare se aggiungere nuovi dati a quelli già presenti in una tabella esistente.  
  
 **Elimina e ricrea tabella di destinazione**  
 Selezionare questa opzione per sovrascrivere la tabella di destinazione. Questa opzione è disponibile solo quando si utilizza la procedura guidata per creare la tabella di destinazione. La tabella di destinazione viene eliminata e ricreata solo se si salva il pacchetto creato dalla procedura guidata e quindi lo si esegue nuovamente. Questa opzione è utile per testare le impostazioni più volte.
  
 **Consenti IDENTITY_INSERT**  
 Selezionare questa opzione per consentire l'inserimento dei valori di identità esistenti nei dati di origine all'interno di una colonna Identity della tabella di destinazione. Per impostazione predefinita, generalmente non è possibile applicare questa opzione alla colonna Identity di destinazione.  
  
> [!TIP]
> Se le chiavi primarie esistenti si trovano in una colonna Identity, in una contatore o nell'equivalente, in genere è necessario selezionare questa opzione per mantenere i valori di chiave primaria esistenti.  In caso contrario la colonna Identity di destinazione assegna in genere nuovi valori.  

## <a name="keep-your-autonumber-or-identity-values"></a>Mantenere i valori del contatore o identità
Se si sta esportando i dati che dispone di una colonna contatore o una colonna identity, ad esempio, se si sta esportando da Microsoft Access - assicurarsi che si seleziona **Consenti IDENTITY_INSERT** come descritto in precedenza immediatamente.

## <a name="review-column-mappings"></a>Esaminare i mapping delle colonne
![Pagina mapping di colonna, sezione mapping](../../integration-services/import-export-data/media/column-mappings-page-mappings-section.png)

 **Mapping**  
 Consente di visualizzare la modalità di mapping tra ogni colonna nell'origine dati e una colonna nella destinazione.
 
L'elenco **Mapping** contiene le colonne seguenti.  
  
-    **Origine**  
     Consente di visualizzare ogni colonna di origine.  
  
-   **Destinazione**  
    Visualizzare la colonna di destinazione mappata o selezionare una colonna diversa.
    
    Non è necessario copiare tutte le colonne della tabella di origine. Selezionare **Ignora** per le colonne che si desidera ignorare. Prima di eseguire il mapping delle colonne, è necessario ignorare tutte le colonne di cui non verrà eseguito il mapping.  
  
-   **Tipo**  
    Visualizzare il tipo di dati per la colonna di destinazione o selezionare un tipo di dati diverso.
  
-   **Ammette i valori Null**  
    Consente di specificare se la colonna di destinazione ammette valori Null.  
  
-   **Dimensione**  
    Specificare il numero di caratteri nella colonna di destinazione, se applicabile.  
  
-    **Precisione**  
    Specificare la precisione dei dati numerici nella colonna di destinazione - il numero di cifre, se applicabile.  
  
 -   **Scala**  
    Specificare la scala dei dati numerici nella colonna di destinazione - il numero di cifre decimali, se applicabile.  
  
## <a name="whats-next"></a>Operazioni successive  
 Dopo aver esaminato e configurare le colonne di destinazione per ricevere i dati copiati da colonne di origine e fare clic su **OK**, **i mapping delle colonne** nuovamente la finestra di dialogo di **Seleziona origine Tabelle e viste** pagina o il **configurazione destinazione File Flat** pagina. Per altre informazioni, vedere [Seleziona tabelle e viste di origine](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md) o [Configurare la destinazione del file flat](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md).  
  
 Se nell'elenco **Mapping** è stato specificato un mapping che potrebbe non avvenire con successo, la finestra di dialogo **Mapping colonne** riporta alla pagina **Verifica mapping tra i tipi di dati** . In questa pagina, esaminare gli avvisi, specificare le opzioni di conversione e anche come gestire gli errori. Per altre informazioni, vedere [Verifica mapping tra i tipi di dati](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md).  
 
 ## <a name="see-also"></a>Vedere anche
[Mapping dei tipi di dati nell'Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)  
[Iniziare con questo semplice esempio dell'Importazione/Esportazione guidata](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)


