---
title: Raccolte di XML Schema di grandi dimensioni e condizioni di memoria insufficiente | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- out-of-memory conditions
- XML schema collections [SQL Server], large
ms.assetid: 29b9d839-aaaf-48fb-be17-840c751f36f1
caps.latest.revision: "9"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 10539a2ce5674a1f0282ca154245c4035f716dda
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="large-xml-schema-collections-and-out-of-memory-conditions"></a>Raccolte di XML Schema di grandi dimensioni e condizioni di memoria insufficiente
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] Durante una chiamata alla funzione incorporata XML_SCHEMA_NAMESPACE() in una raccolta XML Schema di grandi dimensioni o durante il tentativo di eliminare queste ultime, potrebbe verificarsi una condizione di memoria insufficiente. Per risolvere questo problema, è possibile utilizzare le soluzioni seguenti:  
  
-   Quando il carico di lavoro del sistema è ridotto, è consigliabile utilizzare il comando DROP_XML_SCHEMA_COLLECTION. Se tale tentativo ha esito negativo, configurare il database in modalità utente singolo mediante l'istruzione ALTER DATABASE e provare ad eseguire di nuovo il comando DROP XML SCHEMA COLLECTION. Se la raccolta XML Schema è contenuta nel database **master**, **model**o **tempdb**, per attivare la modalità utente singolo è necessario riavviare il server.  
  
-   Quando si chiama la funzione XML_SCHEMA_NAMESPACE, è possibile provare a recuperare un singolo spazio dei nomi XML Schema ; provare a eseguire la chiamata quando diminuisce il carico di lavoro del sistema oppure provare ad eseguirla in modalità utente singolo.  
  
## <a name="see-also"></a>Vedere anche  
 [Requisiti e limitazioni per l'utilizzo di raccolte di XML Schema nel server](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
