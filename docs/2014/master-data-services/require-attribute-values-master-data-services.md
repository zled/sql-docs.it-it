---
title: Richiedere valori di attributo (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], requiring attribute values
- attributes [Master Data Services], requiring values
ms.assetid: a360ef13-0c34-43b8-a87e-2f5d8732d30e
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 1e4c2932102892326ad159d5db1901873d1f22d6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072821"
---
# <a name="require-attribute-values-master-data-services"></a>Richiedere valori di attributo (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]richiedere valori di attributo quando si desidera essere sicuri che i dati master siano completi.  
  
> [!NOTE]  
>  I membri a cui mancano valori di attributo basati su dominio non sono visualizzati nelle gerarchie derivate basate su tali relazioni.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-require-attribute-values"></a>Per richiedere valori di attributo  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Dalla barra dei menu scegliere **Gestisci** e fare clic su **Regole business**.  
  
3.  Nella pagina **Manutenzione regola business** selezionare un modello dall'elenco **Modello** .  
  
4.  Dall'elenco **Entità** selezionare un'entità.  
  
5.  Dall'elenco **Tipo di membro** selezionare un tipo di membro a cui applicare la regola di business.  
  
6.  Dall'elenco **Attributo** selezionare un attributo o lasciare inalterata l'impostazione predefinita **Tutti**.  
  
7.  Fare clic su **Aggiungi regola di business**.  
  
8.  Fare clic su **Modifica regola business selezionata**.  
  
9. Nel riquadro **Componenti** espandere il nodo **Azioni** .  
  
10. Fare clic su **è obbligatorio** e trascinarlo in modo che le **quindi** del riquadro **azione** etichetta.  
  
11. Nel riquadro **Attributi** fare clic su un attributo e trascinarlo nell'etichetta **Seleziona attributo** del riquadro **Modifica azione** .  
  
12. Nel riquadro **Modifica azione** fare clic su **Salva elemento**.  
  
13. Fare clic **Indietro**.  
  
14. Facoltativamente, nella pagina **Manutenzione regola business** per la riga che contiene la regola business fare doppio clic su una cella nella colonna **Nome**, **Descrizione**o **Notifica** per aggiornare il valore.  
  
15. Fare clic su **Pubblica regole business**.  
  
16. Nella finestra di dialogo di conferma fare clic su **OK**. Lo stato della regola viene modificato in **Attiva**.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
-   Applicare regole business ai dati eseguendo una delle procedure riportate di seguito:  
  
    -   [Convalidare membri specifici rispetto a regole Business &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Convalidare una versione rispetto alle regole Business &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Le regole di business &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Gerarchie derivate &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
