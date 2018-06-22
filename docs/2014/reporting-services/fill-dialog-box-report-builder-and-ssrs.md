---
title: Finestra di dialogo (Generatore Report e SSRS) riempimento | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rtp.rptdesigner.reportbody.fill.f1
- "10065"
- "10501"
- sql12.rtp.rptdesigner.shared.filldv.f1
- sql12.rtp.rptdesigner.rectangleproperties.fill.f1
- "10064"
- sql12.rtp.rptdesigner.textboxproperties.fill.f1
- "10124"
ms.assetid: 93a91d02-d558-4a0e-8d17-3fdf21e208d3
caps.latest.revision: 11
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 1378fb461e3a52f751f79cb0d31e0dcd498d8c0b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064202"
---
# <a name="fill-dialog-box-report-builder-and-ssrs"></a>Finestra di dialogo Riempimento (Generatore report e SSRS)
  Nella scheda **Riempimento** è possibile specificare le opzioni relative al colore per lo sfondo di una o più celle in un'area dati o una casella di testo.  
  
## <a name="options"></a>Opzioni  
 **Colore riempimento**  
 Fare clic sul pulsante del colore per selezionare un colore di riempimento per il rettangolo. Fare clic sul **Expression***(fx)* pulsante per modificare l'espressione, che può essere un valore esadecimale per il colore RGB o uno dei nomi di colore predefiniti specificati nella **espressione** finestra di dialogo. Per visualizzare un elenco di colori predefiniti, selezionare **Web** nel riquadro **Elemento**. I nomi di colore elencati nel riquadro **Titolo** possono essere digitati nel riquadro di testo dell'espressione. Quando si digita il nome del colore, non utilizzare un segno di uguale (=) o le virgolette ("").  
  
 **Selezionare l'origine dell'immagine**  
 Indicare il percorso di archiviazione dell'immagine in modo da consentire al processore del report di visualizzarla durante il rendering del report.  
  
-   **Esterna** Scegliere questa opzione se si desidera che l'immagine continui ad essere disponibile come file su un server di report o un server Web.  
  
-   **Incorporata** Scegliere questa opzione se si desidera incorporare l'immagine nel report.  
  
-   **Database** Scegliere questa opzione se si desidera includere un nome di campo del database che rappresenti le immagini da includere nel report.  
  
 **Utilizzare questa immagine**  
 Questa opzione viene visualizzata quando si seleziona l'opzione **Incorporata** o **Esterna** .  
  
 Se si intende incorporare l'immagine, selezionare l'immagine da aggiungere al report nell'elenco a discesa. Fare clic su **Importa** per aggiungere l'immagine all'elenco a discesa. Se un'immagine è stata aggiunta al riquadro **Dati** , è possibile scegliere **Incorporata** e quindi selezionare l'immagine nell'elenco a discesa.  
  
 Se si seleziona l'opzione **Esterna** , digitare l'URL dell'immagine. Per un report pubblicato in un server di report configurato per la modalità nativa, utilizzare un percorso completo o relativo (ad esempio, http://*\<nomeserver >*  /Images/Image1.jpg). Per un report pubblicato in un server di report configurato in modalità integrata SharePoint, utilizzare un URL completo (ad esempio, http://*\<NomeServerSharePoint > /\<sito >*  /documenti/immagini / Image1).  
  
 **Importa**  
 Questa opzione è disponibile quando si seleziona **Incorporata**. Fare clic su questa opzione per aggiungere un'immagine all'elenco a discesa **Use this image** (Usa questa immagine).  
  
 **Utilizzare questo campo**  
 Disponibile quando si seleziona **Database**. Selezionare il nome del campo.  
  
 **Utilizzare questo tipo MIME**  
 Scegliere il formato appropriato delle immagini contenute nel database, ad esempio bmp, jpeg, gif, png o x-png.  
  
## <a name="see-also"></a>Vedere anche  
 [Formattazione degli elementi del report &#40;Generatore report e SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [Formattazione di testo e segnaposto &#40;SSRS e Generatore Report&#41;](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)   
 [Immagini &#40;SSRS e Generatore Report&#41;](report-design/images-report-builder-and-ssrs.md)  
  
  