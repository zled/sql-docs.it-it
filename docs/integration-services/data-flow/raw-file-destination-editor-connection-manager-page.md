---
title: Editor destinazione File non elaborato (pagina Gestione connessione) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.rawfiledestinationconnectionmanager.f1
ms.assetid: a0ec9643-3b44-4467-b855-f45ae4794f7f
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9f27180b2dca144905af1a5346d3d8747aa8248a
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="raw-file-destination-editor-connection-manager-page"></a>Editor destinazione file non elaborato (pagina Gestione connessione)
  Utilizzare l'Editor destinazione file non elaborato per configurare la destinazione file non elaborato in modo da scrivere dati non elaborati in un file.  
  
 **Per saperne di più**  
  
-   [Aprire l'Editor destinazione file non elaborato](#open)  
  
-   [Impostare le opzioni nella scheda Gestione connessione](#connection)  
  
-   [Impostare le opzioni nella scheda Colonne](#mapping)  
  
##  <a name="open"></a> Aprire l'Editor destinazione file non elaborato  
  
1.  Aggiungere la destinazione file non elaborato in un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Fare clic con il pulsante destro del mouse sul componente e quindi scegliere **Modifica**.  
  
##  <a name="connection"></a> Impostare le opzioni nella scheda Gestione connessione  
 **Modalità di accesso**  
 Selezionare come il nome file viene specificato. Selezionare **Nome file** per immettere direttamente il nome file e il percorso o **Nome file da variabile** per specificare una variabile che contiene il nome file.  
  
 **Nome file** o **Nome variabile**  
 Immettere il nome e il percorso del file non elaborato o selezionare la variabile contenente il nome file.  
  
 **Opzione scrittura**  
 Selezionare il metodo utilizzato per creare e scrivere nel file.  
  
 **Generare file non elaborato iniziale**  
 Fare clic sul pulsante per generare un file non elaborato vuoto contenente solo le colonne (file di soli metadati) senza dover eseguire il pacchetto. Nel file sono contenute le colonne selezionate nella pagina **Colonne** di **Editor destinazione file non elaborato**. È possibile puntare l'origine file non elaborato a questo file di soli metadati.  
  
 Quando si fa clic su **Genera file non elaborato iniziale**, viene visualizzata una finestra di messaggio. Fare clic su **OK** per procedere con la creazione del file. Fare clic su **Annulla** per selezionare un elenco diverso di colonne nella pagina **Colonne** .  
  
##  <a name="mapping"></a> Impostare le opzioni nella scheda Colonne  
 **Colonne di input disponibili**  
 Selezionare uno o più colonne di input per scrivere nel file non elaborato.  
  
 **Colonna di input**  
 Una colonna di input viene aggiunta automaticamente a questa tabella quando la si seleziona in **Colonne di input disponibili**o è possibile selezionare direttamente la colonna di input in questa tabella.  
  
 **Alias di output**  
 Specificare un nome alternativo da utilizzare per la colonna di output.  
  
## <a name="see-also"></a>Vedere anche  
 [Destinazione file non elaborato](../../integration-services/data-flow/raw-file-destination.md)  
  
  
