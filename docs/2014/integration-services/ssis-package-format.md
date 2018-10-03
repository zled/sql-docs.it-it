---
title: Formato dei pacchetti SSIS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: cfe0e5dc-5be3-4222-b721-fe83665edd94
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 43c0662c9084c654b4138a8443f1e2e98eaec376
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200021"
---
# <a name="ssis-package-format"></a>Formato del pacchetto SSIS
  Nella versione corrente di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sono state apportate modifiche significative al formato dei pacchetti (file DTSX) per semplificare la lettura del formato e il confronto dei pacchetti. Inoltre, è possibile unire in maniera più affidabile i pacchetti in cui non sono contenute modifiche in conflitto o modifiche archiviate in formato binario.  
  
 Per visualizzare il formato di file dei pacchetti DTSX corrente, vedere [\[MS-DTSX\]: Specifica per il formato di file dei pacchetti XLM Data Transformation Services](http://go.microsoft.com/fwlink/?LinkId=233251).  
  
 Nell'elenco seguente vengono indicate le modifiche al formato del file. Per visualizzare gli esempi di codice di queste modifiche, vedere la pagina relativa alle [modifiche al formato del pacchetto in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=233255).  
  
-   Sono state applicate convenzioni di formattazione per semplificare la lettura e la comprensione del file DTSX.  
  
-   Il formato è più conciso. Gli elementi separati per ogni proprietà sono stati resi persistenti come gli attributi, ad eccezione di PackageFormatVersion. Gli attributi sono elencati in ordine alfabetico e le proprietà con valori predefiniti non sono più persistenti. Infine, gli elementi che possono essere visualizzati più volte, sono ora contenuti all'interno di un elemento padre.  
  
-   La maggior parte degli oggetti all'interno di un pacchetto che può fare riferimento ad altri oggetti contiene ora un attributo `refId` definito nel pacchetto XML. Anziché rendere persistente gli ID di derivazione, ora è stato reso persistente `refID`. Gli ID di derivazione vengono ancora utilizzati all'interno del runtime e vengono rigenerati al caricamento del pacchetto.  
  
     Il `refId` valore è una stringa univoca che è leggibile e comprensibile, rispetto ai valori GUID o valori integer. La stringa è simile ai valori del percorso utilizzati per le configurazioni del pacchetto nelle versioni precedenti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
     Se si uniscono le modifiche tra due versioni di un pacchetto, il `refId` può essere utilizzato nelle operazioni di ricerca/sostituzione per verificare che tutti i riferimenti a tale oggetto siano stati aggiornati correttamente.  
  
-   Le informazioni sul layout sono contenute in una sezione CData.  
  
-   Le annotazioni sono persistenti in testo non crittografato. In questo modo è più facile estrarre le informazioni per la generazione automatica della documentazione.  
  
  
