---
title: "Passaggio 2: Creazione di un file danneggiato | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: cd0b18dc-66c3-4d88-86ef-8e40cb660fae
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# Passaggio 2: Creazione di un file danneggiato
Per illustrare la configurazione e la gestione degli errori di trasformazione, è necessario creare un file flat di esempio che nel corso dell'elaborazione generi l'errore di un componente.  
  
In questa attività verrà creata una copia di un file flat di esempio esistente. L'utente aprirà quindi il file in Blocco note e modificherà la colonna **CurrencyID** per assicurarsi che non si produca una corrispondenza durante la ricerca di trasformazioni. Quando il nuovo file verrà elaborato, l'esito negativo della ricerca impedirà l'esecuzione della trasformazione Currency Key Lookup e quindi del resto del pacchetto. Dopo aver creato il file di esempio danneggiato, verrà eseguito il pacchetto per osservare l'errore.  
  
### Per creare un file flat di esempio danneggiato  
  
1.  Aprire il file Currency_VEB.txt in Blocco note o in un altro editor di testo.  
  
    I dati di esempio sono inclusi nei pacchetti di lezioni di SSIS. Per scaricare i dati di esempio e i pacchetti di lezioni, effettuare le operazioni seguenti.  
  
    1.  Passare alla pagina relativa agli [esempi di prodotti di Integration Services](http://go.microsoft.com/fwlink/?LinkID=267527).  
  
    2.  Fare clic sulla scheda **DOWNLOADS** .  
  
    3.  Fare clic sul file SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
2.  Usare la funzionalità di ricerca e sostituzione dell'editor di testo per trovare tutte le istanze di **VEB** e sostituirle con **BAD**.  
  
3.  Nella stessa cartella degli altri file di dati di esempio, salvare il file modificato con il nome **Currency_BAD.txt**.  
  
    > [!IMPORTANT]  
    > Assicurarsi che il file **Currency_BAD.txt** venga salvato nella stessa cartella degli altri file di dati di esempio.  
  
4.  Chiudere l'editor di testo.  
  
### Per accertarsi che in fase di runtime si verifichi un errore  
  
1.  Scegliere **Avvia debug** dal menu **Debug**.  
  
    Alla terza iterazione del flusso di dati, la trasformazione Lookup Currency Key tenta di elaborare il file Currency_BAD.txt e ha esito negativo. L'errore della trasformazione provoca l'errore dell'intero pacchetto.  
  
2.  Scegliere **Arresta debug** dal menu **Debug**.  
  
3.  Nell'area di progettazione fare clic sulla scheda **Risultati esecuzione**.  
  
4.  Esplorare il registro e verificare che sia stato generato l'errore non gestito seguente:  
  
    `[Lookup Currency Key[27]] Error: Row yielded no match during lookup.`  
  
    > [!NOTE]  
    > Il numero 27 è l'ID del componente. Questo valore viene assegnato quando si compila il flusso di dati e può essere diverso da quello nel pacchetto.  
  
## Passaggi successivi  
[Passaggio 3: Aggiunta del reindirizzamento del flusso degli errori](../integration-services/step-3-adding-error-flow-redirection.md)  
  
  
  
