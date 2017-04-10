---
title: "Gestione della formattazione del codice | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applicazione di rientro a codice [SQL Server]"
  - "visualizzazione di URL"
  - "formattazione di codice [SQL Server Management Studio]"
  - "compressione di testo"
  - "formati [SQL Server], formattazione del codice in SQL Server Management Studio"
  - "nascondere testo"
  - "formati [SQL Server]"
  - "testo [SQL Server], formati del codice"
  - "rientro automatico"
  - "conversione di testo in lettere minuscole"
  - "editor di query [SQL Server Management Studio], gestione dei formati del codice"
  - "URL visualizzati in codice [SQL Server Management Studio]"
  - "conversione di testo in lettere maiuscole"
  - "testo [SQL Server]"
  - "annullamento del rientro di codice"
ms.assetid: ddbac4d2-6bdc-4467-a352-e869ec880eed
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Gestione della formattazione del codice
  L'editor consente di formattare il codice con rientri, testo nascosto, URL e così via. È inoltre possibile formattare il codice automaticamente durante la digitazione tramite la funzionalità intelligente per la gestione dei rientri.  
  
## Stili rientri  
 È possibile scegliere tra tre diversi stili di rientro del testo. È inoltre possibile specificare il numero di spazi di ogni singolo rientro o tabulazione e se per il rientro l'editor deve utilizzare tabulazioni o spazi.  
  
#### Per scegliere uno stile di rientro  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Fare clic su **Editor di testo**.  
  
3.  Selezionare la cartella **Tutti i linguaggi** per impostare i rientri per tutti i linguaggi.  
  
4.  Fare clic su **Tabulazioni**.  
  
5.  Selezionare una delle opzioni seguenti:  
  
    -   **None**. Il cursore si porta all'inizio della riga successiva.  
  
    -   **Blocco**. Il cursore allinea la riga successiva con quella precedente.  
  
    -   **Intelligenti** (impostazione predefinita). Il servizio di linguaggio determina lo stile di rientro appropriato da utilizzare.  
  
    > [!NOTE]  
    >  Non tutte le opzioni di rientro sono disponibili per tutti i linguaggi.  
  
#### Per modificare le impostazioni di tabulazione dei rientri  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Fare clic su **Editor di testo**.  
  
3.  Selezionare la cartella **Tutti i linguaggi** per impostare i rientri per tutti i linguaggi.  
  
4.  Fare clic su **Tabulazioni**.  
  
5.  Per specificare i caratteri per tabulazioni e rientri, fare clic su **Mantieni tabulazioni**. Per specificare spazi, selezionare **Inserisci spazi**.  
  
     Se si seleziona **Inserisci spazi**, immettere il numero di spazi per ogni tabulazione o rientro rispettivamente in **Dimensione tabulazione** o **Dimensione rientro**.  
  
#### Per rientrare il codice  
  
1.  Selezionare il testo che si desidera rientrare.  
  
2.  Premere TAB o fare clic sul pulsante **Rientra** sulla barra degli strumenti Standard.  
  
#### Per ridurre il rientro del codice  
  
1.  Selezionare il testo a cui applicare la riduzione del rientro.  
  
2.  Premere MAIUSC+TAB, oppure fare clic sul pulsante **Riduci rientro** sulla barra degli strumenti Standard.  
  
#### Per rientrare automaticamente tutto il codice  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Fare clic su **Editor di testo**.  
  
3.  Fare clic su **Tutti i linguaggi**.  
  
4.  Fare clic su **Tabulazioni**.  
  
5.  Scegliere **Intelligenti**.  
  
> [!NOTE]  
>  L'opzione **Intelligenti** non è disponibile per tutti i linguaggi.  
  
#### Per convertire gli spazi vuoti in tabulazioni  
  
1.  Selezionare il testo in cui si desidera convertire lo spazio vuoto in tabulazioni.  
  
2.  Scegliere **Avanzate** dal menu **Modifica** e quindi fare clic su **Inserisci tabulazione**.  
  
#### Per convertire le tabulazioni in spazi  
  
1.  Selezionare il testo in cui si desidera convertire le tabulazioni in spazi.  
  
2.  Scegliere **Avanzate** dal menu **Modifica** e quindi fare clic su **Rimuovi tabulazione**.  
  
 Il comportamento di questi comandi dipende dalle impostazioni di tabulazione nella finestra di dialogo** Opzioni**. Se, ad esempio, l'impostazione di tabulazione è 4, **Inserisci tabulazione** comporta la creazione di una tabulazione ogni 4 spazi contigui, mentre **Rimuovi tabulazione** comporta la creazione di 4 spazi per ogni tabulazione.  
  
## Conversione del testo in lettere maiuscole e minuscole  
 Sono previsti dei comandi per convertire un testo in tutte lettere maiuscole o minuscole.  
  
#### Per convertire un testo in lettere maiuscole o minuscole  
  
1.  Selezionare il testo che si desidera convertire.  
  
2.  Per convertirlo in lettere maiuscole, premere CTRL+MAIUSC+U, oppure scegliere **Maiuscole** dal sottomenu **Avanzate** del menu **Modifica**.  
  
3.  Per convertirlo in lettere minuscole, premere CTRL+MAIUSC+L, oppure scegliere **Minuscole** dal sottomenu **Avanzate** del menu **Modifica**.  
  
> [!NOTE]  
>  Per un elenco completo dei tasti di scelta rapida, vedere [Tasti di scelta rapida di SQL Server Management Studio](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md).  
  
## Visualizzazione e collegamenti agli URL  
 All'interno del codice è possibile creare e visualizzare URL selezionabili. Per impostazione predefinita:  
  
-   Gli URL sono sottolineati.  
  
-   Il puntatore del mouse si trasforma in una mano quando viene spostato su di essi.  
  
-   Se l'URL è valido, viene aperto quando si fa clic su di esso.  
  
#### Per visualizzare un URL selezionabile  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Fare clic su **Editor di testo**.  
  
3.  Per modificare l'opzione per un solo linguaggio, fare clic sulla cartella corrispondente e quindi scegliere **Generale**. Per modificarla per tutti i linguaggi, fare clic su **Tutti i linguaggi** e quindi scegliere **Generale**.  
  
4.  Selezionare **Consenti navigazione URL con clic singolo**.  
  
  