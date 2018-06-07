---
title: Lync SDN Interface Bandwidth Estimates
TOCTitle: Lync SDN Interface Bandwidth Estimates
ms:assetid: 35458e8f-29ee-4bc5-b2bc-51bbe390b8d5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912665(v=office.15)
ms:contentKeyID: 64126836
ms.date: 03/04/2016
mtps_version: v=office.15
---

# Lync SDN Interface Bandwidth Estimates

Provides bandwidth estimate data for Lync SDN Interface 2.1.1.


**Applies to**: Lync Server 2010 | Skype for Business

Lync SDN Interface 2.1.1 provides some estimates on the bandwidth that will be used during a call for each stream as a consequence of the codecs being used. The following table shows the raw estimates for each codec. The Bandwidth xml tag contains a weighted average based on the codecs that might be used during the call. This Bandwidth tag shows 0 bandwidth if the given stream direction is inactive.

## Bandwidth Estimates

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Codec</p></th>
<th><p>Media</p></th>
<th><p>Typical</p></th>
<th><p>Maximum</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>X-MSRTA/16000</p></td>
<td><p>audio</p></td>
<td><p>49600</p></td>
<td><p>91000</p></td>
</tr>
<tr class="even">
<td><p>X-MSRTA/8000</p></td>
<td><p>audio</p></td>
<td><p>33100</p></td>
<td><p>56600</p></td>
</tr>
<tr class="odd">
<td><p>G722/8000</p></td>
<td><p>audio</p></td>
<td><p>85400</p></td>
<td><p>164600</p></td>
</tr>
<tr class="even">
<td><p>G722/8000/2</p></td>
<td><p>audio</p></td>
<td><p>108400</p></td>
<td><p>228600</p></td>
</tr>
<tr class="odd">
<td><p>G722/16000/2</p></td>
<td><p>audio</p></td>
<td><p>108400</p></td>
<td><p>228600</p></td>
</tr>
<tr class="even">
<td><p>G7221/16000</p></td>
<td><p>audio</p></td>
<td><p>44800</p></td>
<td><p>81000</p></td>
</tr>
<tr class="odd">
<td><p>PCMU/8000</p></td>
<td><p>audio</p></td>
<td><p>83200</p></td>
<td><p>161000</p></td>
</tr>
<tr class="even">
<td><p>PCMA/8000</p></td>
<td><p>audio</p></td>
<td><p>83200</p></td>
<td><p>161000</p></td>
</tr>
<tr class="odd">
<td><p>SIREN/16000</p></td>
<td><p>audio</p></td>
<td><p>39300</p></td>
<td><p>68600</p></td>
</tr>
<tr class="even">
<td><p>SILK/16000</p></td>
<td><p>audio</p></td>
<td><p>47700</p></td>
<td><p>105000</p></td>
</tr>
<tr class="odd">
<td><p>SILKNARROW/8000</p></td>
<td><p>audio</p></td>
<td><p>31200</p></td>
<td><p>59000</p></td>
</tr>
<tr class="even">
<td><p>SILKWIDE/16000</p></td>
<td><p>audio</p></td>
<td><p>47700</p></td>
<td><p>105000</p></td>
</tr>
<tr class="odd">
<td><p>SILK/8000</p></td>
<td><p>audio</p></td>
<td><p>31200</p></td>
<td><p>59000</p></td>
</tr>
<tr class="even">
<td><p>X-ULPFECUC/90000</p></td>
<td><p>audio</p></td>
<td><p>29000</p></td>
<td><p>64000</p></td>
</tr>
<tr class="odd">
<td><p>AAL2-G726-32/8000</p></td>
<td><p>audio</p></td>
<td><p>38600</p></td>
<td><p>62000</p></td>
</tr>
<tr class="even">
<td><p>X-RTVC1/90000</p></td>
<td><p>video</p></td>
<td><p>500000</p></td>
<td><p>2510000</p></td>
</tr>
<tr class="odd">
<td><p>X-H264UC/90000</p></td>
<td><p>video</p></td>
<td><p>500000</p></td>
<td><p>4010000</p></td>
</tr>
<tr class="even">
<td><p>H264</p></td>
<td><p>video</p></td>
<td><p>500000</p></td>
<td><p>4010000</p></td>
</tr>
<tr class="odd">
<td><p>X-ULPFECUC/90000</p></td>
<td><p>video</p></td>
<td><p>29000</p></td>
<td><p>64000</p></td>
</tr>
<tr class="even">
<td><p>X-DATA/90000</p></td>
<td><p>applicationsharing</p></td>
<td><p>439000</p></td>
<td><p>943000</p></td>
</tr>
</tbody>
</table>

