---
title: "Autorizzazioni per modelli e membri sovrapposte (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modelli [Master Data Services], autorizzazioni valide"
  - "autorizzazioni [Master Data Services], modelli e membri sovrapposti"
  - "membri [Master Data Services], autorizzazioni valide"
ms.assetid: 9fd7a555-43bf-4796-a8b6-1ca63a291216
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Autorizzazioni per modelli e membri sovrapposte (Master Data Services)
  Le autorizzazioni assegnate a un membro possono sovrapporsi alle autorizzazioni assegnate a un oggetto modello. Quando si verificano sovrapposizioni, viene applicata l'autorizzazione più restrittiva.  
  
 Se un membro dispone di autorizzazione diversa da quella del relativo oggetto modello corrispondente, si applicano le regole seguenti:  
  
-   **Negare** esegue l'override di tutte le altre autorizzazioni.  
  
-   **Amministrazione** autorizzazione a livello di modello esegue l'override di tutte le altre autorizzazioni e viene modificato con autorizzazione di accesso (CRUD) tutti i livelli di sub.  
  
-   Un'autorizzazione di accesso valida interseca le autorizzazioni per membri e attributi.  
  
     Ad esempio, se le autorizzazioni membri includono **Crea** e **aggiornamento**, l'autorizzazione per gli attributi è **aggiornamento**. L'autorizzazione valida è **aggiornamento**.  
  
 Nell'immagine seguente viene indicato quali autorizzazioni vengono applicate a ogni singolo valore di attributo quando le autorizzazioni per gli attributi sono diverse dalle autorizzazioni per i membri.  
  
 ![mds_conc_security_member_overlap_table](../master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")  
  
## Esempio 1  
 ![mds_conc_overlap_model_1](../master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")  
  
 Nel **modelli** scheda, l'entità Product presenta **aggiornamento** assegnata l'autorizzazione. Tutti gli attributi nell'entità ereditano questa autorizzazione.  
  
 Nel **membri della gerarchia** scheda, il nodo della sottocategoria Mountain Bikes in una gerarchia derivata include **aggiornamento** assegnata l'autorizzazione.  
  
 Risultato: In **Explorer**, l'utente ha **aggiornamento** autorizzazione a tutti i valori di attributo per tutti i membri nel nodo Mountain bike. Tutti gli altri membri e attributi sono nascosti.  
  
 ![mds_conc_overlap_model_example_1](../master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")  
  
## Esempio 2  
 ![mds_conc_overlap_model_2](../master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")  
  
 Nel **modelli** scheda, all'attributo Subcategory è **aggiornamento** assegnata l'autorizzazione.  
  
 Nel **membri della gerarchia** scheda, il nodo della sottocategoria Mountain Bikes in una gerarchia derivata viene assegnato in modo esplicito **lettura** autorizzazione.  
  
 Risultato: In **Explorer**, l'utente ha **lettura** autorizzazione ai valori di attributo Subcategory per i membri nel nodo Mountain bike. Tutti gli altri membri e attributi sono nascosti.  
  
 ![mds_conc_overlap_model_example_2](../master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## Esempio 3  
 ![mds_conc_overlap_model_3](../master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")  
  
 Nel **modelli** scheda, all'attributo Subcategory è **lettura** assegnata l'autorizzazione.  
  
 Nel **membri della gerarchia** scheda alla sottocategoria Mountain Bikes in una gerarchia derivata viene assegnata in modo esplicito **aggiornamento** autorizzazione.  
  
 Risultato: In **Explorer**, l'utente ha **lettura** autorizzazione ai valori di attributo. Tutti gli altri membri e attributi sono nascosti.  
  
 ![mds_conc_overlap_model_example_2](../master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## Vedere anche  
 [Come vengono determinate le autorizzazioni & #40; Master Data Services & #41;](../master-data-services/how-permissions-are-determined-master-data-services.md)   
 [Sovrapposizione di utenti e autorizzazioni del gruppo di 40 #; Master Data Services & #41;](../master-data-services/overlapping-user-and-group-permissions-master-data-services.md)  
  
  