---
title: Creare un indice (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: d694a105-69b1-4ff6-99d3-1f408b916b81
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 20fad19ffa9d5d82c83321f63236b066e3e1c781
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47849839"
---
# <a name="create-an-index-master-data-services"></a>Creare un indice (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Creare un indice personalizzato in un elenco di attributi a cui si eseguono spesso query per migliorare le prestazioni delle query.  
  
## <a name="prerequisites"></a>Prerequisites  
 Per eseguire questa procedura:  
  
-   È necessaria l'autorizzazione per accedere all'area funzionale Amministrazione sistema. Per altre informazioni, vedere [Autorizzazioni per aree funzionali &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
 **Per creare un indice**  
  
1.  In Gestione dati master fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Gestisci modelli** selezionare un modello dalla griglia, quindi fare clic su **Entità**.  
  
3.  Dalla **griglia** della pagina **Gestisci entità** selezionare la riga per l'entità per cui si vuole creare un indice.  
  
4.  Fare clic su **Indici**.  
  
5.  Nella casella **Nome** digitare un nome per l'indice.  
  
6.  Selezionare **Univoco** per creare un indice univoco. Per altre informazioni sui tipi di indice, vedere [Indice personalizzato &#40;Master Data Services&#41;](../master-data-services/custom-index-master-data-services.md).  
  
7.  Fare clic sugli attributi nella casella **Attributi disponibili** , quindi fare clic sulla freccia **Aggiungi** . Per aggiungere tutti gli attributi, fare clic sulla freccia **Aggiungi tutto** .  
  
8.  Fare clic su **Salva**.  
  
 Per ogni indice creato, viene aggiunta una riga con quattro colonne alla griglia. La tabella seguente descrive le colonne.  
  
|Nome colonna|Descrizione|  
|-----------------|-----------------|  
|Stato|Stato dell'indice.<br /><br /> Quando si fa clic su **Salva** viene visualizzata l'immagine ![Icona di aggiornamento dello stato](../master-data-services/media/mds-statusicon-updating.png "Icona di aggiornamento dello stato") che indica che è in corso l'aggiornamento dell'indice.<br /><br /> Se si verificano errori durante la creazione o la modifica di un indice viene visualizzata l'immagine ![Icona di errore](../master-data-services/media/mds-statusicon-error.png "Icona di errore").<br /><br /> In caso contrario lo stato è OK e viene visualizzata l'immagine ![Icona di stato OK](../master-data-services/media/mds-statusicon-ok.png "Icona di stato OK").|  
|nome|Nome dell'indice.|  
|Univoco|Specifica se l'indice è univoco.|  
|Con attributi|Mostra i nomi visualizzati degli attributi su cui è definito l'indice.|  
  
 Quando si fa clic su un indice, vengono visualizzate le informazioni seguenti.  
  
-   **Creato da**: nome dell'utente che ha creato l'indice.  
  
-   **Il**: la data e l'ora di creazione dell'indice.  
  
-   **Aggiornato da**: nome dell'ultimo utente che ha aggiornato l'indice.  
  
-   **Il**: la data e l'ora dell'ultimo aggiornamento dell'indice.  
  
## <a name="next-steps"></a>Next Steps  
 [Modificare ed eliminare un indice &#40;Master Data Services&#41;](../master-data-services/edit-and-delete-an-index-master-data-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Indice personalizzato &#40;Master Data Services&#41;](../master-data-services/custom-index-master-data-services.md)  
  
  
