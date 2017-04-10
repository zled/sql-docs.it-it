---
title: "Mapping colonne (Importazione/Esportazione guidata SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.columnmapandtransform.f1"
ms.assetid: eadc54a6-f936-4ffc-91d7-fbfd2bdcab93
caps.latest.revision: 69
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 58
---
# Mapping colonne (Importazione/Esportazione guidata SQL Server)
  Dopo aver selezionato le tabelle e le viste esistenti per copiare o rivedere la query fornita, fare clic su **Modifica mapping** per consentire a Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di visualizzare la finestra di dialogo **Mapping colonne**. In questa pagina è necessario specificare e configurare le colonne di destinazione per ricevere i dati copiati.  
 
## <a name="screen-shot-of-the-column-mappings-page"></a>Screenshot della pagina Mapping colonne 
 L'immagine riportata di seguito illustra la finestra di dialogo **Mapping colonne** della procedura guidata. 
 
 In questo esempio, notare come la procedura guidata creerà una nuova tabella di destinazione perché è stato selezionato **Crea tabella di destinazione**. Per impostazione predefinita, ogni colonna nella nuova tabella di destinazione ha lo stesso nome e tipo di dati e le stesse proprietà della colonna di origine corrispondente. 
  
 ![Column mappings page of the Import and Export Wizard](../../integration-services/import-export-data/media/column-mappings.png "Column mappings page of the Import and Export Wizard")  
  
## <a name="confirm-the-source-and-destination"></a>Confermare l'origine e la destinazione  
 **Origine**  
 Identifica la tabella, la visualizzazione o la query di origine selezionata.  
  
 **Destinazione**  
 Identifica la tabella o la vista di destinazione selezionata.  

## <a name="create-a-new-destination-table"></a>Creare una nuova tabella di destinazione
 **Crea tabella di destinazione/file**  
 Creare la tabella di destinazione qualora non esista già.    
  
 **Modifica codice SQL**  
Fare clic su **Modifica SQL** per aprire la finestra di dialogo **Istruzione SQL CREATE TABLE**. Usare l'istruzione CREATE TABLE predefinita o modificarla in base alle proprie esigenze. Se si modifica questa istruzione manualmente, è necessario assicurarsi che l'elenco dei mapping delle colonne riconosca le modifiche. Per altre informazioni, vedere [Istruzione SQL CREATE TABLE](../../integration-services/import-export-data/create-table-sql-statement-sql-server-import-and-export-wizard.md).  
  
 > [!TIP] Se è stata specificata una nuova tabella di destinazione nella pagina **Seleziona tabelle e viste di origine**, l'opzione **Crea tabella di destinazione** viene selezionata automaticamente e il pulsante **Modifica codice SQL** è abilitato. In caso contrario, se si vuole creare la tabella di destinazione, è necessario tornare alla pagina **Seleziona tabelle e viste di origine** e immettere il nome di una **nuova** tabella nella colonna **Destinazione**.
>
> Se l'opzione **Crea tabella di destinazione** e il pulsante **Modifica codice SQL** sono disattivati nella pagina **Mapping colonne**, tornare alla pagina **Seleziona tabelle e viste di origine** e immettere il nome di una **nuova** tabella nella colonna **Destinazione**. Dopo aver specificato una nuova tabella o tabelle di destinazione e aver fatto clic su **Avanti**, l'opzione **Crea tabella di destinazione** viene selezionata automaticamente e il pulsante **Modifica codice SQL** è abilitato nella pagina **Mapping colonne**. Selezionare **Modifica codice SQL** per visualizzare la finestra di dialogo **Istruzione SQL CREATE TABLE **.  

## <a name="specify-options-for-existing-data-in-the-destination"></a>Specificare le opzioni per i dati esistenti nella destinazione
 **Elimina righe nella tabella di destinazione/file**  
 Consente di specificare se cancellare i dati da una tabella esistente prima di caricare nuovi dati.  
  
 **Aggiungi righe alla tabella di destinazione/file**  
 Consente di specificare se aggiungere nuovi dati a quelli già presenti in una tabella esistente.  
  
 **Elimina e ricrea tabella di destinazione**  
 Selezionare questa opzione per sovrascrivere la tabella di destinazione. Questa opzione è disponibile solo quando si utilizza la procedura guidata per creare la tabella di destinazione. La tabella di destinazione viene eliminata e ricreata solo se si salva il pacchetto creato dalla procedura guidata e quindi lo si esegue nuovamente. Questa opzione è utile per testare le impostazioni più volte.
  
 **Consenti IDENTITY_INSERT**  
 Selezionare questa opzione per consentire l'inserimento dei valori di identità esistenti nei dati di origine all'interno di una colonna Identity della tabella di destinazione. Per impostazione predefinita, generalmente non è possibile applicare questa opzione alla colonna Identity di destinazione.  
  
> [!TIP] Se le chiavi primarie esistenti si trovano in una colonna Identity, in una contatore o nell'equivalente, in genere è necessario selezionare questa opzione per mantenere i valori di chiave primaria esistenti.  In caso contrario la colonna Identity di destinazione assegna in genere nuovi valori.  

## <a name="review-column-mappings-and-destination-data-types"></a>Rivedere i mapping delle colonne e i tipi di dati di destinazione 
 **Mapping**  
 Consente di visualizzare la modalità di mapping tra ogni colonna nell'origine dati e una colonna nella destinazione.
 
 Selezionare **Ignora** nella colonna **Destinazione** per le colonne che non si desidera copiare. Non è necessario copiare tutte le colonne in una tabella.  
 
 ![Mapping colonne - mapping](../../integration-services/import-export-data/media/column-mappings-mappings.png)
  
 L'elenco **Mapping** contiene le colonne seguenti.  
  
-    **Origine**  
     Consente di visualizzare ogni colonna di origine per le quali è possibile specificare le impostazioni di conversione, se necessario.  
  
-   **Destinazione**  
    Visualizzare la colonna di destinazione mappata o selezionare una colonna diversa.
    
    Consente di specificare se ignorare una colonna durante l'operazione di copia. È possibile copiare solo un sottoinsieme di colonne selezionando **Ignora** per le colonne che si desidera ignorare. Prima di eseguire il mapping delle colonne, è necessario ignorare tutte le colonne di cui non verrà eseguito il mapping.  
  
-   **Tipo**  
    Visualizzare il tipo di dati per la colonna di destinazione o selezionare un tipo di dati diverso.
  
-   **Ammette i valori Null**  
    Consente di specificare se la colonna di destinazione ammette valori Null.  
  
-   **Dimensione**  
    Specificare il numero di caratteri nella colonna di destinazione, se applicabile.  
  
-    **Precisione**  
    Specificare la precisione dei dati numerici nella colonna di destinazione indicando il numero di cifre, se applicabile.  
  
 -   **Scala**  
    Specificare la scala dei dati numerici nella colonna di destinazione indicando il numero di cifre decimali, se applicabile.  
  
## <a name="whats-next"></a>Operazioni successive  
 Dopo aver specificato e configurato le colonne di destinazione per ricevere i dati copiati e aver fatto clic su **OK**, la finestra di dialogo **Mapping colonne**riporta alla pagina **Seleziona tabelle e viste di origine** o alla pagina **Configurare la destinazione del file flat**. Per altre informazioni, vedere [Seleziona tabelle e viste di origine](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md) o [Configurare la destinazione del file flat](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md).  
  
 Se nell'elenco **Mapping**è stato specificato un mapping che potrebbe non avvenire con successo, la finestra di dialogo **Mapping colonne** riporta alla pagina **Verifica mapping tra i tipi di dati**. In questa pagina, esaminare gli avvisi, specificare le opzioni di conversione e anche come gestire gli errori. Per altre informazioni, vedere [Verifica mapping tra i tipi di dati](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md).  
 
 ## <a name="see-also"></a>Vedere anche
[Data Type Mapping in the SQL Server Import and Export Wizard](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md) (Mapping dei tipi di dati nell'Importazione/Esportazione guidata SQL Server)
