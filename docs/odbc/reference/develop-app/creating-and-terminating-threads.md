---
title: Creazione e chiusura di thread | Documenti Microsoft
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
- terminating threads [ODBC]
- threads [ODBC]
- multithreaded applications [ODBC]
ms.assetid: a2cf98ef-1c71-4742-8ee2-b53fd8e04333
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6568dd1109dc417cad0e5f4ad3d973ae5aaa497a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909256"
---
# <a name="creating-and-terminating-threads"></a>Creazione e chiusura di thread
Applicazioni multithread che utilizzano ODBC devono chiamare le funzioni della libreria Run-Time di Microsoft® Visual C++® **beginthread** e **endthread** (o **beginthreadex** e **endthreadex**) per creare e terminare i thread che chiamano gestione Driver ODBC. Se le applicazioni chiamano le funzioni Microsoft Windows NT® **CreateThread** e **EndThread** invece le funzioni che perché Gestione Driver e alcuni driver ODBC di chiamata C in fase di esecuzione si verificherà le perdite di memoria non funziona in un thread creato chiamando **CreateThread**. Per ulteriori informazioni, vedere la documentazione di Microsoft Windows®.
