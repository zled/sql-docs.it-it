---
title: Classi di sicurezza AMO | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Management Objects, security
- security [AMO]
- AMO, security
ms.assetid: e3d5012a-8121-40de-9244-1fc824228693
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9562c7aab750f4114ef59c1a7c17f44c8e3b05e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171326"
---
# <a name="amo-security-classes"></a>Classi di sicurezza AMO
  
 Nella figura seguente viene illustrata la relazione delle classi descritte in questo argomento.  
  
 ![Classi di sicurezza in AMO descritte in questo argomento](../../../analysis-services/dev-guide/media/amo-securityclasses.gif "classi di sicurezza in AMO descritte in questo argomento")  
  
##  <a name="RolesMembers"></a> Oggetti Role e RoleMember  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.Role>, aggiungerlo alla raccolta di ruoli nel server, quindi aggiornare l'oggetto <xref:Microsoft.AnalysisServices.Role> nel server tramite il metodo Update. Prima che sia possibile utilizzare un oggetto <xref:Microsoft.AnalysisServices.Role>, è necessario aggiornarlo.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.Role>, è necessario eliminarlo tramite il metodo Drop dell'oggetto <xref:Microsoft.AnalysisServices.Role>. Il metodo Remove disponibile nella raccolta dei ruoli impedisce solo la visualizzazione del ruolo nell'applicazione, ma non rimuove il ruolo dal server. Non è possibile eliminare un oggetto <xref:Microsoft.AnalysisServices.Role> se è presente un'autorizzazione associata all'oggetto stesso.  
  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.RoleMember>, aggiungere un utente alla raccolta di membri del ruolo, quindi aggiornare l'oggetto <xref:Microsoft.AnalysisServices.Role> nel server tramite il metodo Update. Solo agli amministratori del server e del database è consentita la creazione di ruoli. È necessario che un oggetto <xref:Microsoft.AnalysisServices.Role> sia aggiornato nel server prima che a uno qualsiasi dei relativi membri sia consentito utilizzare uno degli oggetti per cui sono state concesse le autorizzazioni all'utente.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.RoleMember>, eliminarlo dalla raccolta tramite il metodo Remove della raccolta stessa, quindi aggiornare il ruolo tramite il metodo aggiorna.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili per tali oggetti, vedere <xref:Microsoft.AnalysisServices.Role> e <xref:Microsoft.AnalysisServices.RoleMember> in <xref:Microsoft.AnalysisServices>.  
  
##  <a name="Permissions"></a> Oggetti Permission  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.Permission>, aggiungerlo alla raccolta di autorizzazioni dell'oggetto, quindi aggiornare l'oggetto <xref:Microsoft.AnalysisServices.Permission> nel server tramite il metodo Update.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.Permission>, è necessario eliminarlo tramite il metodo Drop dell'oggetto. Il metodo Remove disponibile nella raccolta di autorizzazioni impedisce solo la visualizzazione delle autorizzazioni nell'applicazione, ma non rimuove l'oggetto <xref:Microsoft.AnalysisServices.Permission> dal server. Non è possibile eliminare un ruolo se è presente un'autorizzazione associata al ruolo stesso.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.Permission> in <xref:Microsoft.AnalysisServices>.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices>   
 [Programmazione di oggetti di sicurezza AMO](programming-amo-security-objects.md)   
 [Le autorizzazioni e diritti di accesso &#40;Analysis Services - dati multidimensionali&#41;](https://msdn.microsoft.com/library/ms174786(v=sql.120).aspx)   
 [Introduzione a classi AMO](amo-classes-introduction.md)   
 [Architettura logica &#40;Analysis Services - dati multidimensionali&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Gli oggetti di database &#40;Analysis Services - dati multidimensionali&#41;](../olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  