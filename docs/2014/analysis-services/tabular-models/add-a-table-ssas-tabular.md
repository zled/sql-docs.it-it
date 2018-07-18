---
title: Aggiungere una tabella (SSAS tabulare) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d713c432-db99-4983-acc1-52b0fdd58bd6
caps.latest.revision: 4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 82167dfaa3de6d9312cb3115849aac7a9beaf07b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281897"
---
# <a name="add-a-table-ssas-tabular"></a>Aggiungere una tabella (SSAS tabulare)
  In questo argomento verrà illustrato come aggiungere una tabella da un'origine dati dalla quale sono stati importati precedentemente i dati nel modello. Per aggiungere una tabella dalla stessa origine dati, è possibile utilizzare la connessione all'origine dati esistente. È consigliabile utilizzare sempre una sola connessione in caso di importazione di un qualsiasi numero di tabelle da un'unica origine dati.  
  
### <a name="to-add-a-table-from-an-existing-data-source"></a>Per aggiungere una tabella da un'origine dati esistente  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]scegliere **Connessioni esistenti** dal menu **Modello**.  
  
2.  Nella pagina **Connessioni esistenti** selezionare la connessione all'origine dati contenente la tabella da aggiungere, quindi fare clic su **Apri**.  
  
3.  Nella pagina **Selezione tabelle e viste** selezionare la tabella dall'origine dati che si desidera aggiungere al modello.  
  
    > [!NOTE]  
    >  Nella pagina **Selezione tabelle e viste** non verranno mostrate le tabelle importate in precedenza come selezionate.  Se si seleziona una tabella che è stata precedentemente importata tramite questa connessione e a cui non è stato assegnato un nome descrittivo diverso, verrà accodato 1 al nome utilizzato. Non è necessario selezionare di nuovo tutte le tabelle importate precedentemente tramite questa connessione.  
  
4.  Se necessario, usare **Visualizza anteprima e applica filtro** per selezionare solo determinate colonne o per applicare filtri ai dati da importare.  
  
5.  Fare clic su **Fine** per importare la nuova tabella.  
  
> [!NOTE]  
>  Se si importano più tabelle contemporaneamente da una sola origine dati, tutte le relazioni tra tali tabelle nell'origine saranno create automaticamente nel modello. In caso di aggiunta di una tabella in un secondo momento, potrebbe essere tuttavia necessario creare manualmente le relazioni nel modello tra le tabelle appena aggiunte e quelle importate in precedenza.  
  
## <a name="see-also"></a>Vedere anche  
 [Importare i dati &#40;tabulare di SSAS&#41;](../import-data-ssas-tabular.md)   
 [Eliminare una tabella &#40;tabulare di SSAS&#41;](delete-a-table-ssas-tabular.md)  
  
  
