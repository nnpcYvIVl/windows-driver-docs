---
title: Filtering Layer
description: Filtering Layer
ms.assetid: db2fd1dc-c080-4f12-8138-7e66c74adacd
keywords:
- filtering layer WDK Windows Filtering Platform
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Filtering Layer


A *filtering layer* is a point in the TCP/IP network stack where network data is passed to the [filter engine](filter-engine.md) for matching against the current set of filters. Each filtering layer in the network stack is identified by a unique [filtering layer identifier](https://docs.microsoft.com/windows-hardware/drivers/network/filtering-layer-identifiers).

When a [filter](filter.md) is added to the filter engine, it is added at a designated filtering layer where it will filter the network data. Specific [data fields](https://docs.microsoft.com/windows-hardware/drivers/network/data-field-identifiers) are made available at each filtering layer for processing by the filters that have been added to the filter engine at that layer. If the filter engine passes the network data to a [callout](callout.md) for additional processing, it includes these data fields and any [metadata](https://docs.microsoft.com/windows-hardware/drivers/network/metadata-fields) that is available at that filtering layer.

[Run-time Filtering Layer Identifiers](https://docs.microsoft.com/windows-hardware/drivers/network/run-time-filtering-layer-identifiers) (FWPS\_*XXX*) are used by kernel-mode callout drivers. [Management Filtering Layer Identifiers](https://docs.microsoft.com/windows-hardware/drivers/network/management-filtering-layer-identifiers) (FWPM\_*XXX*) are used by **Fwpm*Xxx*** functions that interact with the Base Filtering Engine (BFE) from either user mode or kernel mode (for example, [**FwpmFilterAdd0**](https://docs.microsoft.com/windows/desktop/api/fwpmu/nf-fwpmu-fwpmfilteradd0)).

The FWPS data types are smaller than their FWPM counterparts: the FWPM filtering layer identifiers are GUIDs (128 bits), whereas the FWPS filtering layer identifiers are [**LUIDs**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/igpupvdev/ns-igpupvdev-_luid)(64 bits). The smaller size for FWPS data types improves system performance because integer comparisons are faster than GUID comparisons for real-time traffic, and the kernel memory handles FWPS types more efficiently.

 

 





