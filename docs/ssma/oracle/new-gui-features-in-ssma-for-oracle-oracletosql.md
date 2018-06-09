---
title: Nuove funzionalità di interfaccia utente grafica di SSMA per Oracle (OracleToSQL) | Documenti Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 62e2d30f-a73f-42d9-a6ab-3510a8198f4e
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 24bdabbdc3dfd436c745ceec086af71f5cb1d663
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34777567"
---
# <a name="new-gui-features-in-ssma-for-oracle-oracletosql"></a>Nuove funzionalità di interfaccia utente grafica di SSMA per Oracle (OracleToSQL)
In questo capitolo descrive nuove funzionalità dell'interfaccia utente di SSMA.  
  
## <a name="layouts"></a>Layout  
Questa funzionalità consente di scegliere una delle due finestre predefiniti disposizione o creare un layout. Per accedere a sottomenu layout, scegliere dal menu Visualizza dal layout. Non esiste è possibile scegliere uno dei layout esistente, aggiungere di nuovo layout o gestire layout.  
  
### <a name="add-current-layout"></a>Aggiungere il Layout corrente  
Per salvare i layout di windows corrente, dal menu Visualizza di layout, quindi aggiungere Layout corrente.  
  
### <a name="choose-predefined-layout"></a>Scegliere il layout predefinito  
Per scegliere uno dei layout predefinito, dal menu Visualizza di layout, quindi Layout predefinito o senza le finestre di esplorazione. È inoltre possibile utilizzare i tasti di scelta rapida Ctrl + Alt + 1 o Ctrl + Alt + 2 per layout predefiniti.  
  
### <a name="choose-user-defined-layout"></a>Scegliere il layout definite dall'utente  
Per scegliere layout definite dall'utente, scegliere Layout dal menu Visualizza, quindi fare clic su uno dei layout definite dall'utente. È anche possibile utilizzare i collegamenti definiti per il layout.  
  
### <a name="manage-layouts"></a>Gestire layout  
Per aprire una finestra di dialogo Gestisci layout, scegliere Layout dal menu Visualizza e fare clic su Gestisci layout. Nella finestra di dialogo Gestisci layout si troverà un elenco dei layout esistente sul lato sinistro della finestra di dialogo. Non esiste è possibile selezionare il layout per modificare le impostazioni. È inoltre possibile modificare l'ordine di layout nell'elenco o eliminare il layout utilizzando i pulsanti nella parte superiore nell'elenco. Sul lato destro della finestra di dialogo è possibile modificare le impostazioni di layout seguenti:  
  
-   Nome di layout  
  
-   Sincronizzazione delle finestre di esplorazione dei metadati  
  
-   Visibilità e la larghezza delle finestre di esplorazione dei metadati origine e di destinazione  
  
-   Visibilità di finestre di origine o destinazione e le relative dimensioni  
  
-   Visibilità e l'altezza di finestre supplementari  
  
## <a name="bookmarks"></a>Segnalibri  
Questa funzionalità consente di impostare uno o più segnalibri nell'origine o codice di destinazione, rapido trovato un segnalibro utilizzando i tasti di scelta rapida, gestire i segnalibri con una finestra di dialogo descrittivo.  
  
### <a name="toggle-bookmark"></a>Attiva/Disattiva segnalibro  
È possibile Imposta/Rimuovi un segnalibro nei modi seguenti:  
  
-   Utilizzare il pulsante Attiva/Disattiva segnalibro sopra finestra SQL di origine o di destinazione  
  
-   Scegliere l'area grigia a sinistra della finestra di SQL  
  
-   Utilizzare Ctrl + Maiusc +&lt;0..9&gt; per impostare un segnalibro numerato  
  
### <a name="bookmark-navigation"></a>Spostamento di segnalibro  
È possibile scorrere attraverso i segnalibri nei modi seguenti:  
  
-   Utilizzare i pulsanti segnalibro successivo segnalibro precedente nella parte superiore della finestra SQL  
  
-   Utilizzare Ctrl +&lt;0..9&gt; per trovare il segnalibro numerato  
  
-   Utilizzare i pulsanti Vai a visualizzazione origine o nella finestra di dialogo Gestisci segnalibri  
  
### <a name="removing-bookmark"></a>Rimozione di segnalibro  
È possibile rimuovere un segnalibro nei modi seguenti:  
  
-   Pulsante Cancella nella parte superiore della finestra SQL per rimuovere tutti i segnalibri nel documento corrente  
  
-   Utilizzare i pulsanti Rimuovi o Rimuovi tutto nella finestra di dialogo Gestisci segnalibri  
  
### <a name="manage-bookmarks"></a>Gestione di segnalibri  
Per aprire una finestra di dialogo Gestisci segnalibri, fare clic su Gestisci segnalibri dal menu Modifica. Nella finestra di dialogo verrà visualizzato un elenco di segnalibri. È possibile utilizzare i pulsanti sul lato destro della finestra di dialogo per gestire i segnalibri.  
  
## <a name="object-history"></a>Cronologia dell'oggetto  
Quando si passa gli oggetti, cronologia dell'interfaccia utente grafica di oggetto consente i vantaggi seguenti:  
  
-   È possibile utilizzare i pulsanti Indietro e Avanti per spostarsi tra gli oggetti che sono già selezionati  
  
-   Quando esegue il backup per l'oggetto, eseguire la stessa scheda che hai  
  
-   Quando si torna all'oggetto e la scheda è SQL, eseguire la stessa posizione del cursore che hai  
  
## <a name="advanced-search-capabilities"></a>Funzionalità di ricerca avanzate  
Funzionalità di ricerca avanzate forniscono le funzionalità di ricerca potenti e flessibili e consentono di trovare una dichiarazione dell'oggetto, ottenere informazioni sull'oggetto, eseguire una ricerca rapida, eseguire la ricerca in categorie in base a modelli e così via avanzata di oggetti.  
  
### <a name="get-quick-information"></a>Ottenere informazioni rapide  
È possibile ottenere informazioni rapide per l'oggetto in corrispondenza della posizione del cursore nei modi seguenti:  
  
-   Fare clic sul pulsante informazioni rapide nella parte superiore di finestra SQL  
  
-   Seleziona informazioni rapide del menu a comparsa del pulsante destro del mouse  
  
-   Premere Ctrl + Maiusc + barra spaziatrice  
  
### <a name="find-declaration"></a>Trovare dichiarazione  
È possibile passare alla dichiarazione dell'oggetto nella posizione del cursore nei modi seguenti:  
  
-   Fare clic sul pulsante Vai a dichiarazione sopra la finestra SQL  
  
-   Selezionare Vai a dichiarazione nel menu a comparsa pulsante destro del mouse  
  
-   Premere F12  
  
### <a name="quick-search"></a>Ricerca rapida  
È possibile eseguire la ricerca rapida utilizzando le funzionalità seguenti:  
  
-   È possibile avviare la ricerca tramite la scelta rapida Ctrl + F  
  
-   È possibile ripetere l'ultima ricerca in avanti utilizzando F3  
  
-   È possibile ripetere l'ultima ricerca all'indietro con MAIUSC + F3  
  
-   È possibile trovare l'occorrenza successiva della parola nella posizione del cursore utilizzando Ctrl + F3  
  
-   È possibile trovare l'occorrenza precedente della parola nella posizione del cursore utilizzando Ctrl + MAIUSC + F3  
  
-   È anche possibile eseguire tutte queste azioni con voci di menu.  
  
### <a name="advanced-search"></a>Ricerca avanzata  
Per aprire ricerca avanzata della finestra di dialogo Trova il punto dal menu Modifica, quindi fare clic su ricerca avanzata. Nella finestra di dialogo sarà in grado di trovare qualsiasi oggetto con modello. Nella parte superiore la finestra di dialogo è possibile scegliere le categorie di area e dell'oggetto di ricerca.  
  
