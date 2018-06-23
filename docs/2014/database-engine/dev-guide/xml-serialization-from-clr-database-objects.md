---
title: Serializzazione XML da oggetti di Database CLR | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- serialization
- XML serialization [CLR integration]
- common language runtime [SQL Server], XML serialization
- XmlSerializer class
ms.assetid: ac84339b-9384-4710-bebc-01607864a344
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ad6b9ebaba9f05b0a927cd65f788cdbdb672a6d5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171282"
---
# <a name="xml-serialization-from-clr-database-objects"></a>Serializzazione XML da oggetti di database CLR
  La serializzazione XML è necessaria in due scenari:  
  
-   Richiamo di servizi Web da oggetti CLR (Common Language Runtime).  
  
-   Conversione in XML di un tipo definito dall'utente.  
  
 Se la serializzazione XML viene eseguita richiamando la classe `XmlSerializer` di solito viene generato un assembly di serializzazione aggiuntivo che viene sottoposto a overload nel progetto con l'assembly di origine. Tuttavia, per motivi di sicurezza, questo overload è disabilitato in CLR. Pertanto, per chiamare un servizio web o eseguire la conversione da tipo definito dall'utente in formato XML interno [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'assembly deve essere creato manualmente tramite uno strumento denominato **Sgen.exe** fornito con .NET Framework che genera l'errore necessarie assembly di serializzazione. Quando si richiama `XmlSerializer`, l'assembly di serializzazione deve essere creato manualmente tramite la seguente procedura:  
  
1.  Eseguire la **Sgen.exe** strumento che viene fornito con .NET Framework SDK per creare l'assembly contenente i serializzatori XML per l'assembly di origine.  
  
2.  Utilizzando l'istruzione `CREATE ASSEMBLY`, registrare in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'assembly generato.  
  
 Per informazioni sugli errori che si potrebbero ricevere quando si esegue la serializzazione XML, vedere l'articolo di supporto tecnico Microsoft seguente: ["Cannot load dynamically generated serialization assembly"](http://support.microsoft.com/kb/913668).  
  
 Per informazioni su tipi di dati che non sono supportati da XMLSerializer, vedere Supporto dell'associazione a XML Schema nella documentazione di .NET Framework.  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso ai dati da oggetti di Database CLR](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)   
 [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
  
