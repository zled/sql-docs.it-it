---
title: "Guida sensibile al contesto del Visualizzatore profilo dati | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "sql13.dts.dataprofileviewer.f1"
helpviewer_keywords: 
  - "Visualizzatore profilo dati [Integration Services]"
  - "Profiling dati - attività [Integration Services], visualizzatore"
ms.assetid: 3469c60a-8f4f-46ba-999a-cb9070197fea
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# Guida sensibile al contesto del Visualizzatore profilo dati
  Utilizzare il Visualizzatore profilo dati per visualizzare l'output dell'attività Profiling dati.  
  
 Per altre informazioni sull'uso del Visualizzatore profilo dati, vedere [Visualizzatore profilo dati](../../integration-services/control-flow/data-profile-viewer.md). Per altre informazioni sull'uso dell'attività Profiling dati che crea l'output del profilo analizzato nel Visualizzatore profilo dati, vedere [Impostazione dell'attività Profiling Dati](../../integration-services/control-flow/setup-of-the-data-profiling-task.md).  
  
## Opzioni statiche  
 **Apertura**  
 Consente di accedere al file salvato che contiene l'output dell'attività Profiling dati.  
  
 Riquadro **Profili**  
 Espandere l'albero nel riquadro **Profili** per visualizzare i profili inclusi nell'output. Selezionare un profilo per visualizzarne i risultati.  
  
 Riquadro **Messaggio**  
 Visualizza i messaggi di stato.  
  
 Riquadro **Drill-down**  
 Visualizza le righe di dati che corrispondono a un valore nell'output, se l'origine dati utilizzata dall'attività Profiling dati è disponibile.  
  
 Se, ad esempio, si visualizza l'output di un profilo Distribuzione valori di colonna per una colonna US State, il riquadro **Distribuzione dettagliata valori** potrebbe contenere una riga per "WA". Fare doppio clic sulla riga nel riquadro **Distribuzione dettagliata valori** per visualizzare le righe di dati in cui il valore della colonna di stato è "WA" nel riquadro di drill-down.  
  
## Opzioni dinamiche  
  
### Tipo di profilo: profilo Distribuzione lunghezze di colonna  
  
#### Profilo Distribuzione lunghezze di colonna - riquadro \<colonna>  
 **Lunghezza minima**  
 Visualizza la lunghezza minima dei valori nella colonna.  
  
 **Lunghezza massima**  
 Visualizza la lunghezza massima dei valori nella colonna.  
  
 **Ignora spazi iniziali**  
 Indica se il profilo è stato calcolato con un valore **IgnoreLeadingSpaces** impostato su True o False. Questa proprietà è stata impostata nella pagina **Richieste profilo** in Editor attività Profiling dati.  
  
 **Ignora spazi finali**  
 Indica se il profilo è stato calcolato con un valore **IgnoreTrailingSpaces** impostato su True o False. Questa proprietà è stata impostata nella pagina **Richieste profilo** in Editor attività Profiling dati.  
  
 **Conteggio righe**  
 Visualizza il numero di righe della tabella o della vista.  
  
#### Riquadro Distribuzione dettagliata lunghezze  
 **Lunghezza**  
 Visualizza le lunghezze di colonna rilevate nella colonna analizzata.  
  
 **Count**  
 Visualizza il numero di righe in cui il valore della colonna analizzata ha la lunghezza indicata nella colonna **Lunghezza**.  
  
 **Percentuale**  
 Visualizza la percentuale di righe in cui il valore della colonna analizzata ha la lunghezza indicata nella colonna **Lunghezza**.  
  
### Tipo di profilo: profilo Rapporto di valori Null nella colonna  
  
#### Profilo Rapporto di valori Null - riquadro \<colonna>  
 **Conteggio valori Null**  
 Visualizza il numero di righe in cui il valore della colonna analizzata è un valore Null.  
  
 **Percentuale valori Null**  
 Visualizza la percentuale di righe in cui il valore della colonna analizzata è un valore Null.  
  
 **Conteggio righe**  
 Visualizza il numero di righe della tabella o della vista.  
  
### Tipo di profilo: profilo Criteri di ricerca colonna  
  
#### Profilo Criteri di ricerca colonna - riquadro \<colonna>  
 **Conteggio righe**  
 Visualizza il numero di righe della tabella o della vista.  
  
#### Riquadro Distribuzione criteri di ricerca  
 **Pattern**  
 Visualizza i modelli calcolati per la colonna analizzata.  
  
 **Percentuale**  
 Visualizza la percentuale di righe i cui valori corrispondono al modello visualizzato nella colonna **Modello**.  
  
### Tipo di profilo: profilo Statistiche di colonna  
  
#### Profilo Statistiche di colonna - riquadro \<colonna>  
 **Minimo**  
 Visualizza il valore minimo rilevato nella colonna analizzata.  
  
 **Massimo**  
 Visualizza il valore massimo rilevato nella colonna analizzata.  
  
 **Media**  
 Visualizza la media dei valori rilevati nella colonna analizzata.  
  
 **Deviazione standard**  
 Visualizza la deviazione standard dei valori rilevati nella colonna analizzata.  
  
### Tipo di profilo: profilo Distribuzione valori di colonna  
  
#### Profilo Distribuzione valori di colonna - riquadro \<colonna>  
 **Numero di valori distinct**  
 Visualizza il conteggio dei valori distinct rilevati nella colonna analizzata.  
  
 **Conteggio righe**  
 Visualizza il numero di righe della tabella o della vista.  
  
#### Riquadro Distribuzione dettagliata valori  
 **Valore**  
 Visualizza i valori distinct rilevati nella colonna analizzata.  
  
 **Count**  
 Visualizza il numero di righe in cui la colonna analizzata ha il valore indicato nella colonna **Valore**.  
  
 **Percentuale**  
 Visualizza la percentuale di righe in cui la colonna analizzata ha il valore indicato nella colonna **Valore**.  
  
### Tipo di profilo: profilo Chiave candidata  
  
#### Profilo Chiave candidata - riquadro \<tabella>  
 **Colonne chiave**  
 Visualizza le colonne selezionate per l'analisi come chiave candidata.  
  
 **Attendibilità chiave**  
 Visualizza il livello di attendibilità (come percentuale) della colonna o combinazione di colonne chiave candidata. Un livello di attendibilità inferiore al 100% indica la presenza di valori duplicati.  
  
#### Riquadro Violazioni chiave  
 **\<colonna1>, \<colonna2>, ecc.**  
 Visualizza i valori duplicati rilevati nella colonna analizzata.  
  
 **Count**  
 Visualizza il numero di righe in cui la colonna specificata ha il valore indicato nella prima colonna.  
  
### Tipo di profilo: profilo Dipendenza funzionale  
  
#### Riquadro Profilo Dipendenza funzionale  
 **Colonne determinanti**  
 Visualizza la colonna o le colonne selezionate come colonne determinanti. Nell'esempio in cui uno stesso codice postale ZIP (Stati Uniti) deve essere associato sempre allo stesso stato, il codice postale rappresenta la colonna determinante.  
  
 **Colonna dipendente**  
 Visualizza la colonna o le colonne selezionate come colonne dipendenti. Nell'esempio in cui uno stesso codice postale ZIP (Stati Uniti) deve essere associato sempre allo stesso stato, lo stato rappresenta la colonna dipendente.  
  
 **Attendibilità dipendenza funzionale**  
 Visualizza il livello di attendibilità (come percentuale) della dipendenza funzionale tra colonne. Un livello di attendibilità inferiore al 100% indica che vi sono casi in cui il valore determinante non determina il valore dipendente. Nell'esempio in cui uno stesso codice postale ZIP (Stati Uniti) deve essere associato sempre allo stesso stato, tale livello di attendibilità indica che alcuni valori di stato non sono validi.  
  
#### Riquadro Violazioni dipendenza funzionale  
  
> [!NOTE]  
>  Una percentuale elevata di valori non corretti nei dati può provocare risultati imprevisti da un profilo Dipendenza funzionale. Ad esempio, il 90% delle righe contiene il valore di stato "WI" per il valore di codice postale ZIP "98052". Il profilo segnala le righe che contengono il valore di stato "WA" corretto come violazioni.  
  
 **\<nome colonna determinante>**  
 Visualizza il valore della colonna determinante o della combinazione di colonne determinanti in questa istanza di una violazione della dipendenza funzionale.  
  
 **\<nome colonna dipendente>**  
 Visualizza il valore della colonna dipendente in questa istanza di una violazione della dipendenza funzionale.  
  
 **Conteggio del supporto**  
 Visualizza il numero di righe in cui il valore della colonna determinante determina la colonna dipendente.  
  
 **Conteggio violazioni**  
 Visualizza il numero di righe in cui il valore della colonna determinante non determina la colonna dipendente. Si tratta delle righe in cui i valori dipendenti corrispondono ai valori indicati nella colonna **\<nome colonna dipendente>**.  
  
 **Percentuale del supporto**  
 Visualizza la percentuale di righe in cui la colonna determinante determina la colonna dipendente.  
  
### Tipo di profilo: profilo Inclusione valore  
  
#### Riquadro Profilo Inclusione valore  
 **Colonne lato subset**  
 Visualizza la colonna o la combinazione di colonne analizzate per determinare se sono incluse nelle colonne del superset.  
  
 **Colonne lato superset**  
 Visualizza la colonna o la combinazione di colonne analizzate per determinare se includono i valori delle colonne del subset.  
  
 **Attendibilità inclusione**  
 Visualizza il livello di attendibilità (come percentuale) della sovrapposizione tra colonne. Un livello di attendibilità inferiore al 100% indica che vi sono casi in cui il valore del subset non viene rilevato tra i valori del superset.  
  
#### Riquadro Violazioni inclusione  
 **\<colonna1>, \<colonna2>, ecc.**  
 Visualizza i valori nella colonna o colonne del subset che non sono disponibili nella colonna o colonne del superset.  
  
 **Count**  
 Visualizza il numero di righe in cui la colonna specificata ha il valore indicato nella prima colonna.  
  
## Vedere anche  
 [Visualizzatore profilo dati](../../integration-services/control-flow/data-profile-viewer.md)   
 [Attività Profiling dati e visualizzatore](../../integration-services/control-flow/data-profiling-task-and-viewer.md)  
  
  