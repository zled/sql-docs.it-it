---
title: Creazione e chiusura di thread | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- terminating threads [ODBC]
- threads [ODBC]
- multithreaded applications [ODBC]
ms.assetid: a2cf98ef-1c71-4742-8ee2-b53fd8e04333
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6f78b0e2b210385e9ffe32427145ba03395188a3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-and-terminating-threads"></a>Creazione e chiusura di thread
Applicazioni multithread che utilizzano ODBC devono chiamare le funzioni della libreria Run-Time di Microsoft® Visual C++® **beginthread** e **endthread** (o **beginthreadex** e **endthreadex**) per creare e terminare i thread che chiamano gestione Driver ODBC. Se le applicazioni chiamano le funzioni Microsoft Windows NT® **CreateThread** e **EndThread** invece le funzioni che perché Gestione Driver e alcuni driver ODBC di chiamata C in fase di esecuzione si verificherà le perdite di memoria non funziona in un thread creato chiamando **CreateThread**. Per ulteriori informazioni, vedere la documentazione di Microsoft Windows®.
