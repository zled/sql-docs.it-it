---
title: Sicurezza dell'integrazione con CLR | Documenti Microsoft
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
- security [CLR integration]
- authorization [CLR integration]
- common language runtime [SQL Server], security
- database objects [CLR integration], security
ms.assetid: 05d7a471-c5d5-4730-b903-e4edc8157bb4
caps.latest.revision: 54
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 689d425c2f13a442b1d8bbd5515939135f44fa0c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064269"
---
# <a name="clr-integration-security"></a>Sicurezza per l'integrazione con CLR
  Il modello di sicurezza del [!INCLUDE[ssNoVersion](../../../includes/dnprdnshort-md.md)] common language runtime (CLR) gestisce e protegge l'accesso tra diversi tipi di oggetti CLR e non CLR in esecuzione all'interno di [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] istruzione o un altro oggetto CLR in esecuzione sul server. Le chiamate tra gli oggetti vengono definite collegamenti. I tipi di controllo della sicurezza eseguiti su questi oggetti dipendono dai tipi di collegamento utilizzati.  
  
 Il modello di sicurezza dell'integrazione con CLR presenta gli obiettivi seguenti:  
  
-   Per impostazione predefinita, in esecuzione codice utente gestito in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. L'esecuzione di operazioni che potenzialmente compromettono l'affidabilità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] deve essere protetta grazie alle autorizzazioni di livello elevato appropriate.  
  
-   Non è consigliabile concedere al codice utente gestito l'accesso non autorizzato ai dati dell'utente o ad altro codice dell'utente nel database. Il codice definito dall'utente deve essere eseguito nel contesto di sicurezza della sessione utente che lo ha richiamato e con i privilegi corretti per il contesto di sicurezza in questione.  
  
-   È necessario effettuare controlli per limitare al codice utente l'accesso alle risorse esterne al server consentendone l'utilizzo esclusivamente per il calcolo e l'accesso ai dati locali.  
  
-   Non è consigliabile concedere al codice definito dall'utente l'accesso non autorizzato alle risorse di sistema solo perché è in esecuzione nel processo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] con il modello di sicurezza basata sull'accesso di codice di CLR. Alcuni dei vantaggi di questo approccio combinato alla sicurezza vengono esaminati nella presente sezione.  
  
 Nella tabella seguente vengono elencati gli argomenti disponibili in questa sezione.  
  
 [Sicurezza dall'accesso di codice dell'integrazione con CLR](clr-integration-code-access-security.md)  
 Viene illustrato il modello di sicurezza da accesso di codice (CAS, Code Access Security) per il codice gestito.  
  
 [Attributi di protezione host e programmazione dell'integrazione con CLR](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)  
 Vengono fornite informazioni sui valori di attributi di protezione host che non sono consentiti negli assembly SAFE e EXTERNAL_ACCESS.  
  
 [Collegamenti nella sicurezza dell'integrazione con CLR](../../../database-engine/dev-guide/links-in-clr-integration-security.md)  
 Viene illustrato come parti del codice utente possano chiamarsi reciprocamente in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Rappresentazione e la sicurezza dell'integrazione con CLR](../../../database-engine/dev-guide/impersonation-and-clr-integration-security.md)  
 Viene illustrato con il codice gestito acceda a risorse esterne utilizzando la rappresentazione.  
  
 [Chiamanti consentendo parzialmente attendibili](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
 Vengono illustrati i problemi che si verificano quando un metodo gestito richiama un metodo di una classe contenuta in un altro assembly.  
  
 [Domini applicazione e sicurezza dell'integrazione con CLR](../../../database-engine/dev-guide/application-domains-and-clr-integration-security.md)  
 Viene descritto come caricare gli assembly nei domini applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione degli assembly dell'integrazione con CLR](../assemblies/managing-clr-integration-assemblies.md)  
  
  