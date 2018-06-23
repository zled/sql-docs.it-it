---
title: Proprietà catalogo full-Text (pagina generale) | Documenti Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-search
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.general.f1
ms.assetid: d1f66762-2d40-4f24-b635-a417d22ee79a
caps.latest.revision: 34
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: fc774b0dfd87ae4f63e9332dd6813d92f79e4a5c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167919"
---
# <a name="full-text-catalog-properties-general-page"></a>Proprietà catalogo full-text (pagina Generale)
  Questa sezione illustra le opzioni e le funzioni disponibili nella **generali** pagina del **proprietà catalogo Full-Text** finestra di dialogo.  
  
> [!NOTE]  
>  Per [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database, un catalogo full-text è un concetto logico che fa riferimento a un gruppo di indici full-text. Il catalogo full-text è un oggetto virtuale che non appartiene ad alcun filegroup.  
  
## <a name="options"></a>Opzioni  
  
### <a name="properties"></a>Proprietà  
 **Catalogo predefinito**  
 Indica se il catalogo è quello predefinito per il database.  
  
 **Stato popolamento**  
 Indica lo stato del catalogo. I valori possibili sono:  
  
-   **Inattività**  
  
-   **Ricerca per indicizzazione in corso**  
  
-   **In sospeso**  
  
-   **Limitata**  
  
-   **Il ripristino**  
  
-   **Arresto**  
  
-   **Popolamento incrementale in corso**  
  
-   **Compilazione dell'indice**  
  
-   **Disco è pieno, in pausa**  
  
-   **Change tracking**  
  
 **Numero di elementi**  
 Consente di visualizzare il numero di elementi full-text presenti nel catalogo.  
  
 **Dimensioni catalogo**  
 Consente di visualizzare le dimensioni in megabyte del catalogo full-text.  
  
 **Nome**  
 Nome del catalogo full-text.  
  
 **Distinzione caratteri accentati**  
 Visualizza o modifica se il catalogo è sensibile ai segni diacritici, quali la tilde (**~**), accento acuto (**´**), o l'umlaut (**¨**). I valori validi sono:  
  
-   **No**  
  
-   **Sì**  
  
-   Per informazioni sui segni diacritici, vedere [segno diacritico](http://go.microsoft.com/fwlink/?LinkId=154091) nell'Enciclopedia Encarta di MSN.  
  
 **Data ultimo popolamento**  
 Consente di visualizzare la data dell'ultimo popolamento del catalogo.  
  
 **Proprietario**  
 Proprietario del catalogo full-text.  
  
 **Conteggio chiavi univoche**  
 Numero di parole univoche che costituiscono l'indice full-text del catalogo.  
  
### <a name="catalog-action"></a>Azione catalogo  
  
|||  
|-|-|  
|**Nessuno**|Non esegue le operazioni **Ottimizza catalogo**, **Ricompila catalogo**o **Ripopola catalogo** .|  
|**Ottimizza catalogo**|Consente di ottimizzare l'utilizzo di spazio del catalogo e di migliorare le prestazioni di query, nonché di migliorare l'accuratezza della classificazione della pertinenza dei risultati delle ricerche.<br /><br /> Verrà eseguito ALTER FULLTEXT CATALOG *catalog_name* REORGANIZE.|  
|**Ricompilazione del catalogo**|Consente di eliminare e ricompilare il catalogo full-text. È necessario eseguire questa operazione quando viene modificata una proprietà fondamentale del catalogo, ad esempio l'impostazione relativa alla distinzione dei caratteri accentati e non accentati.<br /><br /> Affinché l'operazione di ricompilazione abbia esito positivo, il filegroup in cui risiede il catalogo full-text deve essere online oppure di lettura e scrittura. Al termine della ricompilazione, l'indice full-text verrà ripopolato.<br /><br /> Verrà eseguito ALTER FULLTEXT CATALOG *catalog_name* RICOMPILARE.|  
|**Ripopola catalogo**|Consente di aggiornare il catalogo con le modifiche più recenti apportate ai dati. Questa opzione implica tempi di inattività del catalogo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Popolare gli indici full-text](../relational-databases/indexes/indexes.md)  
  
  