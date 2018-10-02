---
title: Inizializzare una sottoscrizione | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], initializing subscriptions
- transactional replication, initializing subscriptions
- initializing subscriptions [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], about initializing subscriptions
- merge replication [SQL Server replication], initializing subscriptions
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a7cd8c4ce33d34faba4507cfeb9dbe83a81f3bc7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47607520"
---
# <a name="initialize-a-subscription"></a>Inizializzazione di una sottoscrizione
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  I Sottoscrittori in una topologia di replica devono essere inizializzati in modo da disporre di una copia dello schema di ogni articolo della pubblicazione per cui è stata effettuata la sottoscrizione e di tutti gli oggetti di replica necessari, quali stored procedure, trigger e tabelle di metadati. Il Sottoscrittore, inoltre, riceve in genere un set di dati iniziale. Con il metodo di inizializzazione predefinito è possibile utilizzare uno snapshot completo in cui sono inclusi lo schema, gli oggetti di replica e i dati. È tuttavia possibile inizializzare le pubblicazioni senza uno snapshot completo.  
  
 Per ulteriori informazioni, vedere [Initialize a Subscription with a Snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md) e [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
  
