---
title: "Gestione dell&#39;editor e della modalit&#224; di visualizzazione | Microsoft Docs"
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
  - "Editor di query [SQL Server Management Studio], gestione del comportamento delle finestre"
  - "modalità di visualizzazione workbench [SQL Server Management Studio]"
  - "modalità a schermo intero [SQL Server Management Studio]"
  - "caratteri [SQL Server Management Studio]"
  - "a capo automatici [SQL Server Management Studio]"
  - "modalità spazio virtuale [SQL Server Management Studio]"
  - "divisione di visualizzazione del documento"
  - "visualizzazione di numeri di riga"
  - "modalità di visualizzazione [SQL Server Management Studio]"
ms.assetid: 25c58a14-9f94-4296-9770-7d84c6bc3969
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Gestione dell&#39;editor e della modalit&#224; di visualizzazione
  Nell'editor sono disponibili vari modi per gestire la visualizzazione del codice.  
  
## Modifica della modalità di visualizzazione  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] offre una modalità di visualizzazione denominata **Documenti a schede** che consente di aprire contemporaneamente più editor e documenti e di accedervi tramite schede visualizzate nella parte superiore dell'editor. In alternativa, è possibile aprire l'ambiente [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] in modalità interfaccia a più documenti (MDI, Multiple Document Interface), nella quale le finestre sono visualizzate senza schede e possono essere ancorate, affiancate, ridotte a icona e così via.  
  
#### Per passare da una modalità di visualizzazione all'altra  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Fare clic su **Ambiente**. Fare clic su **Generale**.  
  
3.  Selezionare **Documenti a schede** o **Ambiente MDI**.  
  
    > [!NOTE]  
    >  Le modifiche verranno applicate solo dopo il riavvio di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## Divisione di una finestra di visualizzazione  
 È possibile dividere una finestra dell'editor in due parti distinte per semplificare le operazioni di modifica.  
  
#### Per dividere una finestra  
  
1.  Fare clic sulla barra di divisione visualizzata sopra la barra di scorrimento.  
  
2.  Trascinare la barra di divisione verso il basso.  
  
3.  Per visualizzare di nuovo un solo riquadro, fare doppio clic sulla barra di divisione che separa i due riquadri.  
  
 Nel nuovo riquadro sarà visualizzato lo stesso documento e qualsiasi modifica apportata in un riquadro si rifletterà nell'altro, purché si sia posizionati nello stesso punto del documento.  
  
## A capo automatico  
 Quando si attiva l'opzione A capo automatico, la barra di scorrimento orizzontale viene rimossa e le righe di codice con una larghezza superiore alle dimensioni della finestra dell'editor vengono automaticamente mandate a capo sulla riga successiva visualizzata anziché scorrere nella parte non visibile della finestra.  
  
#### Per attivare il ritorno a capo automatico  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Fare clic su **Editor di testo**.  
  
3.  Aprire la cartella del linguaggio desiderato, oppure la cartella **Tutti i linguaggi** per eseguire l'impostazione per tutti i linguaggi.  
  
4.  Selezionare **A capo automatico**.  
  
## Attivazione della modalità spazio virtuale  
 Nella modalità **Spazio virtuale** le righe di codice possono continuare oltre l'area visibile dello schermo come se lo spazio alla fine di ogni riga fosse riempito da un numero infinito di spazi.  
  
#### Per attivare la modalità spazio virtuale  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Fare clic su **Editor di testo**.  
  
3.  Aprire la cartella del linguaggio desiderato, oppure la cartella **Tutti i linguaggi** per eseguire l'impostazione per tutti i linguaggi.  
  
4.  Selezionare **Attiva spazio virtuale**.  
  
 Quando la modalità spazio virtuale non è attivata, il cursore si sposta dalla fine di una riga al primo carattere della riga successiva e viceversa.  
  
## Visualizzazione dei numeri di riga  
 È possibile attivare la numerazione delle righe del codice. I numeri di riga sono utili per spostarsi all'interno del codice. Per altre informazioni, vedere [Spostarsi nel codice e nel testo](../../relational-databases/scripting/navigate-code-and-text.md).  
  
> [!NOTE]  
>  L'attivazione dei numeri di riga non attiva la stampa dei numeri di riga nel documento. Per stampare i numeri di riga è necessario selezionare la casella di controllo **Numeri di riga** nella finestra di dialogo **Imposta pagina** a cui si accede dal menu **File**.  
  
#### Per visualizzare i numeri di riga nel codice  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Fare clic su **Editor di testo**.  
  
3.  Fare clic su **Tutti i linguaggi**.  
  
4.  Fare clic su **Generale**.  
  
5.  Selezionare **Numeri di riga**.  
  
 Per impostare la numerazione delle righe solo per alcuni linguaggi di programmazione, selezionare **Numeri di riga** nella cartella appropriata.  
  
## Attivazione della modalità Schermo intero  
 È possibile attivare la modalità Schermo intero per nascondere tutte le finestre degli strumenti e visualizzare solo le finestre dei documenti.  
  
#### Per attivare la modalità Schermo intero  
  
1.  Per attivare (e successivamente disattivare) la modalità Schermo intero, premere ALT+MAIUSC+INVIO.  
  
## Utilizzo dell'opzione Nascondi tutto automaticamente  
  
#### Per nascondere tutte le finestre degli strumenti contemporaneamente  
  
1.  Scegliere **Nascondi tutto automaticamente** dal menu **Finestra**.  
  
  