---
title: 'Attività 5: Creazione di un attributo basato su dominio da Excel | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07cbc624-2c6b-4568-96e4-f18663a05d80
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5e7a8dda16d8f513b2c4b07b9f41712be806b8a9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155889"
---
# <a name="task-5-creating-a-domain-based-attribute-from-excel"></a>Attività 5: Creazione di un attributo basato su dominio di Excel
  In questa attività si converte il **stato** attributo del **fornitore** entità come un **un attributo basato su dominio**. Dopo aver configurato l'attributo State da uno basato su dominio e pubblicarlo in MDS, una nuova entità denominata **stato** verrà creato nel server MDS con tutti i valori nella colonna e il **stato** attributo del **Fornitore** entità verrà popolato con i valori di **stato** entità. A questo punto, il **Suppliers** modello dovrebbe ora contenere due entità: **fornitore** e **stato** in cui il **stato** attributo del  **Fornitore** entità è un attributo basato su dominio che dipende **stato** entità.  
  
1.  Passare a **Excel** finestra contenente **Cleansed and Matched Suppliers. xlsx** aprire.  
  
2.  Fare clic su **aggiornare** pulsante della barra multifunzione per ottenere gli aggiornamenti più recenti da MDS. Dovrebbe essere altri due record se è stata eseguita l'opzione facoltativa **attività 4**.  
  
3.  Fare clic sul nome di colonna **stato** (cella **I1**) nei **riga di intestazione**.  
  
     ![Excel - pulsante Proprietà attributi](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel - pulsante Proprietà attributi")  
  
4.  Fare clic su **delle proprietà degli attributi** sulla barra multifunzione.  
  
5.  Nel **le proprietà dell'attributo** finestra di dialogo **elenco vincolato (basato su dominio)** per il **tipo di attributo**.  
  
6.  Tipo di **stato** per il **Nome nuova entità** e fare clic su **OK**.  
  
     ![Excel - finestra di dialogo Proprietà attributo](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - finestra di dialogo Proprietà attributo")  
  
7.  A questo punto, in Excel, dovrebbe essere **freccia in giù** quando si fa clic su qualsiasi valore nel **stato** colonna. Se necessario, il valore può essere modificato utilizzando l'elenco a discesa.  
  
     ![Excel - elenco a discesa elenco con gli stati](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel - elenco a discesa elenco con gli Stati")  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 6: Verificare che l'attributo basato su dominio viene creato tramite Gestione dati Master](../../2014/tutorials/task-6-verify-domain-based-attribute-master-data-manager.md)  
  
  