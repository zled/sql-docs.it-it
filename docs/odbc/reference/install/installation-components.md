---
title: Componenti di installazione | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
- ODBC [ODBC], component installation
ms.assetid: 9de15ca0-fe6a-4634-8709-a928d3c9cc73
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c5fe2538d1567630121f05a4798583099de7200
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32917206"
---
# <a name="installation-components"></a>Componenti di installazione
> [!NOTE]  
>  A partire da Windows XP e Windows Server 2003, ODBC è incluso nel sistema operativo Windows. Solo nelle versioni precedenti di Windows è necessario installare ODBC in modo esplicito.  
  
 Il processo di installazione viene avviato quando l'utente esegue il programma di installazione. Il programma di installazione funziona in combinazione con il *installer DLL* e *DLL di installazione del driver* per ogni driver. Il programma di installazione sia il programma di installazione DLL utilizzare gli argomenti di **SQLInstallDriverEx** e **SQLInstallTranslatorEx** funzioni per determinare i file di copia o eliminazione per ogni componente. Nella figura seguente viene illustrata la relazione tra questi componenti di installazione.  
  
 ![Relazione tra componenti di installazione](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]  
>  Il file Odbc.inf che è stato utilizzato in ODBC 2. *x* per descrivere i file necessari per ogni ODBC componente non verrà utilizzata in ODBC 3*x*. I driver di ODBC 3*x* componenti non è necessario creare un file Odbc.inf. La rimozione di **la funzione SQLInstallDriver** e **la funzione SQLInstallODBC**e la rimozione del **la funzione SQLInstallTranslator**, il rendering Odbc.inf non necessari. Le informazioni del driver usato per le sezioni della parola chiave Driver di Odbc.inf viene attualmente fornite nel *lpszDriver* argomento **SQLInstallDriverEx**. Le informazioni di conversione che utilizzato per il [ODBC traduttore] e sezioni specifiche di conversione di Odbc.inf è ora disponibile nel *lpszTranslator* argomento di **SQLInstallTranslatorEx**. Queste modifiche consentono l'installazione di ODBC garantire la portabilità tra piattaforme.  
  
 Per ulteriori informazioni su questi componenti, vedere gli argomenti seguenti alla fine di questa sezione.  
  
-   [Programma di installazione](../../../odbc/reference/install/setup-program.md)  
  
-   [DLL di installazione](../../../odbc/reference/install/installer-dll.md)  
  
-   [DLL di installazione driver](../../../odbc/reference/install/driver-setup-dll.md)
