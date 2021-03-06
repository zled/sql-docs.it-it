---
title: 'Attività 5: Creazione di un attributo basato su dominio da Excel | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 07cbc624-2c6b-4568-96e4-f18663a05d80
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 73d495f35e09ce893e9f8e763a7daa83851c1463
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48146341"
---
# <a name="task-5-creating-a-domain-based-attribute-from-excel"></a>Attività 5: Creazione di un attributo basato su dominio di Excel
  In questa attività si converte il **lo stato** attributo delle **Supplier** entità sotto forma di un **attributo basato su dominio**. Dopo aver configurato l'attributo State da uno basato su dominio e pubblicarlo in MDS, una nuova entità denominata **lo stato** verrà creato nel server MDS con tutti i valori nella colonna e il **stato** attributo del **Supplier** entità verrà popolato con i valori di **stato** entità. A questo punto, il **Suppliers** modello deve disporre di due entità: **Supplier** e **stato** in cui la **stato** attributo del  **Supplier** entità è un attributo basato su dominio che dipende **stato** entità.  
  
1.  Passare a **Excel** finestra dotata **Cleansed and Matched Suppliers. xlsx** aprire.  
  
2.  Fare clic su **Aggiorna** pulsante della barra multifunzione per ottenere gli aggiornamenti più recenti da MDS. Si dovrebbe vedere altri due record se è stata eseguita l'opzione facoltativa **attività 4**.  
  
3.  Fare clic sul nome della colonna **lo stato** (cella **I1**) nella **riga intestazione**.  
  
     ![Excel - pulsante Proprietà attributi](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel - pulsante Proprietà attributi")  
  
4.  Fare clic su **delle proprietà degli attributi** sulla barra multifunzione.  
  
5.  Nel **delle proprietà degli attributi** finestra di dialogo **elenco vincolato (basato su dominio)** per il **tipo di attributo**.  
  
6.  Tipo di **lo stato** per il **Nome nuova entità** e fare clic su **OK**.  
  
     ![Excel - finestra di dialogo Proprietà attributi](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - finestra di dialogo Proprietà attributo")  
  
7.  A questo punto, in Excel, dovrebbe **freccia giù** quando si fa clic su qualsiasi valore nel **stato** colonna. Se necessario, il valore può essere modificato utilizzando l'elenco a discesa.  
  
     ![Excel - elenco a discesa elenco con gli stati](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel - elenco a discesa elenco con gli Stati")  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 6: Verifica della creazione dell'attributo basato su dominio tramite Gestione dati master](../../2014/tutorials/task-6-verify-domain-based-attribute-master-data-manager.md)  
  
  
