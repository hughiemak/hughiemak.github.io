---
layout: post
title:  "Software Engineering Principles"
date:   2021-01-18 00:00
---

* External qualities: visible to users
* Internal qualities: of developer's concern
* Process qualities: Software process best practices of software engineering in an organization context. Expresses the degree to which defined processes were followed and completed.
* Product qualities: Software products are the output of software processes. Product quality is determined by the degree to which the developed software meets the defined requirements.

### In-class Practice 1

|  | Design | Implementation | Testing |
|-------|--------|---------|---------|
| Command and control systems | 46 | 20 | 34 | 
| Spaceborn systems | 34 | 20 | 46 |
| Operating systems | 33 | 17 | 50 |
| Scientific systems | 44 | 26 | 30 | 
| Business systems | 44 | 28 | 28 |

a. iOS 13: operating systems\\
b. TACCS: Command and control systems\\
c. MATLAB: scientific systems\\
d. IQMS manufacturing ERP: Business systems\\
e. Spaceborne radar systems: Spaceborn systems

Requirements/design: b > c = d > e > a

Implementation: d > c > b = e > a

Testing: a > e > b > c > d

Explanation:
* Design and testing is generally most time-consuming.
* Design setup the whole framwork, functionality and usage of the software.
* Testing is required for reliability and robustness.

* Spaceborn systems: high reliability requirement so testing > design
* Operating systems: complex in functionality is high but design procedure is well know so testing > design
* Command and control systems, scientific systems and business systems: relatively complicated but reliability requirement is not hight so design > testing.