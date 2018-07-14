---
title: Proprietà catalogo full-Text (pagina generale) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.general.f1
ms.assetid: d1f66762-2d40-4f24-b635-a417d22ee79a
caps.latest.revision: 34
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: cc0d0c6e287d978b0a10979843a50f40f906872b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169324"
---
# <a name="full-text-catalog-properties-general-page"></a>Proprietà catalogo full-text (pagina Generale)
  Questa sezione illustra le opzioni e le funzioni disponibili nella **generali** pagina della **proprietà catalogo Full-Text** nella finestra di dialogo.  
  
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
  
 **/ Non accentati**  
 Visualizzare o modificare se il catalogo è sensibile ai segni diacritici, ad esempio una tilde (**~**), mark latino (**'**), o umlaut (**¨**). I valori validi sono:  
  
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
|**Ricompila catalogo**|Consente di eliminare e ricompilare il catalogo full-text. È necessario eseguire questa operazione quando viene modificata una proprietà fondamentale del catalogo, ad esempio l'impostazione relativa alla distinzione dei caratteri accentati e non accentati.<br /><br /> Affinché l'operazione di ricompilazione abbia esito positivo, il filegroup in cui risiede il catalogo full-text deve essere online oppure di lettura e scrittura. Al termine della ricompilazione, l'indice full-text verrà ripopolato.<br /><br /> Verrà eseguito ALTER FULLTEXT CATALOG *catalog_name* RICOMPILARE.|  
|**Ripopola catalogo**|Consente di aggiornare il catalogo con le modifiche più recenti apportate ai dati. Questa opzione implica tempi di inattività del catalogo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Popolare gli indici full-text](../relational-databases/indexes/indexes.md)  
  
  
