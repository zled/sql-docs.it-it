---
title: "Richiedere valori di attributo (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "regole business [Master Data Services], richiesta di valori di attributo"
  - "attributi [Master Data Services], richiesta di valori"
ms.assetid: a360ef13-0c34-43b8-a87e-2f5d8732d30e
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# Richiedere valori di attributo (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] richiedere valori di attributo quando si desidera essere sicuri che i dati master siano completi.  
  
> [!NOTE]  
>  I membri a cui mancano valori di attributo basati su dominio non sono visualizzati nelle gerarchie derivate basate su tali relazioni.  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per ulteriori informazioni, vedere [amministratori & #40; Master Data Services & #41;](../master-data-services/administrators-master-data-services.md).  
  
### Per richiedere valori di attributo  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Dalla barra dei menu scegliere **Gestisci** e fare clic su **regole Business**.  
  
3.  Nel **regole Business** pagina da di **modello** elenco a discesa, selezionare un modello.  
  
4.  Dal **entità** elenco a discesa, selezionare un'entità.  
  
5.  Dal **i tipi di membro** elenco a discesa, selezionare un tipo di membro per la regola business da applicare a.  
  
6.  Scegliere **Aggiungi**.  
  
7.  Nel **nome** digitare un nome per la regola business.  
  
8.  Facoltativamente, nel **Descrizione** digitare la descrizione della regola business.  
  
9. Sotto il **quindi** blocco, fare clic su **Aggiungi**. Verrà visualizzato un pannello.  
  
10. Dal **operatore** elenco a discesa, selezionare **necessaria azione**.  
  
11. Dal **attributo** elenco a discesa, selezionare un attributo.  
  
12. Fare clic su **Salva**. Verrà aggiunta una nuova riga per il **quindi** griglia.  
  
13. Fare clic su **Salva**.  
  
14. Fare clic su **pubblicano tutti**.  
  
15. Nella finestra di dialogo di conferma, fare clic su **OK**. Il valore di **lo stato regola Business** colonna **Active**.  
  
## Passaggi successivi  
  
-   Applicare regole business ai dati eseguendo una delle procedure riportate di seguito:  
  
    -   [Convalidare membri specifici rispetto alle regole Business & #40; Master Data Services & #41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Convalidare una versione rispetto alle regole Business & #40; Master Data Services & #41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## Vedere anche  
 [Le regole di business & #40; Master Data Services & #41;](../master-data-services/business-rules-master-data-services.md)   
 [Gerarchie derivate & #40; Master Data Services & #41;](../master-data-services/derived-hierarchies-master-data-services.md)  
  
  